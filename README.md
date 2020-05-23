## yajra table
1 link -: https://github.com/yajra/laravel-datatables
2. composer require yajra/laravel-datatables-oracle:"~9.0"
3. config/app.php

	'providers' => [
	    ...,
	    Yajra\DataTables\DataTablesServiceProvider::class,
	]

	'aliases' => [
	    ...,
	    'DataTables' => Yajra\DataTables\Facades\DataTables::class,
	]

4. php artisan vendor:publish --provider="Yajra\DataTables\DataTablesServiceProvider"
5. datatable js code
	 <script>
         $(function() {
               $('#table').DataTable({
               processing: true,
               serverSide: true,
               ajax: '{{ url('ajax-list') }}',
               columns: [
                        { data: 'id', name: 'id' },
                        { data: 'name', name: 'name' },
                        { data: 'email', name: 'email' }
                     ]
            });
         });
         </script>

##############################################################################################################
## Tinker use for dummy data insert
1. php artisan tinker
2. factory(App\User::class, 100)->create();
##############################################################################################################

## Create the validation request command
1. php artisan make:request ContactRequest
2. composer require proengsoft/laravel-jsvalidation
3. php artisan vendor:publish --provider="Proengsoft\JsValidation\JsValidationServiceProvider"
4. By default we use bootstrap to render Javascript validation code. You may want to change the version 
            of bootstrap to bootstrap4 in config/jsvalidation.phpby editing that line:

         'view' => 'jsvalidation::bootstrap4',
5. Keep in mind to copy your files using mix, so add in webpack.mix.js file -:

   mix.copy('vendor/proengsoft/laravel-jsvalidation/resources/views', 'resources/views/vendor/jsvalidation')
    .copy('vendor/proengsoft/laravel-jsvalidation/public', 'public/vendor/jsvalidation');
6. add these files to .gitignore to prevent them being tracked
   /resources/views/vendor/
   /public/vendor/

4. <div class="container">
    <div class="row">
        <div class="col-md-10 col-md-offset-1">
            <form class="form-horizontal" role="form" method="POST" action="" id="my-form">
                <div class="form-group">
                    <label class="col-md-4 control-label">Name</label>
                    <div class="col-md-6">
                        <input type="text" class="form-control" name="title">
                    </div>
                </div>
                <div class="form-group">
                    <label class="col-md-4 control-label">Email</label>
                    <div class="col-md-6">
                        <textarea name="body"></textarea>
                    </div>
                </div>
            </form>
        </div>
    </div>
</div>
<!-- Scripts -->
<script src="//cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.1/js/bootstrap.min.js"></script>
<!-- Laravel Javascript Validation -->
<script type="text/javascript" src="{{ asset('vendor/proengsoft/laravel-jsvalidation/public/js/jsvalidation.js')}}"></script>
{!! JsValidator::formRequest('App\Http\Requests\StoreBlogPostRequest', '#m

##############################################################################################################
## Repository
1. composer create-project --prefer-dist laravel/laravel repository
2. php artisan make:model Models/Conatct -m
3. https://itnext.io/repository-design-pattern-done-right-in-laravel-d177b5fa75d4
4.php artisan make:provider RepositoryServiceProvider