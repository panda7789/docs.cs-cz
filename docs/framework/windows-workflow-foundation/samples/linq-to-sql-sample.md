---
title: Ukázka LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515365"
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="b1b75-102">Ukázka LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b1b75-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="b1b75-103">Tento příklad ukazuje, jak vytvořit aktivitu použití LINQ na SQL dotazu entity z tabulky v databázích systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b1b75-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1b75-104">Ukázky WCF může již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b1b75-104">The WCF samples may already be installed on your machine.</span></span> <span data-ttu-id="b1b75-105">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b1b75-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="b1b75-106">Pokud tento adresář neexistuje, klikněte na odkaz ke stažení vzorku v horní části této stránky.</span><span class="sxs-lookup"><span data-stu-id="b1b75-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="b1b75-107">Všimněte si, že tento odkaz stáhne a nainstaluje všechny komponenty nástroje [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b1b75-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="b1b75-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b1b75-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="b1b75-109">Podrobnosti o aktivitě pro FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="b1b75-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="b1b75-110">Tato aktivita umožňuje uživatelům na dotazu entity z tabulky v databázi pomocí LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="b1b75-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="b1b75-111">Aktivity uživatelů můžete také zadat predikát LINQ ve formě lambda výraz k filtrování výsledků.</span><span class="sxs-lookup"><span data-stu-id="b1b75-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="b1b75-112">Pokud je k dispozici žádné predikátu, je vrácena celá tabulka.</span><span class="sxs-lookup"><span data-stu-id="b1b75-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="b1b75-113">Následující tabulka uvádí vlastnosti a návratové hodnoty pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="b1b75-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="b1b75-114">Vlastnost nebo návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1b75-114">Property or Return Value</span></span>|<span data-ttu-id="b1b75-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b1b75-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b1b75-116">`Collection` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b1b75-116">`Collection` property</span></span>|<span data-ttu-id="b1b75-117">Požadovaná vlastnost, která určuje zdrojovou kolekci.</span><span class="sxs-lookup"><span data-stu-id="b1b75-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="b1b75-118">`Predicate` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b1b75-118">`Predicate` property</span></span>|<span data-ttu-id="b1b75-119">Požadovaná vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="b1b75-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="b1b75-120">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1b75-120">Return Value</span></span>|<span data-ttu-id="b1b75-121">Filtrované kolekce.</span><span class="sxs-lookup"><span data-stu-id="b1b75-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="b1b75-122">Vzorový kód, který používá vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="b1b75-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="b1b75-123">Následující příklad kódu používá `FindInSqlTable` vlastní aktivity se najít všechny řádky v tabulce SQL serveru s názvem `Employee` kde `Role` sloupce je rovna `SDE`.</span><span class="sxs-lookup"><span data-stu-id="b1b75-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b1b75-124">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="b1b75-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="b1b75-125">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="b1b75-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b1b75-126">Přejděte do složky obsahující tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="b1b75-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="b1b75-127">Spuštění souboru příkazů Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="b1b75-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1b75-128">Skriptu Setup.cmd pokusu o instalaci ukázkové databáze v místním počítači systému SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="b1b75-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="b1b75-129">Pokud chcete nainstalovat v jiné instance systému SQL server, upravte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="b1b75-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="b1b75-130">Provádí následující akce skriptu Setup.cmd.:</span><span class="sxs-lookup"><span data-stu-id="b1b75-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="b1b75-131">Vytvoří databázi s názvem LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="b1b75-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="b1b75-132">Vytvoří tabulku role.</span><span class="sxs-lookup"><span data-stu-id="b1b75-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="b1b75-133">Vytvoří tabulku Zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="b1b75-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="b1b75-134">Vloží do tabulky. role 3 záznamy.</span><span class="sxs-lookup"><span data-stu-id="b1b75-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="b1b75-135">Vloží do tabulky Employees 12 záznamy.</span><span class="sxs-lookup"><span data-stu-id="b1b75-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="b1b75-136">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="b1b75-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="b1b75-137">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b1b75-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="b1b75-138">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="b1b75-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="b1b75-139">Chcete-li odinstalovat LinqToSql ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="b1b75-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="b1b75-140">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="b1b75-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b1b75-141">Přejděte do složky obsahující tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="b1b75-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="b1b75-142">Spusťte soubor Cleanup.cmd příkazu.</span><span class="sxs-lookup"><span data-stu-id="b1b75-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1b75-143">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b1b75-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1b75-144">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b1b75-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1b75-145">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b1b75-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1b75-146">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b1b75-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="b1b75-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1b75-147">See Also</span></span>  
 [<span data-ttu-id="b1b75-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b1b75-148">LINQ to SQL</span></span>](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="b1b75-149">Začínáme (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="b1b75-149">Getting Started (LINQ to SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150377)
