# stored-procedure
create table sp3 (Id int primary key identity,Name varchar(50),
Email varchar(60),Mobile varchar(20))

create proc Crud_sp
@id int,
@name varchar(50),
@Email varchar(60),
@Mobile varchar(20),
@choice int
as
begin
if @choice='Insert'
begin
insert into sp3 (id,name,Email,Mobile) values (@id,@name,@Email,@Mobile)
end
else if @choice='Delete'
begin
delete sp3 where Id=@id
end
else if @choice='Update'
begin
update sp3 set Name=@name,Email=@Email,Mobile=@Mobile where Id=@id
end
else if @choice='Select'
begin
select * from sp3
end
else if @choice='Search'
begin
select * from sp3 where id=@id
end
end

create table sp4 (Id_d int primary key, Department varchar(30),
Id int foreign key references sp3(Id))

select * from sp3 inner join sp4 on sp3.Id=sp4.Id

create proc Crud4_sp
@Id_d int,
@Department varchar(30),
@Id int,
@choice int
as
begin
if @choice='Insert'
begin
insert into sp4 (Id_d,Department,Id) values (@id,@Department,@Id)
end
else if @choice='Delete'
begin
delete sp4 where Id=@Id
end
else if @choice='Update'
begin
update sp4 set Department=@Department where Id=@id
end
else if @choice='Select'
begin
select * from sp4
end
else if @choice='Search'
begin
select * from sp4 where id=@id
end
end
