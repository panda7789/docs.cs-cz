---
title: "Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit (F#)"
description: "Zjistěte, jak pro přístup k zadaných dat pro databázi SQL, který je založen na modelu ADO.NET Entity Data v F # 3.0."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 770d405921758eeb7e8d7ea98b95c29c99631475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="55d62-104">Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit</span><span class="sxs-lookup"><span data-stu-id="55d62-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="55d62-105">Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="55d62-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="55d62-106">V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="55d62-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="55d62-107">Rozhraní API referenčních odkazů se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="55d62-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="55d62-108">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="55d62-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="55d62-109">Tento návod pro jazyk F# 3.0 popisuje možnosti přístupu k typovým datům databáze SQL na základě datového modelu entity ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="55d62-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="55d62-110">Tento postup vám ukáže, jak nastavit F # `SqlEntityConnection` pro použití s databázi SQL, jak psát dotazy na data, jak volat uložené procedury v databázi, jakož i jak používat některé typy ADO.NET Entity Framework a metody k upd – zprostředkovatel typu uje databáze.</span><span class="sxs-lookup"><span data-stu-id="55d62-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="55d62-111">Tento návod znázorňuje následující úkoly, které je nutné z důvodu správné funkčnosti provést v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="55d62-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="55d62-112">Vytvoření databáze školy</span><span class="sxs-lookup"><span data-stu-id="55d62-112">Create the School database</span></span>
<br />

- <span data-ttu-id="55d62-113">Vytvoření a konfigurace projektu v jazyce F#</span><span class="sxs-lookup"><span data-stu-id="55d62-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="55d62-114">Nakonfigurujte typ poskytovatele a připojte se k datového modelu Entity</span><span class="sxs-lookup"><span data-stu-id="55d62-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="55d62-115">Dotaz na databázi</span><span class="sxs-lookup"><span data-stu-id="55d62-115">Query the database</span></span>
<br />

- <span data-ttu-id="55d62-116">Aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="55d62-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="55d62-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55d62-117">Prerequisites</span></span>
<span data-ttu-id="55d62-118">K dokončení těchto kroků je vyžadován přístup k systému SQL Server, kde můžete databázi vytvořit.</span><span class="sxs-lookup"><span data-stu-id="55d62-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="55d62-119">Vytvoření databáze školy</span><span class="sxs-lookup"><span data-stu-id="55d62-119">Create the School database</span></span>
<span data-ttu-id="55d62-120">Databázi školy můžete vytvořit na libovolném serveru, na kterém je spuštěn systém SQL Server, k němuž máte přístup správce, nebo můžete použít databázi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="55d62-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="55d62-121">Postup vytvoření databáze školy</span><span class="sxs-lookup"><span data-stu-id="55d62-121">To create the School database</span></span>

1. <span data-ttu-id="55d62-122">V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat** uzel a potom zvolte **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="55d62-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="55d62-123">**Přidat připojení** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="55d62-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="55d62-124">V **název serveru** pole, zadejte název instance systému SQL Server, ke kterému mají přístup pro správu nebo zadejte (localdb\v11.0), pokud nemáte přístup k serveru.</span><span class="sxs-lookup"><span data-stu-id="55d62-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="55d62-125">Databáze SQL Server Express LocalDB poskytuje jednoduchý databázový server pro vývoj a testování na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="55d62-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="55d62-126">Další informace o LocalDB najdete v tématu [návod: Vytvoření místního souboru databáze v sadě Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="55d62-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="55d62-127">Vytvoří se nový uzel v **Průzkumníka serveru** pod **datová připojení**.</span><span class="sxs-lookup"><span data-stu-id="55d62-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="55d62-128">Otevřete místní nabídku pro nový uzel připojení a potom zvolte **nový dotaz**.</span><span class="sxs-lookup"><span data-stu-id="55d62-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="55d62-129">Otevřete [vytváření ukázkovou databázi školy](http://go.microsoft.com/fwlink/?LinkID=237278) na webu společnosti Microsoft a potom zkopírovat a vložit databázového skriptu vytvářející databázi studenty do okna editoru.</span><span class="sxs-lookup"><span data-stu-id="55d62-129">Open [Creating the School Sample Database](http://go.microsoft.com/fwlink/?LinkID=237278) on the Microsoft website, and then copy and paste the database script that creates the Student database into the editor window.</span></span>
<br />


## <span data-ttu-id="55d62-130"><a name="BKMK_CreateConfigFSProj"></a></span><span class="sxs-lookup"><span data-stu-id="55d62-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="55d62-131">Vytvoření a konfigurace projektu v jazyce F#</span><span class="sxs-lookup"><span data-stu-id="55d62-131">Create and configure an F# project</span></span>
<span data-ttu-id="55d62-132">V tomto kroku vytvoříte projekt a nastavíte jej pro používání poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="55d62-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="55d62-133">Postup vytvoření a konfigurace projektu jazyka F#</span><span class="sxs-lookup"><span data-stu-id="55d62-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="55d62-134">Zavřete předchozí projektu, vytvořte jiný projekt s názvem **SchoolEDM**.</span><span class="sxs-lookup"><span data-stu-id="55d62-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="55d62-135">V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="55d62-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="55d62-136">Vyberte **Framework** uzel a pak na **Framework** vyberte **System.Data**, **System.Data.Entity**a **System.Data.Linq**.</span><span class="sxs-lookup"><span data-stu-id="55d62-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="55d62-137">Vyberte **rozšíření** uzlu, přidejte odkaz na [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) sestavení a potom zvolte **OK** tlačítko Zavřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="55d62-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="55d62-138">Pro definování vnitřního modulu a otevření příslušných oborů názvů přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="55d62-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="55d62-139">Poskytovatel typu může vložit typy pouze do soukromého nebo interního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="55d62-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="55d62-140">Spustí kód v tomto návodu interaktivně jako skript místo jako kompilované program, otevřete místní nabídce uzlu projektu, zvolte **přidat novou položku**, přidání souboru skriptu F # a pak přidejte do skriptu kód v jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="55d62-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="55d62-141">Chcete-li načíst odkazy na sestavení, přidejte následující řádky.</span><span class="sxs-lookup"><span data-stu-id="55d62-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="55d62-142">Jakmile přidáte každý blok kódu, zvýrazněte jej a stiskněte klávesovou zkratku Alt+Enter, abyste kód spustili pomocí součásti F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="55d62-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="55d62-143">Konfigurace poskytovatele typu a připojení k modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="55d62-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="55d62-144">V tomto kroku nastavíte poskytovatele typu pomocí datového připojení a získáte kontext dat, který umožňuje práci s daty.</span><span class="sxs-lookup"><span data-stu-id="55d62-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="55d62-145">Postup konfigurace poskytovatele typu a připojení k modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="55d62-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="55d62-146">Zadejte následující kód do konfigurace `SqlEntityConnection` typ zprostředkovatele, který generuje typů F # podle Entity Data Model, který jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="55d62-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="55d62-147">Namísto úplného připojovacího řetězce modelu EDMX použijte pouze připojovací řetězec databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="55d62-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="55d62-148">Tato akce nastaví poskytovatele typu pomocí připojení k databázi, které jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="55d62-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="55d62-149">Vlastnost `MultipleActiveResultSets` je potřeba, když používáte ADO.NET Entity Framework, protože tato vlastnost umožňuje více příkazů pro spuštění asynchronně na databázi v jedno připojení, kterému může dojít, často v kódu ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="55d62-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="55d62-150">Další informace najdete v tématu [více sad Active výsledek (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span><span class="sxs-lookup"><span data-stu-id="55d62-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="55d62-151">Získáte kontext dat, což je objekt obsahující tabulky databáze jako vlastnosti a uložené procedury a funkce databáze jako metody.</span><span class="sxs-lookup"><span data-stu-id="55d62-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="55d62-152">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="55d62-152">Querying the database</span></span>
<span data-ttu-id="55d62-153">V tomto kroku použijete výrazy dotazu jazyka F# ke spuštění různých dotazů v databázi.</span><span class="sxs-lookup"><span data-stu-id="55d62-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="55d62-154">Postup dotazování na data</span><span class="sxs-lookup"><span data-stu-id="55d62-154">To query the data</span></span>

- <span data-ttu-id="55d62-155">Chcete-li zadat dotaz na data z modelu Entity Data Model, použijte následující kód.</span><span class="sxs-lookup"><span data-stu-id="55d62-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="55d62-156">Pamatujte, že parametr Pluralize má hodnotu true, čímž dojde ke změně tabulky databáze z položky Kurz na položku Kurzy a z položky Osoba na položku Lidé.</span><span class="sxs-lookup"><span data-stu-id="55d62-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
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

## <a name="updating-the-database"></a><span data-ttu-id="55d62-157">Aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="55d62-157">Updating the database</span></span>
<span data-ttu-id="55d62-158">Chcete-li databázi aktualizovat, použijte třídy a metody rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="55d62-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="55d62-159">Poskytovatel typu SQLEntityConnection může používat dva typy kontextu dat.</span><span class="sxs-lookup"><span data-stu-id="55d62-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="55d62-160">První, `ServiceTypes.SimpleDataContextTypes.EntityContainer` je zjednodušená data kontext, který obsahuje pouze zadané vlastnosti, které představují databázových tabulek a sloupců.</span><span class="sxs-lookup"><span data-stu-id="55d62-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="55d62-161">Druhou, kontextu úplné dat je instance třídy rozhraní Entity Framework `System.Data.Objects.ObjectContext`, který obsahuje metodu `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` přidání řádků do databáze.</span><span class="sxs-lookup"><span data-stu-id="55d62-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="55d62-162">Rozhraní Entity Framework rozpoznává tabulky a vztahy mezi nimi, čímž zajišťuje konzistenci databáze.</span><span class="sxs-lookup"><span data-stu-id="55d62-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="55d62-163">Postup aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="55d62-163">To update the database</span></span>

1. <span data-ttu-id="55d62-164">Do programu přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="55d62-164">Add the following code to your program.</span></span> <span data-ttu-id="55d62-165">V tomto příkladu přidáte dva objekty se vztahem mezi nimi a poté přidáte školitele a přiřazení kanceláře.</span><span class="sxs-lookup"><span data-stu-id="55d62-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="55d62-166">V tabulce `OfficeAssignments` obsahuje `InstructorID` sloupec, který odkazuje `PersonID` sloupec v `Person` tabulky.</span><span class="sxs-lookup"><span data-stu-id="55d62-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
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

<span data-ttu-id="55d62-167">Nic se změnilo v databázi, dokud zavoláte `System.Data.Objects.ObjectContext.SaveChanges`.</span><span class="sxs-lookup"><span data-stu-id="55d62-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="55d62-168">Nyní databázi obnovte do předchozího stavu odstraněním objektů, které jste přidali.</span><span class="sxs-lookup"><span data-stu-id="55d62-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
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
<span data-ttu-id="55d62-169">Pokud použijete výraz dotazu, je nutné si pamatovat, že dotaz je vyhodnocen opožděně.</span><span class="sxs-lookup"><span data-stu-id="55d62-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="55d62-170">Databáze je tedy stále otevřena pro čtení během jakýchkoliv zřetězených vyhodnocení, jako například v blocích výrazu lambda po každém výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="55d62-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="55d62-171">Všechny operace databáze, které explicitně nebo implicitně používají transakci, musí být provedeny po dokončení operací čtení.</span><span class="sxs-lookup"><span data-stu-id="55d62-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="55d62-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="55d62-172">Next Steps</span></span>
<span data-ttu-id="55d62-173">Prozkoumat další možnosti dotazu kontrolou operátory dotazu, který je k dispozici v [výrazy dotazů](../../language-reference/query-expressions.md)a také zkontrolovat [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) pochopit, jaké funkce je k dispozici při můžete použít tento typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="55d62-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="55d62-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="55d62-174">See Also</span></span>
[<span data-ttu-id="55d62-175">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="55d62-175">Type Providers</span></span>](index.md)

[<span data-ttu-id="55d62-176">Sqlentityconnection – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="55d62-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="55d62-177">Návod: Generování typů F # ze souboru schématu EDMX</span><span class="sxs-lookup"><span data-stu-id="55d62-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)

[<span data-ttu-id="55d62-178">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="55d62-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)

[<span data-ttu-id="55d62-179">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="55d62-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="55d62-180">Generátor EDM &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="55d62-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)
