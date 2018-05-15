---
title: Technologie LINQ to SQL ukázka
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 3cfcaf3de1a22b8bb5505083f127a9888b99dbd8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="4cdba-102">Technologie LINQ to SQL ukázka</span><span class="sxs-lookup"><span data-stu-id="4cdba-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="4cdba-103">Tento příklad znázorňuje postup vytvoření aktivity použití LINQ na entity dotazu SQL z tabulek v databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4cdba-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4cdba-104">Ukázky WCF mohou již být nainstalován na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4cdba-104">The WCF samples may already be installed on your machine.</span></span> <span data-ttu-id="4cdba-105">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4cdba-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="4cdba-106">Pokud tento adresář neexistuje, klikněte na odkaz ke stažení ukázkové v horní části této stránky.</span><span class="sxs-lookup"><span data-stu-id="4cdba-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="4cdba-107">Všimněte si, že tento odkaz se stáhne a nainstaluje všechny [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4cdba-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="4cdba-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4cdba-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="4cdba-109">Podrobnosti o aktivitě pro FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="4cdba-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="4cdba-110">Tato aktivita umožňuje uživatelům dotaz entity z tabulek v databázi pomocí technologie LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="4cdba-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="4cdba-111">Uživatelé aktivity také zadat predikát LINQ ve formě výrazu lambda filtrování výsledků.</span><span class="sxs-lookup"><span data-stu-id="4cdba-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="4cdba-112">Pokud je k dispozici žádné predikátu, je vrácena celou tabulku.</span><span class="sxs-lookup"><span data-stu-id="4cdba-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="4cdba-113">V následující tabulce jsou hodnoty vlastností a vraťte se pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="4cdba-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="4cdba-114">Vlastnost nebo vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="4cdba-114">Property or Return Value</span></span>|<span data-ttu-id="4cdba-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4cdba-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="4cdba-116">`Collection` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4cdba-116">`Collection` property</span></span>|<span data-ttu-id="4cdba-117">Povinnou vlastnost, která určuje zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="4cdba-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="4cdba-118">`Predicate` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4cdba-118">`Predicate` property</span></span>|<span data-ttu-id="4cdba-119">Povinnou vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="4cdba-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="4cdba-120">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4cdba-120">Return Value</span></span>|<span data-ttu-id="4cdba-121">Filtrované kolekce.</span><span class="sxs-lookup"><span data-stu-id="4cdba-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="4cdba-122">Ukázka kódu, který používá vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="4cdba-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="4cdba-123">Následující příklad kódu používá `FindInSqlTable` vlastní aktivity najít všechny řádky v tabulce systému SQL Server s názvem `Employee` kde `Role` sloupec je rovno `SDE`.</span><span class="sxs-lookup"><span data-stu-id="4cdba-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4cdba-124">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="4cdba-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="4cdba-125">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4cdba-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="4cdba-126">Přejděte do složky, která obsahuje tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="4cdba-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="4cdba-127">Spusťte soubor Setup.cmd příkaz.</span><span class="sxs-lookup"><span data-stu-id="4cdba-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4cdba-128">Skript Setup.cmd pokusu o instalaci ukázkové databáze v místním počítači systému SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="4cdba-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="4cdba-129">Pokud chcete nainstalujte ho do jiné instance systému SQL server, upravte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="4cdba-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="4cdba-130">Setup.cmd skript provede následující akce.:</span><span class="sxs-lookup"><span data-stu-id="4cdba-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="4cdba-131">Vytvoří databázi názvem LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="4cdba-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="4cdba-132">Vytvoří tabulku role.</span><span class="sxs-lookup"><span data-stu-id="4cdba-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="4cdba-133">Vytvoří tabulku Zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="4cdba-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="4cdba-134">Vloží do tabulky role 3 záznamy.</span><span class="sxs-lookup"><span data-stu-id="4cdba-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="4cdba-135">Vloží do tabulky Zaměstnanci 12 záznamy.</span><span class="sxs-lookup"><span data-stu-id="4cdba-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="4cdba-136">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="4cdba-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="4cdba-137">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4cdba-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="4cdba-138">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="4cdba-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="4cdba-139">Chcete-li odinstalovat LinqToSql ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="4cdba-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="4cdba-140">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4cdba-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="4cdba-141">Přejděte do složky, která obsahuje tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="4cdba-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="4cdba-142">Spusťte soubor Cleanup.cmd příkaz.</span><span class="sxs-lookup"><span data-stu-id="4cdba-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4cdba-143">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4cdba-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4cdba-144">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4cdba-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4cdba-145">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4cdba-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4cdba-146">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4cdba-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="4cdba-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cdba-147">See Also</span></span>  
 [<span data-ttu-id="4cdba-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4cdba-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="4cdba-149">Začínáme (technologie LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="4cdba-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
