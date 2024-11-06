<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Create Appointment</title>
</head>
<body>
    <h2>Create a New Appointment</h2>
    <form action="insert_appointment.php" method="POST">
        Pet Name: 
        <select name="pet_id">
            <?php
            include('db.php');
            $result = $conn->query("SELECT pet_id, pet_name FROM pets");
            while($row = $result->fetch_assoc()) {
                echo "<option value='".$row['pet_id']."'>".$row['pet_name']."</option>";
            }
            ?>
        </select><br><br>
        Veterinarian:
        <select name="employee_id">
            <?php
            $result = $conn->query("SELECT employee_id, name FROM employees");
            while($row = $result->fetch_assoc()) {
                echo "<option value='".$row['employee_id']."'>".$row['name']."</option>";
            }
            ?>
        </select><br><br>
        Appointment Date: <input type="date" name="date"><br><br>
        Appointment Time: <input type="time" name="time"><br><br>
        <input type="submit" value="Create Appointment">
    </form>
</body>
</html>
