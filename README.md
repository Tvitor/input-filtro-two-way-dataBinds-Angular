---
description: Anotações feitas durante as Aulas do Bootcamp - 13 horas
---

### Filtrar dinamicamente 

> Utilizando  two-way Databinds onde sera inserido o valor que sera lincado ao componente e também onde receberá o valor que será filtrado

```text
course-list.component.ts

import { Course } from './course';
import { CourseService } from './course.service';
filteredCourses: Course[] = [];
    _courses:Course[] = [] ;
    _filterBy: String;
    
    constructor(private courseService: CourseService){}
    ngOnInit(): void {
        //Called after the constructor, initializing input properties, and the first call to ngOnChanges.
        //Add 'implements OnInit' to the class.
        this._courses = this.courseService.retrieveAll();
        this.filteredCourses = this._courses;
    }
    set filter(value:String){
        this._filterBy = value;
        this.filteredCourses = this._courses.filter((course:Course)=>course.name.toLocaleLowerCase().indexOf(this._filterBy.toLocaleLowerCase()) > -1)
    }

    get filter(){
        return this._filterBy;
    }
```

> Para receber o evento de input do two-way Databinds é utilizado o a sinaxe set + funcao

```text
 set filter(valor: Course){
  _this.filterby = value;
 }
```

> a sintaxe get + funcao será para atualizar o input, retornando o resultado filtrado

> Para que o get retorne o valor filtrado, é preciso utilizar o filter ainda no set filter

```text
set filter(valor:Course)
this.filteredCourses = this._courses.filter((course:Course)=>course.name.toLocaleLowerCase().indexOf(this._filterBy.toLocaleLowerCase()) > -1)
```

```text
ngOnInit()
_filteredCourses = this._courses;
```

> para a filtrar o que foi digitado sem alterar a variável que contem a lista de cursos, é necessário criar uma outra variável recebendo a lista de cursos.

```text
get filter(){
    return _this.filterby 
}

```

```text
course-list.component.html
<div class="form-group row">
    <label class="col-sm-2 col-form-label">Filter by:</label>
    <div class="col-sm-10">
        <input [(ngModel)]="filter" class="form-control">
    </div>
</div>
```

## Course-Manager

#### Sistema de Gerenciamento de Cursos - Criar - Editar - Consultar - Deletar

```
ng new course-manager
```

> Esse projeto tem como finalidade consultar, editar, alterar e deletar os cursos além de criar validações de formulário do curso

### SRC/APP/courses

> Diretório correspondente aos componentes inerentes aos cursos

```text
course-list.component.html
```

```text
course.ts
```

> Classe de curso



