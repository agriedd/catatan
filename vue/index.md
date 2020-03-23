### Librari untuk vue js

#### Layout

#### Form
##### Select
1. vue-select
2. edd-select
##### Date Picker
1. edd-datepicker
##### Time Picker
1. edd-timepicker

#### Table
1. edd-table

#### Pagination
1. edd-pagination

#### Sidebar
1. edd-sidebar

#### 

### Catatan Singkat
#### Disable ESLint pada Vue Cli

buat file vue.config.js

tambahkan
```javascript
	module.exports = {
	    chainWebpack: config => {
	        config.module.rules.delete('eslint');
	    }
	}
```