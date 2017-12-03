---
title: "Databáze Access aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d95eece0a02433a78a400f1cfd9ab06ca716668e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="database-access-activities"></a><span data-ttu-id="c5a09-102">Databáze Access aktivity</span><span class="sxs-lookup"><span data-stu-id="c5a09-102">Database Access Activities</span></span>
<span data-ttu-id="c5a09-103">Databáze access aktivity umožňují přístup k databázi v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c5a09-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="c5a09-104">Tyto aktivity povolit přístup k databázím načtení nebo upravte informace a použití [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5a09-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c5a09-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5a09-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c5a09-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5a09-107">Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c5a09-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5a09-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c5a09-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a><span data-ttu-id="c5a09-109">Databázové aktivity</span><span class="sxs-lookup"><span data-stu-id="c5a09-109">Database Activities</span></span>  
 <span data-ttu-id="c5a09-110">V následujících oddílech jsou upřesněny seznam aktivit, které jsou součástí této ukázky.</span><span class="sxs-lookup"><span data-stu-id="c5a09-110">The following sections detail the list of activities included in this sample.</span></span>  
  
## <a name="dbupdate"></a><span data-ttu-id="c5a09-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="c5a09-111">DbUpdate</span></span>  
 <span data-ttu-id="c5a09-112">Provede dotaz SQL, který vytváří změny v databázi (vložení, aktualizaci, odstranění a jiné změny).</span><span class="sxs-lookup"><span data-stu-id="c5a09-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>  
  
 <span data-ttu-id="c5a09-113">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity> a používá možnosti asynchronní).</span><span class="sxs-lookup"><span data-stu-id="c5a09-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="c5a09-114">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5a09-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="c5a09-115">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="c5a09-116">Po `DbUpdate` je proveden, počet ovlivněných záznamů je vrácený v `AffectedRecords` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5a09-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
|<span data-ttu-id="c5a09-117">Argument</span><span class="sxs-lookup"><span data-stu-id="c5a09-117">Argument</span></span>|<span data-ttu-id="c5a09-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c5a09-118">Description</span></span>|  
|-|-|  
|<span data-ttu-id="c5a09-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c5a09-119">ProviderName</span></span>|<span data-ttu-id="c5a09-120">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c5a09-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="c5a09-121">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-122">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="c5a09-122">ConnectionString</span></span>|<span data-ttu-id="c5a09-123">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-123">Connection string to connect to the database.</span></span> <span data-ttu-id="c5a09-124">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-124">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="c5a09-125">ConfigName</span></span>|<span data-ttu-id="c5a09-126">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="c5a09-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="c5a09-127">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="c5a09-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="c5a09-128">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="c5a09-128">CommandType</span></span>|<span data-ttu-id="c5a09-129">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="c5a09-130">SQL</span><span class="sxs-lookup"><span data-stu-id="c5a09-130">Sql</span></span>|<span data-ttu-id="c5a09-131">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="c5a09-131">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="c5a09-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a09-132">Parameters</span></span>|<span data-ttu-id="c5a09-133">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c5a09-133">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="c5a09-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="c5a09-134">AffectedRecords</span></span>|<span data-ttu-id="c5a09-135">Počet záznamů ovlivněný poslední operace.</span><span class="sxs-lookup"><span data-stu-id="c5a09-135">Number of records affected by the last operation.</span></span>|  
  
## <a name="dbqueryscalar"></a><span data-ttu-id="c5a09-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="c5a09-136">DbQueryScalar</span></span>  
 <span data-ttu-id="c5a09-137">Provede dotaz, který načte jednu hodnotu z databáze.</span><span class="sxs-lookup"><span data-stu-id="c5a09-137">Executes a query that retrieves a single value from the database.</span></span>  
  
 <span data-ttu-id="c5a09-138">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a používá možnosti asynchronní).</span><span class="sxs-lookup"><span data-stu-id="c5a09-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="c5a09-139">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5a09-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="c5a09-140">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="c5a09-141">Po `DbQueryScalar` je proveden, skalárních je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="c5a09-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
```  
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|<span data-ttu-id="c5a09-142">Argument</span><span class="sxs-lookup"><span data-stu-id="c5a09-142">Argument</span></span>|<span data-ttu-id="c5a09-143">Popis</span><span class="sxs-lookup"><span data-stu-id="c5a09-143">Description</span></span>|  
|-|-|  
|<span data-ttu-id="c5a09-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c5a09-144">ProviderName</span></span>|<span data-ttu-id="c5a09-145">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c5a09-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="c5a09-146">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-147">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="c5a09-147">ConnectionString</span></span>|<span data-ttu-id="c5a09-148">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-148">Connection string to connect to the database.</span></span> <span data-ttu-id="c5a09-149">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-149">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="c5a09-150">ConfigName</span></span>|<span data-ttu-id="c5a09-151">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="c5a09-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="c5a09-152">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="c5a09-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="c5a09-153">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="c5a09-153">CommandType</span></span>|<span data-ttu-id="c5a09-154">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="c5a09-155">SQL</span><span class="sxs-lookup"><span data-stu-id="c5a09-155">Sql</span></span>|<span data-ttu-id="c5a09-156">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="c5a09-156">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="c5a09-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a09-157">Parameters</span></span>|<span data-ttu-id="c5a09-158">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c5a09-158">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="c5a09-159">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c5a09-159">Result</span></span>|<span data-ttu-id="c5a09-160">Skalární hodnota, která se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5a09-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="c5a09-161">Tento argument je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="c5a09-161">This argument is of type `TResult`.</span></span>|  
  
## <a name="dbquery"></a><span data-ttu-id="c5a09-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="c5a09-162">DbQuery</span></span>  
 <span data-ttu-id="c5a09-163">Provede dotaz, který načte seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="c5a09-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="c5a09-164">Po provedení dotazu provedení funkce mapování (může být <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="c5a09-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="c5a09-165">Toto mapování funkce získá záznam v `DbDataReader` a mapuje na objekt, který má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="c5a09-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>  
  
 <span data-ttu-id="c5a09-166">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5a09-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="c5a09-167">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="c5a09-168">Výsledky dotazu SQL se načítají pomocí `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="c5a09-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="c5a09-169">Aktivity provádí iteraci `DbDataReader` a mapuje řádky v `DbDataReader` na instanci `TResult`.</span><span class="sxs-lookup"><span data-stu-id="c5a09-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="c5a09-170">Uživatel `DbQuery` musí zadat kód mapování a to můžete provést dvěma způsoby: pomocí <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="c5a09-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="c5a09-171">V prvním případě mapy probíhá v jednom pulse provádění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="c5a09-172">Proto je rychlejší, ale to nelze serializovat do jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="c5a09-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="c5a09-173">V případě poslední mapy probíhá v několika impulsů.</span><span class="sxs-lookup"><span data-stu-id="c5a09-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="c5a09-174">Proto může být pomalejší, ale může být serializován do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="c5a09-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>  
  
```  
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [OverloadGroup("DirectMapping")]  
    [DefaultValue(null)]  
    public Func<DbDataReader, TResult> Mapper { get; set; }  
  
    [OverloadGroup("MultiplePulseMapping")]  
    [DefaultValue(null)]  
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }  
}  
```  
  
|<span data-ttu-id="c5a09-175">Argument</span><span class="sxs-lookup"><span data-stu-id="c5a09-175">Argument</span></span>|<span data-ttu-id="c5a09-176">Popis</span><span class="sxs-lookup"><span data-stu-id="c5a09-176">Description</span></span>|  
|-|-|  
|<span data-ttu-id="c5a09-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c5a09-177">ProviderName</span></span>|<span data-ttu-id="c5a09-178">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c5a09-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="c5a09-179">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-180">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="c5a09-180">ConnectionString</span></span>|<span data-ttu-id="c5a09-181">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-181">Connection string to connect to the database.</span></span> <span data-ttu-id="c5a09-182">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-182">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="c5a09-183">ConfigName</span></span>|<span data-ttu-id="c5a09-184">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="c5a09-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="c5a09-185">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="c5a09-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="c5a09-186">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="c5a09-186">CommandType</span></span>|<span data-ttu-id="c5a09-187">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="c5a09-188">SQL</span><span class="sxs-lookup"><span data-stu-id="c5a09-188">Sql</span></span>|<span data-ttu-id="c5a09-189">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="c5a09-189">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="c5a09-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a09-190">Parameters</span></span>|<span data-ttu-id="c5a09-191">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c5a09-191">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="c5a09-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="c5a09-192">Mapper</span></span>|<span data-ttu-id="c5a09-193">Mapování funkce (<xref:System.Func%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="c5a09-194">V takovém případě mapování se provádí v jednom pulse spuštění, ale nemůže být vytvořené deklarativně pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="c5a09-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|  
|<span data-ttu-id="c5a09-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="c5a09-195">MapperFunc</span></span>|<span data-ttu-id="c5a09-196">Mapování funkce (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="c5a09-197">V takovém případě mapování se provádí v několika impulsů provádění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="c5a09-198">Tato funkce může serializovat do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="c5a09-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|  
|<span data-ttu-id="c5a09-199">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c5a09-199">Result</span></span>|<span data-ttu-id="c5a09-200">Po provedení dotazu a provádění mapování funkce pro každý záznam v získat seznam objektů `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="c5a09-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|  
  
## <a name="dbquerydataset"></a><span data-ttu-id="c5a09-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="c5a09-201">DbQueryDataSet</span></span>  
 <span data-ttu-id="c5a09-202">Provede dotaz, který vrátí <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c5a09-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c5a09-203">Tato třída provádí svou práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c5a09-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="c5a09-204">Je odvozena z <xref:System.Activities.AsyncCodeActivity> < `TResult`> a používá možnosti asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c5a09-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>  
  
 <span data-ttu-id="c5a09-205">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5a09-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="c5a09-206">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c5a09-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="c5a09-207">Po `DbQueryDataSet` se spustí `DataSet` je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="c5a09-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
```  
public class DbQueryDataSet : AsyncCodeActivity<DataSet>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|<span data-ttu-id="c5a09-208">Argument</span><span class="sxs-lookup"><span data-stu-id="c5a09-208">Argument</span></span>|<span data-ttu-id="c5a09-209">Popis</span><span class="sxs-lookup"><span data-stu-id="c5a09-209">Description</span></span>|  
|-|-|  
|<span data-ttu-id="c5a09-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="c5a09-210">ProviderName</span></span>|<span data-ttu-id="c5a09-211">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c5a09-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="c5a09-212">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-213">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="c5a09-213">ConnectionString</span></span>|<span data-ttu-id="c5a09-214">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-214">Connection string to connect to the database.</span></span> <span data-ttu-id="c5a09-215">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5a09-215">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="c5a09-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="c5a09-216">ConfigName</span></span>|<span data-ttu-id="c5a09-217">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="c5a09-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="c5a09-218">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="c5a09-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="c5a09-219">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="c5a09-219">CommandType</span></span>|<span data-ttu-id="c5a09-220">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="c5a09-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="c5a09-221">SQL</span><span class="sxs-lookup"><span data-stu-id="c5a09-221">Sql</span></span>|<span data-ttu-id="c5a09-222">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="c5a09-222">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="c5a09-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a09-223">Parameters</span></span>|<span data-ttu-id="c5a09-224">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="c5a09-224">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="c5a09-225">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c5a09-225">Result</span></span>|<span data-ttu-id="c5a09-226"><xref:System.Data.DataSet>která se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5a09-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|  
  
## <a name="configuring-connection-information"></a><span data-ttu-id="c5a09-227">Konfigurace informací o připojení</span><span class="sxs-lookup"><span data-stu-id="c5a09-227">Configuring Connection Information</span></span>  
 <span data-ttu-id="c5a09-228">Všechny DbActivities sdílejí stejnou konfigurační parametry.</span><span class="sxs-lookup"><span data-stu-id="c5a09-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="c5a09-229">Mohou být konfigurovány dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="c5a09-229">They can be configured in two ways:</span></span>  
  
-   <span data-ttu-id="c5a09-230">`ConnectionString + InvariantName`: Nastavte zprostředkovatele ADO.NET invariantní název a připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="c5a09-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<DateTime>()  
    {  
        ProviderName = "System.Data.SqlClient",  
        ConnectionString = @"Data Source=.\SQLExpress;  
                             Initial Catalog=DbActivitiesSample;  
                             Integrated Security=True",  
        Sql = "SELECT GetDate()"  
    };  
    ```  
  
-   <span data-ttu-id="c5a09-231">`ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="c5a09-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   <span data-ttu-id="c5a09-232">V rámci aktivity:</span><span class="sxs-lookup"><span data-stu-id="c5a09-232">In the activity:</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a><span data-ttu-id="c5a09-233">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="c5a09-233">Running this sample</span></span>  
  
### <a name="setup-instructions"></a><span data-ttu-id="c5a09-234">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="c5a09-234">Setup instructions</span></span>  
 <span data-ttu-id="c5a09-235">Tato ukázka používá databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a09-235">This sample uses a database.</span></span> <span data-ttu-id="c5a09-236">Nastavení a zatížení skript (Setup.cmd) k dispozici vzorku.</span><span class="sxs-lookup"><span data-stu-id="c5a09-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="c5a09-237">Je třeba spustit tento soubor pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c5a09-237">You must execute that file using the command prompt.</span></span>  
  
 <span data-ttu-id="c5a09-238">Skript Setup.cmd vyvolá CreateDb.sql souboru skriptu, který obsahuje příkazy SQL, které postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="c5a09-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>  
  
-   <span data-ttu-id="c5a09-239">Vytvoří databázi názvem DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="c5a09-239">Creates a database called DbActivitiesSample.</span></span>  
  
-   <span data-ttu-id="c5a09-240">Vytvoří tabulku role.</span><span class="sxs-lookup"><span data-stu-id="c5a09-240">Creates the Roles table.</span></span>  
  
-   <span data-ttu-id="c5a09-241">Vytvoří tabulku Zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="c5a09-241">Creates Employees table.</span></span>  
  
-   <span data-ttu-id="c5a09-242">Vloží do tabulky role tři záznamy.</span><span class="sxs-lookup"><span data-stu-id="c5a09-242">Inserts three records into the Roles table.</span></span>  
  
-   <span data-ttu-id="c5a09-243">Vloží do tabulky Zaměstnanci dvanáct záznamy.</span><span class="sxs-lookup"><span data-stu-id="c5a09-243">Inserts twelve records into the Employees table.</span></span>  
  
##### <a name="to-run-setupcmd"></a><span data-ttu-id="c5a09-244">Ke spuštění Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="c5a09-244">To run Setup.cmd</span></span>  
  
1.  <span data-ttu-id="c5a09-245">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="c5a09-245">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="c5a09-246">Přejděte do složky DbActivities ukázka.</span><span class="sxs-lookup"><span data-stu-id="c5a09-246">Go to the DbActivities sample folder.</span></span>  
  
3.  <span data-ttu-id="c5a09-247">Zadejte "setup.cmd" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c5a09-247">Type "setup.cmd" and press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5a09-248">Setup.cmd se pokusí ukázku nainstalujete v instanci SqlExpress místního počítače.</span><span class="sxs-lookup"><span data-stu-id="c5a09-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="c5a09-249">Pokud chcete nainstalujte ho do jiné instance systému SQL server, upravte Setup.cmd s novým názvem instance.</span><span class="sxs-lookup"><span data-stu-id="c5a09-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>  
  
##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="c5a09-250">Chcete-li odinstalovat ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="c5a09-250">To uninstall the sample database</span></span>  
  
1.  <span data-ttu-id="c5a09-251">Spusťte Cleanup.cmd z ukázkové složky v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c5a09-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>  
  
##### <a name="to-run-the-sample"></a><span data-ttu-id="c5a09-252">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c5a09-252">To run the sample</span></span>  
  
1.  <span data-ttu-id="c5a09-253">Otevřete řešení v[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a09-253">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span></span>  
  
2.  <span data-ttu-id="c5a09-254">Chcete-li zkompilovat řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="c5a09-254">To compile the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c5a09-255">Chcete-li spustit ukázku bez ladění, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="c5a09-255">To run the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5a09-256">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c5a09-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5a09-257">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c5a09-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5a09-258">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c5a09-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5a09-259">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c5a09-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
