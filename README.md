Creating school management system using html ,css , JQuery and Bootstrap 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>School Management System</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
    <style>
        body {
            background: url('school-bg.jpg') no-repeat center center fixed;
            background-size: cover;
        }
        .login-form {
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 10px;
        }
        .student-table tbody tr:nth-child(odd) {
            background-color: #f2f2f2;
        }
        .student-table tbody tr:nth-child(even) {
            background-color: #ffffff;
        }
        .btn-edit {
            background-color: #007bff;
            color: white;
        }
        .btn-delete {
            background-color: #dc3545;
            color: white;
        }
        .highlight {
            background-color: #d3f9d8 !important;
            transition: background-color 0.3s;
        }
    </style>
</head>
<body>

<div class="container">
    
    <h1 class="text-center text-white my-4">Welcome to the School Management System</h1>
    <p class="text-center text-white">Efficiently manage your school data and student information with our system.</p>

   
    <div class="login-form" id="loginSection">
        <h3 class="text-center">Login</h3>
        <form id="loginForm">
            <div class="form-group">
                <label for="username">Username</label>
                <input type="text" id="username" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" class="form-control" required>
                <small class="form-text text-muted">Password must contain at least 1 uppercase, 1 lowercase, and 1 digit.</small>
            </div>
            <button type="button" id="loginBtn" class="btn btn-primary btn-block">Login</button>
        </form>
    </div>

  
    <div id="studentSection" style="display:none;">
        <h2 class="text-white mt-4">Student Information</h2>
        <input type="text" id="searchBar" class="form-control mb-3" placeholder="Search by name">
        <table class="table table-bordered student-table">
            <thead class="thead-dark">
                <tr>
                    <th>Name</th>
                    <th>Age</th>
                    <th>Semester</th>
                    <th>Registration Number</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>AMRIT</td>
                    <td>20</td>
                    <td>3</td>
                    <td>2341013244</td>
                    <td>
                        <button class="btn btn-sm btn-edit">Edit</button>
                        <button class="btn btn-sm btn-delete">Delete</button>
                    </td>
                </tr>
                <tr>
                    <td>SASWAT</td>
                    <td>22</td>
                    <td>6</td>
                    <td>2101324550</td>
                    <td>
                        <button class="btn btn-sm btn-edit">Edit</button>
                        <button class="btn btn-sm btn-delete">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
        <button class="btn btn-outline-primary" id="viewAchievements">View Achievements</button>
    </div>

  
    <div id="navButtons" class="mt-4" style="display:none;">
        <button class="btn btn-outline-light mr-2" id="admission">Admission</button>
        <div class="btn-group">
            <button class="btn btn-outline-light dropdown-toggle" data-toggle="dropdown">Achievements</button>
            <div class="dropdown-menu">
                <a class="dropdown-item" id="gallery">Gallery</a>
            </div>
        </div>
        <button class="btn btn-outline-light" id="alumni">Alumni</button>
    </div>

   
    <div id="achievementGallery" class="carousel slide mt-4" style="display:none;">
        <div class="carousel-inner">
            <div class="carousel-item active">
                <img src="achievement1.jpg" class="d-block w-100" alt="Achievement 1">
            </div>
            <div class="carousel-item">
                <img src="achievement2.jpg" class="d-block w-100" alt="Achievement 2">
            </div>
            <div class="carousel-item">
                <img src="achievement3.jpg" class="d-block w-100" alt="Achievement 3">
            </div>
        </div>
        <a class="carousel-control-prev" href="#achievementGallery" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        </a>
        <a class="carousel-control-next" href="#achievementGallery" role="button" data-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
        </a>
    </div>
</div>

<script>
   
    $("#loginBtn").click(function () {
        const password = $("#password").val();
        const regex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).+$/;
        if (regex.test(password)) {
            $("#loginSection").hide();
            $("#studentSection").show();
        } else {
            alert("Invalid password! Make sure it contains at least 1 uppercase, 1 lowercase, and 1 digit.");
        }
    });

  
    $("#viewAchievements").click(function () {
        $("#studentSection").hide();
        $("#achievementGallery").show();
    });

 
    $("#searchBar").on("input", function () {
        const value = $(this).val().toLowerCase();
        $(".student-table tbody tr").filter(function () {
            $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1);
        });
    });

  
    $(".student-table tbody tr").hover(
        function () { $(this).addClass("highlight"); },
        function () { $(this).removeClass("highlight"); }
    );

  
    $("#gallery").click(function () {
        $("#achievementGallery").toggle();
    });

 
    $("#alumni").click(function () {
        alert("Navigate to the Alumni Section"); 
    });
</script>

</body>
</html>
