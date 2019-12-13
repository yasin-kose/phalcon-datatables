# About
This is a [Phalcon Framework](http://phalconphp.com/) adapter for [DataTables](http://www.datatables.net/).
# Support
### Currently supported
* QueryBuilder interface
* ResultSet interface
* Pagination
* Raw query interface(*new)
* Global search (by value)
* Ordering
* Multiple column ordering
* Column-based search
* Caching

# Installation
### Installation via Composer
* Install a composer
* Create `composer.json` file inside your project directory
* Paste into it
```json
{
	"require": {
		"ankapix/phalcon-datatables": "dev-master"
	}
}
```
* Run `composer update`

# Example usage
It uses Phalcon [QueryBuilder](http://docs.phalconphp.com/en/latest/api/Phalcon_Mvc_Model_Query_Builder.html) for pagination in DataTables.

In example we have a stantart MVC application, with database enabled. Don't need to provide a normal bootstrap PHP file, for Phalcon documentation, visit official site.

### Controller (using QueryBuilder):
```php
<?php
use \DataTables\DataTable;

class TestController extends \Phalcon\Mvc\Controller {
	public function indexAction() {
		if ($this->request->isAjax()) {
		$builder = $this->modelsManager->createBuilder()
						->columns('id, name, email, balance')
						->from('Example\Models\User');

		$dataTables = new DataTable();
		$dataTables->fromBuilder($builder)->sendResponse();
		}
	}
}
```