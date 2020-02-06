<?php
    // Tải thư viện
    require_once ('libs/db.php');
    require_once ('libs/utils.php');
    // Xử lý module và action truyền từ URL
	$module = isset($_GET['m']) ? $_GET['m'] : 'home';
	$action = isset($_GET['a']) ? $_GET['a'] : 'list';
    $file = '';
	switch ($module) {
        case 'home':
            $file = 'modules/home/home.php';
            break;
        case 'project':
            $file = 'modules/project/project.php';
            break;
        case 'task':
            $file = 'modules/task/task.php';
            break;
        case 'user':
            $file = 'modules/user/user.php';
            break;
        default:
            $file = 'modules/home/home.php';
    }
?>
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <meta name="description" content="">
    <meta name="author" content="Mark Otto, Jacob Thornton, and Bootstrap contributors">
    <meta name="generator" content="Jekyll v3.8.6">
    <title>My Office: <?php echo $module ?></title>

    <!-- Bootstrap core CSS -->
    <link href="public/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">

    <style>
        .bd-placeholder-img {
            font-size: 1.125rem;
            text-anchor: middle;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }

        @media (min-width: 768px) {
            .bd-placeholder-img-lg {
                font-size: 3.5rem;
            }
        }
    </style>
    <!-- Custom styles for this template -->
    <link href="public/css/jumbotron.css" rel="stylesheet">
</head>
<body>
<nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
    <a class="navbar-brand" href="index.php">MyOffice</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarsExampleDefault" aria-controls="navbarsExampleDefault" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarsExampleDefault">
        <ul class="navbar-nav mr-auto">
            <li class="nav-item <?php if ($module === 'home') echo 'active'; ?>">
                <a class="nav-link" href="index.php">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item <?php if ($module === 'user') echo 'active'; ?>">
                <a class="nav-link" href="index.php?m=user&a=list">User</a>
            </li>
            <li class="nav-item <?php if ($module === 'project') echo 'active'; ?>">
                <a class="nav-link" href="index.php?m=project&a=list">Project</a>
            </li>
            <li class="nav-item <?php if ($module === 'task') echo 'active'; ?>">
                <a class="nav-link" href="index.php?m=task&a=list">Task</a>
            </li>
            <li class="nav-item dropdown dropdown-menu-right">
                <a class="nav-link dropdown-toggle" href="#" id="dropdown01" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Tài khoản</a>
                <div class="dropdown-menu" aria-labelledby="dropdown01">
                    <a class="dropdown-item" href="#">Đổi mật khẩu</a>
                    <a class="dropdown-item" href="#">Thông tin cá nhân</a>
                    <a class="dropdown-item" href="#">Thoát</a>
                </div>
            </li>
        </ul>
        <!--<form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>-->
    </div>
</nav>

<main role="main">
    <?php include($file) ?>
</main>

<footer class="container">
    <p>&copy; Company 2017-2019</p>
</footer>
<script src="https://code.jquery.com/jquery-3.4.1.slim.min.js"  crossorigin="anonymous"></script>
<script src="public/js/bootstrap.bundle.min.js" integrity="sha384-6khuMg9gaYr5AxOqhkVIODVIvm9ynTT5J4V1cfthmT+emCG6yVmEZsRHdxlotUnm" crossorigin="anonymous"></script>
</body>
</html>
<?php isset($conn) ? mysqli_close($conn) : null ?>
