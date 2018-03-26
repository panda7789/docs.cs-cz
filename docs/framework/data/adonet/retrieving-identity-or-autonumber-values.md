---
title: Načítání Identity nebo hodnoty automatické číslování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 15c435d46d3695f78db27801f54ec9de475b2989
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="retrieving-identity-or-autonumber-values"></a>Načítání Identity nebo hodnoty automatické číslování
Primární klíče v relační databázi je sloupec nebo kombinace sloupců, které vždy obsahovat jedinečné hodnoty. Znalost hodnotu primárního klíče umožňuje umístit na řádek, který jej obsahuje. Relační databáze weby, jako je například SQL Server, Oracle a Microsoft Access/Jet podporují vytvoření automaticky zvyšování sloupce, které lze určit jako primární klíče. Tyto hodnoty generované serverem při přidávání řádků do tabulky. V systému SQL Server nastavte vlastnost identity sloupce v Oracle vytvoříte pořadí a v aplikaci Microsoft Access vytvořit sloupec Automatické číslo.  
  
 A <xref:System.Data.DataColumn> lze také použít ke generování hodnot automaticky narůstajícími nastavením <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnost na hodnotu true. Však může skončili s duplicitními hodnotami v samostatné instance <xref:System.Data.DataTable>, pokud se více aplikací klienta nezávisle na nástroji generují automaticky narůstajícími hodnoty. Server pro generování hodnot automaticky narůstajícími eliminuje potenciální konflikty tím, že každý uživatel k načtení generované hodnoty pro každý vloženého řádku.  
  
 Během volání `Update` metodu `DataAdapter`, databáze může odesílat data zpět do aplikace ADO.NET jako výstupní parametry, nebo jako první vrácená záznam sady výsledků dotazu příkazu SELECT provést v dávce stejný jako příkaz INSERT. Získat tyto hodnoty a aktualizovat na odpovídající sloupce v ADO.NET <xref:System.Data.DataRow> aktualizované.  
  
 Některé databázové stroje, jako je například databázový stroj Microsoft Jet přístup, nepodporuje výstupní parametry a nemůže zpracovat více příkazů v jedné dávce. Při práci s databázový stroj, můžete načíst nová hodnota Automatické číslování vygenerované vloženého řádku spuštěním samostatný příkaz SELECT v obslužné rutiny události pro `RowUpdated` události `DataAdapter`.  
  
> [!NOTE]
>  Alternativu k použití automaticky přírůstkovou hodnotou je použití <xref:System.Guid.NewGuid%2A> metodu <xref:System.Guid> objekt, který chcete generovat identifikátor GUID nebo globálně jedinečný identifikátor v klientském počítači, který je možné zkopírovat do serveru, jako je vložen každý nový řádek. `NewGuid` Metoda generuje 16 bajtů binární hodnotu, která je vytvořena pomocí algoritmu, který poskytuje vysokou pravděpodobnost, že žádná hodnota bude duplicitní. V databázi systému SQL Server, je identifikátor GUID uložené v `uniqueidentifier` sloupec, který systému SQL Server může automaticky generovat pomocí jazyka Transact-SQL `NEWID()` funkce. Pomocí identifikátor GUID jako primární klíč může nepříznivě ovlivnit výkon. [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] poskytuje podporu pro `NEWSEQUENTIALID()` funkci, která generuje sekvenční identifikátor GUID, který není musí být globálně jedinečný, ale který lze efektivněji indexovat.  
  
## <a name="retrieving-sql-server-identity-column-values"></a>Načítání hodnot sloupce Identity serveru SQL  
 Při práci se službou Microsoft SQL Server, můžete vytvořit uložené procedury s výstupní parametr vrátit hodnotu identity pro vloženého řádku. Následující tabulka popisuje tři funkce jazyka Transact-SQL v systému SQL Server, který slouží k načtení hodnoty pro sloupec identity.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|SCOPE_IDENTITY|Vrátí poslední hodnotu identity v aktuálním oboru provádění. SCOPE_IDENTITY se doporučuje pro většinu scénářů.|  
|@@IDENTITY|Obsahuje poslední hodnotu identity vygenerovaných všechny tabulky v aktuální relaci. @@IDENTITY může být ovlivněno aktivační události a nemusí vracet hodnotu identity, které očekáváte.|  
|IDENT_CURRENT|Vrátí poslední hodnotu identity vygenerované určité tabulky v jakékoli relace a jakémkoli oboru.|  
  
 Následující uložené procedury ukazuje, jak o vložení řádku do **kategorie** tabulky a použít výstupní parametr, který vrátí novou hodnotu identity generované funkce SCOPE_IDENTITY() Transact-SQL.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 Uloženou proceduru lze poté jako zdroj <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter> objektu. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Vlastnost <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> musí být nastavena na <xref:System.Data.CommandType.StoredProcedure>. Výstup identity jsou načítána pro vytváření <xref:System.Data.SqlClient.SqlParameter> má <xref:System.Data.ParameterDirection> z <xref:System.Data.ParameterDirection.Output>. Při `InsertCommand` je zpracovat, je na hodnotu automaticky zvýší identity vrátí a uložena v umístění **CategoryID** sloupec na aktuálním řádku, pokud jste nastavili <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> vlastnost příkazu insert `UpdateRowSource.OutputParameters` nebo `UpdateRowSource.Both`.  
  
 Pokud váš příkaz insert provede dávky, která zahrnuje příkazu INSERT a příkaz SELECT, který vrátí novou hodnotu identity, pak můžete načíst nová hodnota nastavením `UpdatedRowSource` vlastnost příkazu insert `UpdateRowSource.FirstReturnedRecord`.  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## <a name="merging-new-identity-values"></a>Slučování nové hodnoty Identity  
 Obvyklým scénářem je k volání `GetChanges` metodu `DataTable` vytvořit kopii, která obsahuje pouze změněných řádků a použít nové kopie při volání metody `Update` metodu `DataAdapter`. Toto je obzvláště užitečná, když potřebujete zařazování změněných řádků samostatné součásti, která provede aktualizace. Následující aktualizace, může obsahovat kopie nové hodnoty identity, které je potřeba sloučit pak zpět do původní `DataTable`. Nové hodnoty identity by mohly být liší od původní hodnoty `DataTable`. K provedení sloučení, původní hodnoty **AutoIncrement** sloupce do kopie musí být zachováno, aby bylo možné najít a aktualizovat existující řádky v původním `DataTable`, místo připojování nové řádky obsahující nové hodnoty identity. Ve výchozím nastavení tyto původní hodnoty jsou však ztraceny po volání `Update` metodu `DataAdapter`, protože `AcceptChanges` je implicitně volána pro každou aktualizovat `DataRow`.  
  
 Existují dva způsoby, chcete-li zachovat původní hodnoty `DataColumn` v `DataRow` během `DataAdapter` aktualizace:  
  
-   První metoda zachování původní hodnoty je nastavit `AcceptChangesDuringUpdate` vlastnost `DataAdapter` k `false`. Tato akce ovlivní všechny `DataRow` v `DataTable` aktualizované. Příklad kódu a další informace najdete v tématu <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.  
  
-   Druhý způsob spočívá v psaní kódu `RowUpdated` obslužnou rutinu události `DataAdapter` nastavit <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow>. `DataRow` Se aktualizuje ale původní hodnotu jednotlivých `DataColumn` se zachová. Tato metoda umožňuje zachovat původní hodnoty, u některých řádků a nikoli pro ostatní uživatele. Například můžete zachovat původní hodnoty pro přidání řádků a ne pro upravené nebo odstraněné řádků první kontrolou kódu <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> a nastavením <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow> pouze pro řádky s `StatementType` z `Insert`.  
  
 Pokud některý z těchto metod se používá k zachovat původní hodnoty v `DataRow` během `DataAdapter` aktualizace, ADO.NET provádí sérii akcí nastavit aktuální hodnoty `DataRow` nové hodnoty vrátí výstupní parametry, nebo první Vrátí řádek je sada výsledků dotazu při zachování stále původní hodnoty v jednotlivých `DataColumn`. Nejdřív `AcceptChanges` metodu `DataRow` je volána, pokud chcete zachovat aktuální hodnoty jako původní hodnoty, a poté jsou přiřazeny s novými hodnotami. Následující tyto akce `DataRows` , měl jejich <xref:System.Data.DataRow.RowState%2A> vlastnost nastavena na hodnotu <xref:System.Data.DataRowState.Added> bude mít jejich `RowState` vlastnost nastavena na hodnotu <xref:System.Data.DataRowState.Modified>, což může neočekávaná.  
  
 Jak jsou výsledky příkazu použitá pro každé <xref:System.Data.DataRow> aktualizované je dáno <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnost jednotlivých <xref:System.Data.Common.DbCommand>. Tato vlastnost nastavena na hodnotu z `UpdateRowSource` výčtu.  
  
 Následující tabulka popisuje jak `UpdateRowSource` hodnot výčtu vliv <xref:System.Data.DataRow.RowState%2A> vlastnost aktualizované řádky.  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges` je volána a obě výstup hodnoty parametrů a hodnoty v prvním řádku všechny vrácené výsledné sady jsou umístěny v `DataRow` aktualizované. Pokud neexistují žádné hodnoty, které chcete použít, `RowState` bude <xref:System.Data.DataRowState.Unchanged>.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Řádek byl vrácen, `AcceptChanges` nazývá a řádek je namapovaná na řádek změněné v `DataTable`, nastavení `RowState` k `Modified`. Pokud je vrácen žádný řádek, pak `AcceptChanges` není volán a `RowState` zůstane `Added`.|  
|<xref:System.Data.UpdateRowSource.None>|Všechny vrácené parametry řádky budou ignorovány. Neexistuje žádná volání `AcceptChanges` a `RowState` zůstane `Added`.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges` je volána a všechny výstupní parametry jsou namapované na změněných řádků v `DataTable`, nastavení `RowState` k `Modified`. Pokud nejsou žádná výstupní parametry `RowState` bude `Unchanged`.|  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje extrahování změněných řádků z `DataTable` a použití <xref:System.Data.SqlClient.SqlDataAdapter> k aktualizaci zdroje dat a načtení nová hodnota sloupce identity. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Provede dva příkazy jazyka Transact-SQL; první z nich je příkazu INSERT a druhý je příkaz SELECT, který používá funkci SCOPE_IDENTITY k načtení hodnoty identity.  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 `UpdatedRowSource` Příkazu insert je nastavena na `UpdateRowSource.FirstReturnedRow` a <xref:System.Data.MissingSchemaAction> vlastnost `DataAdapter` je nastaven na `MissingSchemaAction.AddWithKey`. `DataTable` Vyplněno a kód přidá nový řádek, abyste `DataTable`. Změněných řádků se pak extrahují do nového `DataTable`, který je předán `DataAdapter`, který pak aktualizací na server.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` Kontroly obslužné rutiny událostí <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> z <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> k určení, zda řádek je typu vložení. Pokud je, pak se <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> je nastavena na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Řádek byl aktualizován, ale se zachovají původní hodnoty v řádku. Hlavní body procesu <xref:System.Data.DataSet.Merge%2A> metoda je volána sloučit novou hodnotu identity do původní `DataTable`a v neposlední řadě `AcceptChanges` je volána.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## <a name="retrieving-microsoft-access-autonumber-values"></a>Načítání hodnot automatické číslování Microsoft Access  
 Tato část obsahuje vzorku, který ukazuje, jak načíst `Autonumber` hodnoty z databáze Jet 4.0. Databázový stroj nepodporuje provádění více příkazů v dávce nebo použití výstupní parametry, takže není možné použít některou z těchto postupů a vrátí nové `Autonumber` hodnotu přiřazenou vloženého řádku. Můžete však přidat kód pro `RowUpdated` obslužné rutiny události, které provádí samostatné vyberte @@IDENTITY příkaz načíst nové `Autonumber` hodnotu.  
  
### <a name="example"></a>Příklad  
 Místo přidávání schématu informací pomocí `MissingSchemaAction.AddWithKey`, tento příklad konfiguruje `DataTable` s správné schéma před voláním <xref:System.Data.OleDb.OleDbDataAdapter> k vyplnění `DataTable`. V takovém případě **CategoryID** sloupec je nakonfigurovaný se sníží hodnotu přiřazenou každý vloženého řádku od nula, a to nastavením <xref:System.Data.DataColumn.AutoIncrement%2A> k `true`, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> na hodnotu 0, a <xref:System.Data.DataColumn.AutoIncrementStep%2A> na hodnotu -1. Kód pak přidá dva nové řádky a používá `GetChanges` přidat změněných řádků na nový `DataTable` předá do `Update` metoda.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` Obslužné rutiny události používá stejné otevřete <xref:System.Data.OleDb.OleDbConnection> jako `Update` prohlášení o `OleDbDataAdapter`. Zkontroluje `StatementType` z <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> pro vložit řádky. Pro každou vložit řádek novou <xref:System.Data.OleDb.OleDbCommand> se vytvoří pro spuštění vyberte @@IDENTITY příkazu k připojení, vrácení nové `Autonumber` hodnotu, která je umístěn v **CategoryID** sloupec `DataRow`. `Status` Je pak nastavena na `UpdateStatus.SkipCurrentRow` potlačit skrytá volání `AcceptChanges`. Hlavní body procesu `Merge` metoda je volána sloučit dva `DataTable` objekty a v neposlední řadě `AcceptChanges` je volána.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### <a name="retrieving-identity-values"></a>Načítání hodnoty Identity  
 Často nastaví sloupec identitou při hodnoty ve sloupci musí být jedinečné. A někdy potřebujeme hodnotu identity nová data. Tento příklad ukazuje, jak načíst hodnoty identity:  
  
-   Vytvoří uložené procedury k vkládání dat a vrátí hodnotu identity.  
  
-   Spustí příkaz pro vložení nová data a zobrazit výsledek.  
  
-   Používá <xref:System.Data.SqlClient.SqlDataAdapter> vkládat nová data a zobrazit výsledek.  
  
 Před zkompilování a spuštění ukázky, je třeba vytvořit ukázkové databáze pomocí následující skript:  
  
```  
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
  
 Kód výpis následovně:  
  
> [!IMPORTANT]
>  Výpis kódu odkazuje na soubor databáze aplikace Access názvem MySchool.mdb. MySchool.mdb (jako součást úplný ukázkový projekt C# nebo Visual Basic) můžete stáhnout z buď [ukázkové sady Visual Studio 2012](http://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43) nebo [ukázkové sady Visual Studio 2013](http://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).  
  
```  
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
  
   /// For a Jet 4.0 database, we need use the sigle statement and event handler to insert new rows and retrieve the identity value.  
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
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Stavy řádků a verze řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Metody AcceptChanges a RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [Slučování obsahu datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
