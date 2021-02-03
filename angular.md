# angular 中使用 material-design-icons

`npm install material-design-icons`

在angular.json添加

`"projects": { "YOUR-PROJECT-NAME": { "architect": { "build": { "options": { "styles": [ {"node_modules/material-design-icons/iconfont/material-icons.css"`

# angular 中定义 Paginator

`
import {MatPaginatorIntl} from "@angular/material/paginator";
import {Injectable} from "@angular/core";

@Injectable()
export class ChinesePaginator extends MatPaginatorIntl {


  itemsPerPageLabel = '每页个数:';
  nextPageLabel     = 'next';
  previousPageLabel = 'previous';

  getRangeLabel = function (page, pageSize, length) {
    if (length === 0 || pageSize === 0) {
      return '0 od ' + length;
    }
    length = Math.max(length, 0);
    const startIndex = page * pageSize;
    // If the start index exceeds the list length, do not try and fix the end index to the end.
    const endIndex = startIndex < length ?
      Math.min(startIndex + pageSize, length) :
      startIndex + pageSize;
    return startIndex + 1 + ' - ' + endIndex + ' / ' + length;
  };
  
}
`

`@Injectable()` 不要忘记了，不然没有效果

最后在`material.model.ts`中添加
`  providers:[
    {provide: MatPaginatorIntl, useClass: ChinesePaginator}
  ]
`
