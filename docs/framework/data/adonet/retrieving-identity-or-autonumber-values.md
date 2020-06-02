---
title: Načítání hodnot identity nebo automatického číslování
description: Naučte se, jak načíst identitu a hodnoty pro automatické číslování primárních klíčů v relačních databázích a jak sloučit nové hodnoty identity v ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: dbbc013a5b6c83391a29109beca44120c68d827f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286569"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Načítání hodnot identity nebo automatického číslování

Primární klíč v relační databázi je sloupec nebo kombinace sloupců, které vždycky obsahují jedinečné hodnoty. Znalost hodnoty primárního klíče vám umožní najít řádek, který ho obsahuje. Relační databázové moduly, jako jsou SQL Server, Oracle a Microsoft Access/jet, podporují vytváření automaticky rostoucích sloupců, které se dají určit jako primární klíče. Tyto hodnoty jsou generovány serverem při přidávání řádků do tabulky. V SQL Server nastavíte vlastnost identity sloupce, v Oracle vytvoříte sekvenci a v Microsoft Access vytvoříte sloupec AutoNumber.

<xref:System.Data.DataColumn>Lze také použít ke generování automaticky rostoucích hodnot nastavením <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnosti na hodnotu true. Nicméně může dokončit duplicitními hodnotami v samostatných instancích a <xref:System.Data.DataTable> , pokud více klientských aplikací je nezávisle generuje automaticky zvyšovat hodnoty. Když server vygeneruje automaticky zvýší hodnoty, eliminuje potenciální konflikty tím, že umožňuje každému uživateli načíst vygenerovanou hodnotu pro každý vložený řádek.

Během volání `Update` metody a `DataAdapter` může databáze odesílat data zpět do vaší aplikace ADO.NET jako výstupní parametry nebo jako první vrácený záznam sady výsledků příkazu SELECT prováděného ve stejné dávce jako příkaz INSERT. ADO.NET může tyto hodnoty načíst a aktualizovat odpovídající sloupce v <xref:System.Data.DataRow> aktualizovaném sloupci.

Některé databázové moduly, jako je databázový stroj Jet Microsoft Access, nepodporují výstupní parametry a nemohou zpracovávat více příkazů v rámci jedné dávky. Při práci s databázovým strojem Jet můžete načíst novou hodnotu AutoNumber vygenerovanou pro vložený řádek spuštěním samostatného příkazu SELECT v obslužné rutině události pro `RowUpdated` událost `DataAdapter` .

> [!NOTE]
> Alternativou k použití automatického zvyšování hodnoty je použití <xref:System.Guid.NewGuid%2A> metody <xref:System.Guid> objektu k VYgenerování identifikátoru GUID nebo globálně jedinečného identifikátoru v klientském počítači, který lze zkopírovat na server při vložení každého nového řádku. `NewGuid`Metoda generuje 16 bajtů binární hodnotu, která je vytvořena pomocí algoritmu, který poskytuje vysokou pravděpodobnost, že žádná hodnota nebude duplikována. V databázi SQL Server je identifikátor GUID uložen ve `uniqueidentifier` sloupci, který SQL Server může automaticky generovat pomocí funkce jazyka Transact-SQL `NEWID()` . Použití identifikátoru GUID jako primárního klíče může negativně ovlivnit výkon. SQL Server poskytuje podporu pro `NEWSEQUENTIALID()` funkci, která generuje sekvenční identifikátor GUID, u kterého není zaručeno, že bude globálně jedinečný, ale který bude možné indexovat efektivněji.

## <a name="retrieving-sql-server-identity-column-values"></a>Načítají se SQL Server hodnoty sloupce identity.

Při práci s Microsoft SQL Server můžete vytvořit uloženou proceduru s parametrem Output, která vrátí hodnotu identity vloženého řádku. Následující tabulka popisuje tři funkce jazyka Transact-SQL v SQL Server, které lze použít k načtení hodnot sloupce identity.

|Funkce|Popis|
|--------------|-----------------|
|SCOPE_IDENTITY|Vrátí hodnotu poslední identity v rámci aktuálního oboru provádění. SCOPE_IDENTITY se doporučuje pro většinu scénářů.|
|@@IDENTITY|Obsahuje hodnotu poslední identity vygenerovanou v libovolné tabulce v aktuální relaci. @ @IDENTITY může být ovlivněn triggery a nemusí vracet hodnotu identity, kterou očekáváte.|
|IDENT_CURRENT|Vrátí hodnotu poslední identity vygenerovanou pro konkrétní tabulku v jakékoli relaci a v jakémkoli oboru.|

 Následující uložená procedura ukazuje, jak vložit řádek do tabulky **Categories** a použít výstupní parametr pro návrat nové hodnoty identity vygenerované funkcí Transact-SQL SCOPE_IDENTITY ().

```sql
CREATE PROCEDURE dbo.InsertCategory
  @CategoryName nvarchar(15),
  @Identity int OUT
AS
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)
SET @Identity = SCOPE_IDENTITY()
```

Uloženou proceduru lze poté zadat jako zdroj <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter> objektu. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A>Vlastnost <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> musí být nastavena na hodnotu <xref:System.Data.CommandType.StoredProcedure> . Výstup identity je načten vytvořením a <xref:System.Data.SqlClient.SqlParameter> , který má <xref:System.Data.ParameterDirection> <xref:System.Data.ParameterDirection.Output> . Při `InsertCommand` zpracování je vrácena hodnota automaticky zvýšená identita a umístěna do sloupce **KódKategorie** aktuálního řádku, pokud nastavíte <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> vlastnost příkazu Vložit na `UpdateRowSource.OutputParameters` nebo na `UpdateRowSource.Both` .

Pokud příkaz INSERT spustí dávku, která obsahuje příkaz INSERT a příkaz SELECT, který vrací novou hodnotu identity, můžete novou hodnotu načíst nastavením `UpdatedRowSource` vlastnosti pro příkaz INSERT na `UpdateRowSource.FirstReturnedRecord` .

[!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]

## <a name="merging-new-identity-values"></a>Slučují se nové hodnoty identity.

Běžným scénářem je zavolat `GetChanges` metodu `DataTable` pro vytvoření kopie, která obsahuje pouze změněné řádky a použít novou kopii při volání `Update` metody typu `DataAdapter` . To je užitečné hlavně v případě, že je potřeba zařadit změněné řádky do samostatné součásti, která provádí aktualizaci. Po aktualizaci může kopie obsahovat nové hodnoty identity, které se pak musí sloučit zpátky do původní `DataTable` . Nové hodnoty identity se pravděpodobně liší od původních hodnot v `DataTable` . Aby bylo možné sloučení dokončit, musí být zachovány původní hodnoty sloupců **Autoincrements** v kopii, aby bylo možné vyhledat a aktualizovat existující řádky v původním umístění `DataTable` , nikoli připojit nové řádky obsahující nové hodnoty identity. Ve výchozím nastavení jsou však tyto původní hodnoty ztraceny po volání `Update` metody `DataAdapter` , protože `AcceptChanges` je implicitně volána pro každou aktualizaci `DataRow` .

Existují dva způsoby, jak zachovat původní hodnoty `DataColumn` v v `DataRow` průběhu `DataAdapter` aktualizace:

- První metodou zachování původních hodnot je nastavení `AcceptChangesDuringUpdate` vlastnosti třídy `DataAdapter` na `false` . To má vliv na všechny `DataRow` `DataTable` aktualizované. Další informace a příklad kódu naleznete v tématu <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A> .

- Druhou metodou je napsat kód v `RowUpdated` obslužné rutině události `DataAdapter` pro nastavení na <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> . `DataRow`Je aktualizována, ale původní hodnota `DataColumn` je zachována. Tato metoda umožňuje zachovat původní hodnoty pro některé řádky, nikoli pro jiné. Kód může například zachovat původní hodnoty pro přidané řádky, nikoli pro upravené nebo odstraněné řádky, a to nejprve zaškrtnutím <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> a potom nastavením <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> pouze pro řádky s `StatementType` `Insert` .

Když se jedna z těchto metod používá k zachování původních hodnot v `DataRow` průběhu `DataAdapter` aktualizace, ADO.NET provede řadu akcí pro nastavení aktuálních hodnot na `DataRow` nové hodnoty vrácené výstupními parametry nebo prvním vráceným řádkem sady výsledků dotazu a přitom stále zachovává původní hodnotu v každé z nich `DataColumn` . Nejprve `AcceptChanges` Metoda `DataRow` je volána pro zachování aktuálních hodnot jako původních hodnot a následně jsou přiřazeny nové hodnoty. Po těchto akcích, `DataRows` které mají <xref:System.Data.DataRow.RowState%2A> vlastnost nastavenou na <xref:System.Data.DataRowState.Added> , bude `RowState` mít vlastnost nastavenou na <xref:System.Data.DataRowState.Modified> , což může být neočekávané.

Způsob, jakým jsou výsledky příkazu aplikovány na každý <xref:System.Data.DataRow> aktualizovaný, je určen <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastností každého <xref:System.Data.Common.DbCommand> . Tato vlastnost je nastavena na hodnotu z `UpdateRowSource` výčtu.

Následující tabulka popisuje, jak `UpdateRowSource` hodnoty výčtu ovlivňují <xref:System.Data.DataRow.RowState%2A> vlastnost aktualizovaných řádků.

|Název členu|Popis|
|-----------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges`je zavolána a výstupní hodnoty parametrů a/nebo hodnoty v prvním řádku libovolné vrácené sady výsledků jsou umístěny do `DataRow` aktualizovaného. Pokud neexistují žádné hodnoty, které by bylo možné použít, bude `RowState` <xref:System.Data.DataRowState.Unchanged> .|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Pokud byl vrácen řádek, `AcceptChanges` je zavolán a řádek je namapován na změněný řádek v `DataTable` , nastavení na `RowState` `Modified` . Pokud není vrácen žádný řádek, není `AcceptChanges` voláno a `RowState` zůstane `Added` .|
|<xref:System.Data.UpdateRowSource.None>|Všechny vrácené parametry nebo řádky jsou ignorovány. Není k dispozici žádné volání `AcceptChanges` a `RowState` zůstane `Added` .|
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges`je volána a všechny výstupní parametry jsou namapovány na změněný řádek v `DataTable` , nastavení na `RowState` `Modified` . Pokud žádné výstupní parametry neexistují, bude `RowState` `Unchanged` .|

### <a name="example"></a>Příklad

Tento příklad ukazuje extrakci změněných řádků z `DataTable` a pomocí a <xref:System.Data.SqlClient.SqlDataAdapter> k aktualizaci zdroje dat a načtení nové hodnoty sloupce identity. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>Provede dva příkazy jazyka Transact-SQL. první z nich je příkaz INSERT a druhá je příkaz SELECT, který používá funkci SCOPE_IDENTITY k načtení hodnoty identity.

```sql
INSERT INTO dbo.Shippers (CompanyName)
VALUES (@CompanyName);
SELECT ShipperID, CompanyName FROM dbo.Shippers
WHERE ShipperID = SCOPE_IDENTITY();
```

`UpdatedRowSource`Vlastnost příkazu INSERT je nastavena na hodnotu `UpdateRowSource.FirstReturnedRow` a <xref:System.Data.MissingSchemaAction> vlastnost `DataAdapter` je nastavena na hodnotu `MissingSchemaAction.AddWithKey` . `DataTable`Je vyplněn a kód přidá nový řádek do `DataTable` . Změněné řádky jsou poté extrahovány do nového `DataTable` , který je předán do `DataAdapter` , který následně aktualizuje server.

[!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]

`OnRowUpdated`Obslužná rutina události zkontroluje, <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> zda je řádek vložen. Pokud je, <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> vlastnost je nastavena na <xref:System.Data.UpdateStatus.SkipCurrentRow> . Řádek je aktualizován, ale původní hodnoty v řádku jsou zachovány. V hlavním těle postupu <xref:System.Data.DataSet.Merge%2A> je metoda volána pro sloučení nové hodnoty identity do původní `DataTable` a nakonec `AcceptChanges` je volána.

[!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
[!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]

## <a name="retrieving-microsoft-access-autonumber-values"></a>Načítání hodnot pro automatické číslování aplikace Microsoft Access

Tato část obsahuje ukázku, která ukazuje, jak načíst `Autonumber` hodnoty z databáze Jet 4,0. Databázový stroj Jet nepodporuje provádění více příkazů v dávce nebo použití výstupních parametrů, takže není možné použít některý z těchto postupů k vrácení nové `Autonumber` hodnoty přiřazené vloženému řádku. Můžete však přidat kód do `RowUpdated` obslužné rutiny události, která provede samostatný příkaz Select @ @IDENTITY pro načtení nové `Autonumber` hodnoty.

### <a name="example"></a>Příklad

Namísto přidávání informací o schématu pomocí `MissingSchemaAction.AddWithKey` , tento příklad nakonfiguruje `DataTable` se správným schématem před zavoláním metody <xref:System.Data.OleDb.OleDbDataAdapter> k vyplnění `DataTable` . V tomto případě je sloupec **KódKategorie** nakonfigurovaný tak, aby se hodnota přiřazená každému vloženému řádku od nuly nastavila na hodnotu <xref:System.Data.DataColumn.AutoIncrement%2A> `true` <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0 a na hodnotu <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1. Kód pak přidá dva nové řádky a použije `GetChanges` k přidání změněných řádků do nového `DataTable` , který je předán `Update` metodě.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]

`RowUpdated`Obslužná rutina události používá stejné otevření <xref:System.Data.OleDb.OleDbConnection> jako `Update` příkaz `OleDbDataAdapter` . Kontroluje `StatementType` <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> pro vložené řádky. Pro každý vložený řádek <xref:System.Data.OleDb.OleDbCommand> je vytvořen nový příkaz pro spuštění příkazu Select @ @IDENTITY v připojení, který vrací novou `Autonumber` hodnotu, která je umístěna do sloupce **KódKategorie** v `DataRow` . `Status`Vlastnost je pak nastavena na hodnotu `UpdateStatus.SkipCurrentRow` pro potlačení skrytého volání `AcceptChanges` . V hlavním těle procedury `Merge` je volána metoda pro sloučení těchto dvou `DataTable` objektů a nakonec `AcceptChanges` je volána metoda.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]

### <a name="retrieving-identity-values"></a>Načítání hodnot identity

Často jsme nastavili sloupec jako identitu, pokud hodnoty ve sloupci musí být jedinečné. A někdy potřebujeme hodnotu identity nových dat. Tato ukázka předvádí, jak načíst hodnoty identity:

- Vytvoří uloženou proceduru pro vložení dat a vrácení hodnoty identity.

- Provede příkaz pro vložení nových dat a zobrazení výsledku.

- Slouží <xref:System.Data.SqlClient.SqlDataAdapter> k vložení nových dat a zobrazení výsledku.

Před kompilací a spuštěním ukázky musíte vytvořit ukázkovou databázi pomocí následujícího skriptu:

```sql
USE [master]
GO

CREATE DATABASE [MySchool]
GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE procedure [dbo].[CourseExtInfo] @CourseId int
as
select c.CourseID,c.Title,c.Credits,d.Name as DepartmentName
from Course as c left outer join Department as d on c.DepartmentID=d.DepartmentID
where c.CourseID=@CourseId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create procedure [dbo].[DepartmentInfo] @DepartmentId int,@CourseCount int output
as
select @CourseCount=Count(c.CourseID)
from course as c
where c.DepartmentID=@DepartmentId

select d.DepartmentID,d.Name,d.Budget,d.StartDate,d.Administrator
from Department as d
where d.DepartmentID=@DepartmentId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
Create PROCEDURE [dbo].[GetDepartmentsOfSpecifiedYear]
@Year int,@BudgetSum money output
AS
BEGIN
        SELECT @BudgetSum=SUM([Budget])
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

SELECT [DepartmentID]
      ,[Name]
      ,[Budget]
      ,[StartDate]
      ,[Administrator]
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[GradeOfStudent]
-- Add the parameters for the stored procedure here
@CourseTitle nvarchar(100),@FirstName nvarchar(50),
@LastName nvarchar(50),@Grade decimal(3,2) output
AS
BEGIN
select @Grade=Max(Grade)
from [dbo].[StudentGrade] as s join [dbo].[Course] as c on
s.CourseID=c.CourseID join [dbo].[Person] as p on s.StudentID=p.PersonID
where c.Title=@CourseTitle and p.FirstName=@FirstName
and p.LastName= @LastName
END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[InsertPerson]
-- Add the parameters for the stored procedure here
@FirstName nvarchar(50),@LastName nvarchar(50),
@PersonID int output
AS
BEGIN
    insert [dbo].[Person](LastName,FirstName) Values(@LastName,@FirstName)

    set @PersonID=SCOPE_IDENTITY()
END
Go

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
SET ANSI_PADDING ON
GO
CREATE TABLE [dbo].[Person]([PersonID] [int] IDENTITY(1,1) NOT NULL,
[LastName] [nvarchar](50) NOT NULL,
[FirstName] [nvarchar](50) NOT NULL,
[HireDate] [datetime] NULL,
[EnrollmentDate] [datetime] NULL,
[Picture] [varbinary](max) NULL,
 CONSTRAINT [PK_School.Student] PRIMARY KEY CLUSTERED
(
[PersonID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[StudentGrade]([EnrollmentID] [int] IDENTITY(1,1) NOT NULL,
[CourseID] [nvarchar](10) NOT NULL,
[StudentID] [int] NOT NULL,
[Grade] [decimal](3, 2) NOT NULL,
 CONSTRAINT [PK_StudentGrade] PRIMARY KEY CLUSTERED
(
[EnrollmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create view [dbo].[EnglishCourse]
as
select c.CourseID,c.Title,c.Credits,c.DepartmentID
from Course as c join Department as d on c.DepartmentID=d.DepartmentID
where d.Name=N'English'

GO
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)
SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF
SET IDENTITY_INSERT [dbo].[Person] ON

INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (1, N'Hu', N'Nan', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (2, N'Norman', N'Laura', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (3, N'Olivotto', N'Nino', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (4, N'Anand', N'Arturo', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (5, N'Jai', N'Damien', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (6, N'Holt', N'Roger', CAST(0x000097F100000000 AS DateTime), NULL)
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (7, N'Martin', N'Randall', CAST(0x00008B1A00000000 AS DateTime), NULL)
SET IDENTITY_INSERT [dbo].[Person] OFF
SET IDENTITY_INSERT [dbo].[StudentGrade] ON

INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (1, N'C1045', 1, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (2, N'C1045', 2, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (3, N'C1045', 3, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (4, N'C1045', 4, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (5, N'C1045', 5, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (6, N'C1061', 1, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (7, N'C1061', 3, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (8, N'C1061', 4, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (9, N'C1061', 5, CAST(1.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (10, N'C2021', 1, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (11, N'C2021', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (12, N'C2021', 4, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (13, N'C2021', 5, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (14, N'C2042', 1, CAST(2.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (15, N'C2042', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (16, N'C2042', 3, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (17, N'C2042', 5, CAST(3.00 AS Decimal(3, 2)))
SET IDENTITY_INSERT [dbo].[StudentGrade] OFF
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
ALTER TABLE [dbo].[StudentGrade]  WITH CHECK ADD  CONSTRAINT [FK_StudentGrade_Student] FOREIGN KEY([StudentID])
REFERENCES [dbo].[Person] ([PersonID])
GO
ALTER TABLE [dbo].[StudentGrade] CHECK CONSTRAINT [FK_StudentGrade_Student]
GO
```

Následuje výpis kódu:

> [!TIP]
> Výpis kódu odkazuje na soubor databáze Access s názvem MySchool. mdb. MySchool. mdb můžete stáhnout (jako součást kompletního ukázkového projektu C# nebo Visual Basic) z [Code.MSDN.Microsoft.com](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).

```csharp
using System;
using System.Data;
using System.Data.OleDb;
using System.Data.SqlClient;

class Program {
   static void Main(string[] args) {
      String SqlDbConnectionString = "Data Source=(local);Initial Catalog=MySchool;Integrated Security=True;Asynchronous Processing=true;";

      InsertPerson(SqlDbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      InsertPersonInAdapter(SqlDbConnectionString, "Peter", "Krebs");
      Console.WriteLine();

      String oledbConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0; Data Source=Database\\MySchool.mdb";
      InsertPersonInJet4Database(oledbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      Console.WriteLine("Please press any key to exit.....");
      Console.ReadKey();
   }

   // Using stored procedure to insert a new row and retrieve the identity value
   static void InsertPerson(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";

      using (SqlConnection conn = new SqlConnection(connectionString)) {
         using (SqlCommand cmd = new SqlCommand(commandText, conn)) {
            cmd.CommandType = CommandType.StoredProcedure;

            cmd.Parameters.Add(new SqlParameter("@FirstName", firstName));
            cmd.Parameters.Add(new SqlParameter("@LastName", lastName));
            SqlParameter personId = new SqlParameter("@PersonID", SqlDbType.Int);
            personId.Direction = ParameterDirection.Output;
            cmd.Parameters.Add(personId);

            conn.Open();
            cmd.ExecuteNonQuery();

            Console.WriteLine("Person Id of new person:{0}", personId.Value);
         }
      }
   }

   // Using stored procedure in adapter to insert new rows and update the identity value.
   static void InsertPersonInAdapter(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";
      using (SqlConnection conn = new SqlConnection(connectionString)) {
         SqlDataAdapter mySchool = new SqlDataAdapter("Select PersonID,FirstName,LastName from [dbo].[Person]", conn);

         mySchool.InsertCommand = new SqlCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.StoredProcedure;

         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@FirstName", SqlDbType.NVarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@LastName", SqlDbType.NVarChar, 50, "LastName"));

         SqlParameter personId = mySchool.InsertCommand.Parameters.Add(new SqlParameter("@PersonID", SqlDbType.Int, 0, "PersonID"));
         personId.Direction = ParameterDirection.Output;

         DataTable persons = new DataTable();
         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         mySchool.Update(persons);
         Console.WriteLine("Show all persons:");
         ShowDataTable(persons, 14);
      }
   }

   /// For a Jet 4.0 database, we need use the single statement and event handler to insert new rows and retrieve the identity value.
   static void InsertPersonInJet4Database(String connectionString, String firstName, String lastName) {
      String commandText = "Insert into Person(FirstName,LastName) Values(?,?)";
      using (OleDbConnection conn = new OleDbConnection(connectionString)) {
         OleDbDataAdapter mySchool = new OleDbDataAdapter("Select PersonID,FirstName,LastName from Person", conn);

         // Create Insert Command
         mySchool.InsertCommand = new OleDbCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.Text;

         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@FirstName", OleDbType.VarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@LastName", OleDbType.VarChar, 50, "LastName"));
         mySchool.InsertCommand.UpdatedRowSource = UpdateRowSource.Both;

         DataTable persons = CreatePersonsTable();

         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         DataTable dataChanges = persons.GetChanges();

         mySchool.RowUpdated += OnRowUpdated;

         mySchool.Update(dataChanges);

         Console.WriteLine("Data before merging:");
         ShowDataTable(persons, 14);
         Console.WriteLine();

         persons.Merge(dataChanges);
         persons.AcceptChanges();

         Console.WriteLine("Data after merging");
         ShowDataTable(persons, 14);
      }
   }

   static void OnRowUpdated(object sender, OleDbRowUpdatedEventArgs e) {
      if (e.StatementType == StatementType.Insert) {
         // Retrieve the identity value
         OleDbCommand cmdNewId = new OleDbCommand("Select @@IDENTITY", e.Command.Connection);
         e.Row["PersonID"] = (Int32)cmdNewId.ExecuteScalar();

         // After the status is changed, the original values in the row are preserved. And the
         // Merge method will be called to merge the new identity value into the original DataTable.
         e.Status = UpdateStatus.SkipCurrentRow;
      }
   }

   // Create the Persons table before filling.
   private static DataTable CreatePersonsTable() {
      DataTable persons = new DataTable();

      DataColumn personId = new DataColumn();
      personId.DataType = Type.GetType("System.Int32");
      personId.ColumnName = "PersonID";
      personId.AutoIncrement = true;
      personId.AutoIncrementSeed = 0;
      personId.AutoIncrementStep = -1;
      persons.Columns.Add(personId);

      DataColumn firstName = new DataColumn();
      firstName.DataType = Type.GetType("System.String");
      firstName.ColumnName = "FirstName";
      persons.Columns.Add(firstName);

      DataColumn lastName = new DataColumn();
      lastName.DataType = Type.GetType("System.String");
      lastName.ColumnName = "LastName";
      persons.Columns.Add(lastName);

      DataColumn[] pkey = { personId };
      persons.PrimaryKey = pkey;

      return persons;
   }

   private static void ShowDataTable(DataTable table, Int32 length) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-" + length + "}", col.ColumnName);
      }
      Console.WriteLine();

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-" + length + ":d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-" + length + ":C}", row[col]);
            else
               Console.Write("{0,-" + length + "}", row[col]);
         }

         Console.WriteLine();
      }
   }
}
```

## <a name="see-also"></a>Viz také

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Stavy řádků a verze řádků](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges a RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Slučování obsahu datové sady](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Přehled ADO.NET](ado-net-overview.md)
