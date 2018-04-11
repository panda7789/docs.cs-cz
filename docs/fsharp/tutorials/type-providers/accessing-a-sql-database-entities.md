---
title: 'Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit (F#)'
description: 'Zjistěte, jak pro přístup k zadaných dat pro databázi SQL, který je založen na modelu ADO.NET Entity Data v F # 3.0.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](https://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Tento návod pro jazyk F# 3.0 popisuje možnosti přístupu k typovým datům databáze SQL na základě datového modelu entity ADO.NET. Tento postup vám ukáže, jak nastavit F # `SqlEntityConnection` pro použití s databázi SQL, jak psát dotazy na data, jak volat uložené procedury v databázi, jakož i jak používat některé typy ADO.NET Entity Framework a metody k upd – zprostředkovatel typu uje databáze.

Tento návod znázorňuje následující úkoly, které je nutné z důvodu správné funkčnosti provést v tomto pořadí:


- Vytvoření databáze školy
<br />

- Vytvoření a konfigurace projektu v jazyce F#
<br />

- Nakonfigurujte typ poskytovatele a připojte se k datového modelu Entity
<br />

- Dotaz na databázi
<br />

- Aktualizace databáze
<br />


## <a name="prerequisites"></a>Požadavky
K dokončení těchto kroků je vyžadován přístup k systému SQL Server, kde můžete databázi vytvořit.

## <a name="create-the-school-database"></a>Vytvoření databáze školy
Databázi školy můžete vytvořit na libovolném serveru, na kterém je spuštěn systém SQL Server, k němuž máte přístup správce, nebo můžete použít databázi LocalDB.


#### <a name="to-create-the-school-database"></a>Postup vytvoření databáze školy

1. V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat** uzel a potom zvolte **přidat připojení**.
<br />  **Přidat připojení** zobrazí se dialogové okno.
<br />

2. V **název serveru** pole, zadejte název instance systému SQL Server, ke kterému mají přístup pro správu nebo zadejte (localdb\v11.0), pokud nemáte přístup k serveru.
<br />  Databáze SQL Server Express LocalDB poskytuje jednoduchý databázový server pro vývoj a testování na vašem počítači. Další informace o LocalDB najdete v tématu [návod: Vytvoření místního souboru databáze v sadě Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).
<br />  Vytvoří se nový uzel v **Průzkumníka serveru** pod **datová připojení**.
<br />

3. Otevřete místní nabídku pro nový uzel připojení a potom zvolte **nový dotaz**.
<br />

4. Otevřete [vytváření ukázkovou databázi školy](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) na webu společnosti Microsoft a potom zkopírovat a vložit databázového skriptu vytvářející databázi školy do okna editoru.
<br />


## <a name="BKMK_CreateConfigFSProj"></a>

## <a name="create-and-configure-an-f-project"></a>Vytvoření a konfigurace projektu v jazyce F#
V tomto kroku vytvoříte projekt a nastavíte jej pro používání poskytovatele typu.


#### <a name="to-create-and-configure-an-f-project"></a>Postup vytvoření a konfigurace projektu jazyka F#

1. Zavřete předchozí projektu, vytvořte jiný projekt s názvem **SchoolEDM**.
<br />

2. V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.
<br />

3. Vyberte **Framework** uzel a pak na **Framework** vyberte **System.Data**, **System.Data.Entity**a **System.Data.Linq**.
<br />

4. Vyberte **rozšíření** uzlu, přidejte odkaz na [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) sestavení a potom zvolte **OK** tlačítko Zavřít dialogové okno.
<br />

5. Pro definování vnitřního modulu a otevření příslušných oborů názvů přidejte následující kód. Poskytovatel typu může vložit typy pouze do soukromého nebo interního oboru názvů.
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. Spustí kód v tomto návodu interaktivně jako skript místo jako kompilované program, otevřete místní nabídce uzlu projektu, zvolte **přidat novou položku**, přidání souboru skriptu F # a pak přidejte do skriptu kód v jednotlivých kroků. Chcete-li načíst odkazy na sestavení, přidejte následující řádky.
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. Jakmile přidáte každý blok kódu, zvýrazněte jej a stiskněte klávesovou zkratku Alt+Enter, abyste kód spustili pomocí součásti F# Interactive.
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Konfigurace poskytovatele typu a připojení k modelu Entity Data Model
V tomto kroku nastavíte poskytovatele typu pomocí datového připojení a získáte kontext dat, který umožňuje práci s daty.


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Postup konfigurace poskytovatele typu a připojení k modelu Entity Data Model

1. Zadejte následující kód do konfigurace `SqlEntityConnection` typ zprostředkovatele, který generuje typů F # podle Entity Data Model, který jste vytvořili dříve. Namísto úplného připojovacího řetězce modelu EDMX použijte pouze připojovací řetězec databáze SQL.
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  Tato akce nastaví poskytovatele typu pomocí připojení k databázi, které jste vytvořili dříve. Vlastnost `MultipleActiveResultSets` je potřeba, když používáte ADO.NET Entity Framework, protože tato vlastnost umožňuje více příkazů pro spuštění asynchronně na databázi v jedno připojení, kterému může dojít, často v kódu ADO.NET Entity Framework. Další informace najdete v tématu [více sad Active výsledek (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).
<br />

2. Získáte kontext dat, což je objekt obsahující tabulky databáze jako vlastnosti a uložené procedury a funkce databáze jako metody.
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>Dotazování na databázi
V tomto kroku použijete výrazy dotazu jazyka F# ke spuštění různých dotazů v databázi.


#### <a name="to-query-the-data"></a>Postup dotazování na data

- Chcete-li zadat dotaz na data z modelu Entity Data Model, použijte následující kód. Pamatujte, že parametr Pluralize má hodnotu true, čímž dojde ke změně tabulky databáze z položky Kurz na položku Kurzy a z položky Osoba na položku Lidé.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a>Aktualizace databáze
Chcete-li databázi aktualizovat, použijte třídy a metody rozhraní Entity Framework. Poskytovatel typu SQLEntityConnection může používat dva typy kontextu dat. První, `ServiceTypes.SimpleDataContextTypes.EntityContainer` je zjednodušená data kontext, který obsahuje pouze zadané vlastnosti, které představují databázových tabulek a sloupců. Druhou, kontextu úplné dat je instance třídy rozhraní Entity Framework `System.Data.Objects.ObjectContext`, který obsahuje metodu `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` přidání řádků do databáze. Rozhraní Entity Framework rozpoznává tabulky a vztahy mezi nimi, čímž zajišťuje konzistenci databáze.


#### <a name="to-update-the-database"></a>Postup aktualizace databáze

1. Do programu přidejte následující kód. V tomto příkladu přidáte dva objekty se vztahem mezi nimi a poté přidáte školitele a přiřazení kanceláře. V tabulce `OfficeAssignments` obsahuje `InstructorID` sloupec, který odkazuje `PersonID` sloupec v `Person` tabulky.
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

Nic se změnilo v databázi, dokud zavoláte `System.Data.Objects.ObjectContext.SaveChanges`.
<br />

2. Nyní databázi obnovte do předchozího stavu odstraněním objektů, které jste přidali.
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
Pokud použijete výraz dotazu, je nutné si pamatovat, že dotaz je vyhodnocen opožděně. Databáze je tedy stále otevřena pro čtení během jakýchkoliv zřetězených vyhodnocení, jako například v blocích výrazu lambda po každém výrazu dotazu. Všechny operace databáze, které explicitně nebo implicitně používají transakci, musí být provedeny po dokončení operací čtení.


## <a name="next-steps"></a>Další kroky
Prozkoumat další možnosti dotazu kontrolou operátory dotazu, který je k dispozici v [výrazy dotazů](../../language-reference/query-expressions.md)a také zkontrolovat [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) pochopit, jaké funkce je k dispozici při můžete použít tento typ poskytovatele.


## <a name="see-also"></a>Viz také
[Zprostředkovatelé typů](index.md)  
[Sqlentityconnection – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[Návod: Generování typů F # ze souboru schématu EDMX](generating-fsharp-types-from-edmx.md)  
[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)  
[Přehled souboru EDMX](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[Generátor EDM &#40;EdmGen.exe&#41;](https://msdn.microsoft.com/library/bb387165)  
