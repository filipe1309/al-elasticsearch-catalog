# Class - 2.5

### Visualize

```html
KQL interesses: esportes Pessoas com interesse em esportes agrupadas por
formacao e estado
<iframe
  src="http://localhost:5601/app/kibana#/visualize/create?embed=true&type=table&indexPattern=0e2245b0-0537-11ec-8b45-4dbebb389f9c&_g=()&_a=(filters:!(),linked:!f,query:(language:kuery,query:'interesses+:+esportes'),uiState:(vis:(params:(sort:(columnIndex:!n,direction:!n)))),vis:(aggs:!((enabled:!t,id:'1',params:(),schema:metric,type:count),(enabled:!t,id:'2',params:(field:forma%C3%A7%C3%A3o.original,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:100000),schema:bucket,type:terms),(enabled:!t,id:'3',params:(field:estado,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:5),schema:bucket,type:terms)),params:(dimensions:(buckets:!((accessor:0,aggType:terms,format:(id:terms,params:(id:string,missingBucketLabel:Missing,otherBucketLabel:Other)),params:())),metrics:!((accessor:1,aggType:count,format:(id:number),params:()))),perPage:10,percentageCol:'',showMetricsAtAllLevels:!f,showPartialRows:!f,showTotal:!f,sort:(columnIndex:!n,direction:!n),totalFunc:sum),title:'',type:table))"
  height="600"
  width="800"
></iframe>

Top 5 formacoes
<iframe
  src="http://localhost:5601/app/kibana#/visualize/edit/b2229760-0540-11ec-8b45-4dbebb389f9c?embed=true&_g=()&_a=(filters:!(),linked:!f,query:(language:kuery,query:''),uiState:(),vis:(aggs:!((enabled:!t,id:'1',params:(),schema:metric,type:count),(enabled:!t,id:'2',params:(field:forma%C3%A7%C3%A3o.original,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:5),schema:segment,type:terms)),params:(addLegend:!t,addTooltip:!t,dimensions:(metric:(accessor:0,aggType:count,format:(id:number),params:())),isDonut:!f,labels:(last_level:!t,show:!f,truncate:100,values:!t),legendPosition:right,type:pie),title:'Top+5+formacoes',type:pie))"
  height="600"
  width="800"
></iframe>

Top 5 formacoes por estado
<iframe
  src="http://localhost:5601/app/kibana#/visualize/edit/60fed7d0-0541-11ec-8b45-4dbebb389f9c?embed=true&_g=()&_a=(filters:!(),linked:!f,query:(language:kuery,query:''),uiState:(),vis:(aggs:!((enabled:!t,id:'1',params:(),schema:metric,type:count),(enabled:!t,id:'2',params:(field:estado,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:30),schema:segment,type:terms),(enabled:!t,id:'3',params:(field:forma%C3%A7%C3%A3o.original,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:5),schema:group,type:terms)),params:(addLegend:!t,addTimeMarker:!f,addTooltip:!t,categoryAxes:!((id:CategoryAxis-1,labels:(filter:!t,show:!t,truncate:100),position:bottom,scale:(type:linear),show:!t,style:(),title:(),type:category)),dimensions:(x:(accessor:0,aggType:terms,format:(id:terms,params:(id:string,missingBucketLabel:Missing,otherBucketLabel:Other)),params:()),y:!((accessor:1,aggType:count,format:(id:number),params:()))),grid:(categoryLines:!f),labels:(show:!f),legendPosition:right,seriesParams:!((data:(id:'1',label:Count),drawLinesBetweenPoints:!t,mode:stacked,show:true,showCircles:!t,type:histogram,valueAxis:ValueAxis-1)),thresholdLine:(color:%2334130C,show:!f,style:full,value:10,width:1),times:!(),type:histogram,valueAxes:!((id:ValueAxis-1,labels:(filter:!f,rotate:0,show:!t,truncate:100),name:LeftAxis-1,position:left,scale:(mode:normal,type:linear),show:!t,style:(),title:(text:Count),type:value))),title:'Top+5+formacoes+por+estado',type:histogram))"
  height="600"
  width="800"
></iframe>

Top 5 Formacoes por estado MG & SP 
1. Uma dimensão com bucket com agregação de
termo no campo "estado" 
2. Uma dimensão com sub-bucket com agregação de termo no
campo "formação.original" 
3. Filtro: "estado : "MG" or estado : "SP"

<iframe
  src="http://localhost:5601/app/kibana#/visualize/edit/c6956530-0543-11ec-8b45-4dbebb389f9c?embed=true&_g=()&_a=(filters:!(),linked:!f,query:(language:kuery,query:'estado+:+%22MG%22+or+estado+:+%22SP%22+'),uiState:(),vis:(aggs:!((enabled:!t,id:'1',params:(),schema:metric,type:count),(enabled:!t,id:'2',params:(field:estado,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:5),schema:segment,type:terms),(enabled:!t,id:'3',params:(field:forma%C3%A7%C3%A3o.original,missingBucket:!f,missingBucketLabel:Missing,order:desc,orderBy:'1',otherBucket:!f,otherBucketLabel:Other,size:5),schema:segment,type:terms)),params:(addLegend:!t,addTooltip:!t,dimensions:(buckets:!((accessor:0,aggType:terms,format:(id:terms,params:(id:string,missingBucketLabel:Missing,otherBucketLabel:Other)),params:())),metric:(accessor:1,aggType:count,format:(id:number),params:())),isDonut:!f,labels:(last_level:!t,show:!f,truncate:100,values:!t),legendPosition:right,type:pie),title:'Top+5+Formacoes+por+estado+MG+%26+SP',type:pie))"
  height="600"
  width="800"
></iframe>
```

## Dashboard

```html
Meu Dashboard

<iframe
  src="http://localhost:5601/app/kibana#/dashboard/43219ee0-0542-11ec-8b45-4dbebb389f9c?embed=true&_g=()&_a=(description:'',filters:!(),fullScreenMode:!f,options:(hidePanelTitles:!f,useMargins:!t),panels:!((embeddableConfig:(),gridData:(h:7,i:dcb20198-c65c-4da4-86cb-06d5f9791143,w:24,x:0,y:0),id:d0c40020-053e-11ec-8b45-4dbebb389f9c,panelIndex:dcb20198-c65c-4da4-86cb-06d5f9791143,type:visualization,version:'7.4.2'),(embeddableConfig:(),gridData:(h:7,i:a6d1e167-6509-4b6a-baed-f7fd13cb10f8,w:24,x:24,y:0),id:b2229760-0540-11ec-8b45-4dbebb389f9c,panelIndex:a6d1e167-6509-4b6a-baed-f7fd13cb10f8,type:visualization,version:'7.4.2'),(embeddableConfig:(),gridData:(h:14,i:'6fc177ab-09cd-497d-8e1f-5de99b9b1902',w:48,x:0,y:7),id:'60fed7d0-0541-11ec-8b45-4dbebb389f9c',panelIndex:'6fc177ab-09cd-497d-8e1f-5de99b9b1902',type:visualization,version:'7.4.2')),query:(language:kuery,query:'estado+:+%22SP%22+or+estado+:%22RJ%22+'),timeRestore:!f,title:'Meu+Dashboard',viewMode:view)"
  height="600"
  width="800"
></iframe>
```

Aggregations Framework  
https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html

https://caelum-online-public.s3.amazonaws.com/1601-elasticsearch2/05/Alura+Elasticsearch+Aula+10_+Agregando+e+visualizando+nossos+dados.pdf