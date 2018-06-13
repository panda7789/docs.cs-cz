---
title: Databáze Access aktivity
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: e9c7627738d3c5313a4f3e6e4451daf78b87839a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520406"
---
# <a name="database-access-activities"></a><span data-ttu-id="f4d37-102">Databáze Access aktivity</span><span class="sxs-lookup"><span data-stu-id="f4d37-102">Database Access Activities</span></span>
<span data-ttu-id="f4d37-103">Databáze access aktivity umožňují přístup k databázi v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f4d37-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="f4d37-104">Tyto aktivity povolit přístup k databázím načtení nebo upravte informace a použití [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4d37-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f4d37-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4d37-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f4d37-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4d37-107">Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f4d37-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4d37-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f4d37-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a><span data-ttu-id="f4d37-109">Databázové aktivity</span><span class="sxs-lookup"><span data-stu-id="f4d37-109">Database Activities</span></span>  
 <span data-ttu-id="f4d37-110">V následujících oddílech jsou upřesněny seznam aktivit, které jsou součástí této ukázky.</span><span class="sxs-lookup"><span data-stu-id="f4d37-110">The following sections detail the list of activities included in this sample.</span></span>  
  
## <a name="dbupdate"></a><span data-ttu-id="f4d37-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="f4d37-111">DbUpdate</span></span>  
 <span data-ttu-id="f4d37-112">Provede dotaz SQL, který vytváří změny v databázi (vložení, aktualizaci, odstranění a jiné změny).</span><span class="sxs-lookup"><span data-stu-id="f4d37-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>  
  
 <span data-ttu-id="f4d37-113">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity> a používá možnosti asynchronní).</span><span class="sxs-lookup"><span data-stu-id="f4d37-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="f4d37-114">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4d37-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="f4d37-115">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="f4d37-116">Po `DbUpdate` je proveden, počet ovlivněných záznamů je vrácený v `AffectedRecords` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4d37-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>  
  
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
  
|<span data-ttu-id="f4d37-117">Argument</span><span class="sxs-lookup"><span data-stu-id="f4d37-117">Argument</span></span>|<span data-ttu-id="f4d37-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d37-118">Description</span></span>|  
|-|-|  
|<span data-ttu-id="f4d37-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f4d37-119">ProviderName</span></span>|<span data-ttu-id="f4d37-120">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d37-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="f4d37-121">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-122">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="f4d37-122">ConnectionString</span></span>|<span data-ttu-id="f4d37-123">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-123">Connection string to connect to the database.</span></span> <span data-ttu-id="f4d37-124">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-124">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="f4d37-125">ConfigName</span></span>|<span data-ttu-id="f4d37-126">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="f4d37-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="f4d37-127">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="f4d37-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="f4d37-128">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="f4d37-128">CommandType</span></span>|<span data-ttu-id="f4d37-129">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="f4d37-130">SQL</span><span class="sxs-lookup"><span data-stu-id="f4d37-130">Sql</span></span>|<span data-ttu-id="f4d37-131">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="f4d37-131">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="f4d37-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d37-132">Parameters</span></span>|<span data-ttu-id="f4d37-133">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="f4d37-133">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="f4d37-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="f4d37-134">AffectedRecords</span></span>|<span data-ttu-id="f4d37-135">Počet záznamů ovlivněný poslední operace.</span><span class="sxs-lookup"><span data-stu-id="f4d37-135">Number of records affected by the last operation.</span></span>|  
  
## <a name="dbqueryscalar"></a><span data-ttu-id="f4d37-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="f4d37-136">DbQueryScalar</span></span>  
 <span data-ttu-id="f4d37-137">Provede dotaz, který načte jednu hodnotu z databáze.</span><span class="sxs-lookup"><span data-stu-id="f4d37-137">Executes a query that retrieves a single value from the database.</span></span>  
  
 <span data-ttu-id="f4d37-138">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a používá možnosti asynchronní).</span><span class="sxs-lookup"><span data-stu-id="f4d37-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="f4d37-139">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4d37-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="f4d37-140">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="f4d37-141">Po `DbQueryScalar` je proveden, skalárních je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="f4d37-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
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
  
|<span data-ttu-id="f4d37-142">Argument</span><span class="sxs-lookup"><span data-stu-id="f4d37-142">Argument</span></span>|<span data-ttu-id="f4d37-143">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d37-143">Description</span></span>|  
|-|-|  
|<span data-ttu-id="f4d37-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f4d37-144">ProviderName</span></span>|<span data-ttu-id="f4d37-145">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d37-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="f4d37-146">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-147">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="f4d37-147">ConnectionString</span></span>|<span data-ttu-id="f4d37-148">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-148">Connection string to connect to the database.</span></span> <span data-ttu-id="f4d37-149">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-149">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="f4d37-150">ConfigName</span></span>|<span data-ttu-id="f4d37-151">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="f4d37-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="f4d37-152">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="f4d37-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="f4d37-153">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="f4d37-153">CommandType</span></span>|<span data-ttu-id="f4d37-154">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="f4d37-155">SQL</span><span class="sxs-lookup"><span data-stu-id="f4d37-155">Sql</span></span>|<span data-ttu-id="f4d37-156">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="f4d37-156">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="f4d37-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d37-157">Parameters</span></span>|<span data-ttu-id="f4d37-158">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="f4d37-158">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="f4d37-159">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4d37-159">Result</span></span>|<span data-ttu-id="f4d37-160">Skalární hodnota, která se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4d37-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="f4d37-161">Tento argument je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="f4d37-161">This argument is of type `TResult`.</span></span>|  
  
## <a name="dbquery"></a><span data-ttu-id="f4d37-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="f4d37-162">DbQuery</span></span>  
 <span data-ttu-id="f4d37-163">Provede dotaz, který načte seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="f4d37-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="f4d37-164">Po provedení dotazu provedení funkce mapování (může být <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="f4d37-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="f4d37-165">Toto mapování funkce získá záznam v `DbDataReader` a mapuje na objekt, který má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="f4d37-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>  
  
 <span data-ttu-id="f4d37-166">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4d37-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="f4d37-167">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="f4d37-168">Výsledky dotazu SQL se načítají pomocí `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="f4d37-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="f4d37-169">Aktivity provádí iteraci `DbDataReader` a mapuje řádky v `DbDataReader` na instanci `TResult`.</span><span class="sxs-lookup"><span data-stu-id="f4d37-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="f4d37-170">Uživatel `DbQuery` musí zadat kód mapování a to můžete provést dvěma způsoby: pomocí <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="f4d37-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="f4d37-171">V prvním případě mapy probíhá v jednom pulse provádění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="f4d37-172">Proto je rychlejší, ale to nelze serializovat do jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="f4d37-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="f4d37-173">V případě poslední mapy probíhá v několika impulsů.</span><span class="sxs-lookup"><span data-stu-id="f4d37-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="f4d37-174">Proto může být pomalejší, ale může být serializován do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="f4d37-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>  
  
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
  
|<span data-ttu-id="f4d37-175">Argument</span><span class="sxs-lookup"><span data-stu-id="f4d37-175">Argument</span></span>|<span data-ttu-id="f4d37-176">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d37-176">Description</span></span>|  
|-|-|  
|<span data-ttu-id="f4d37-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f4d37-177">ProviderName</span></span>|<span data-ttu-id="f4d37-178">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d37-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="f4d37-179">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-180">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="f4d37-180">ConnectionString</span></span>|<span data-ttu-id="f4d37-181">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-181">Connection string to connect to the database.</span></span> <span data-ttu-id="f4d37-182">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-182">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="f4d37-183">ConfigName</span></span>|<span data-ttu-id="f4d37-184">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="f4d37-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="f4d37-185">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="f4d37-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="f4d37-186">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="f4d37-186">CommandType</span></span>|<span data-ttu-id="f4d37-187">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="f4d37-188">SQL</span><span class="sxs-lookup"><span data-stu-id="f4d37-188">Sql</span></span>|<span data-ttu-id="f4d37-189">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="f4d37-189">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="f4d37-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d37-190">Parameters</span></span>|<span data-ttu-id="f4d37-191">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="f4d37-191">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="f4d37-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="f4d37-192">Mapper</span></span>|<span data-ttu-id="f4d37-193">Mapování funkce (<xref:System.Func%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="f4d37-194">V takovém případě mapování se provádí v jednom pulse spuštění, ale nemůže být vytvořené deklarativně pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="f4d37-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|  
|<span data-ttu-id="f4d37-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="f4d37-195">MapperFunc</span></span>|<span data-ttu-id="f4d37-196">Mapování funkce (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="f4d37-197">V takovém případě mapování se provádí v několika impulsů provádění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="f4d37-198">Tato funkce může serializovat do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="f4d37-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|  
|<span data-ttu-id="f4d37-199">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4d37-199">Result</span></span>|<span data-ttu-id="f4d37-200">Po provedení dotazu a provádění mapování funkce pro každý záznam v získat seznam objektů `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="f4d37-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|  
  
## <a name="dbquerydataset"></a><span data-ttu-id="f4d37-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="f4d37-201">DbQueryDataSet</span></span>  
 <span data-ttu-id="f4d37-202">Provede dotaz, který vrátí <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f4d37-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f4d37-203">Tato třída provádí svou práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="f4d37-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="f4d37-204">Je odvozena z <xref:System.Activities.AsyncCodeActivity> < `TResult`> a používá možnosti asynchronní.</span><span class="sxs-lookup"><span data-stu-id="f4d37-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>  
  
 <span data-ttu-id="f4d37-205">Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4d37-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="f4d37-206">Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4d37-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="f4d37-207">Po `DbQueryDataSet` se spustí `DataSet` je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="f4d37-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
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
  
|<span data-ttu-id="f4d37-208">Argument</span><span class="sxs-lookup"><span data-stu-id="f4d37-208">Argument</span></span>|<span data-ttu-id="f4d37-209">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d37-209">Description</span></span>|  
|-|-|  
|<span data-ttu-id="f4d37-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f4d37-210">ProviderName</span></span>|<span data-ttu-id="f4d37-211">Neutrální název zprostředkovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f4d37-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="f4d37-212">Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-213">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="f4d37-213">ConnectionString</span></span>|<span data-ttu-id="f4d37-214">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-214">Connection string to connect to the database.</span></span> <span data-ttu-id="f4d37-215">Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="f4d37-215">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="f4d37-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="f4d37-216">ConfigName</span></span>|<span data-ttu-id="f4d37-217">Název oddílu konfiguračního souboru se uloží informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="f4d37-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="f4d37-218">Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="f4d37-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="f4d37-219">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="f4d37-219">CommandType</span></span>|<span data-ttu-id="f4d37-220">Typ <xref:System.Data.Common.DbCommand> spouštění.</span><span class="sxs-lookup"><span data-stu-id="f4d37-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="f4d37-221">SQL</span><span class="sxs-lookup"><span data-stu-id="f4d37-221">Sql</span></span>|<span data-ttu-id="f4d37-222">Příkaz SQL, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="f4d37-222">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="f4d37-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d37-223">Parameters</span></span>|<span data-ttu-id="f4d37-224">Kolekce parametrů příkazu jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="f4d37-224">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="f4d37-225">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4d37-225">Result</span></span>|<span data-ttu-id="f4d37-226"><xref:System.Data.DataSet> která se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4d37-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|  
  
## <a name="configuring-connection-information"></a><span data-ttu-id="f4d37-227">Konfigurace informací o připojení</span><span class="sxs-lookup"><span data-stu-id="f4d37-227">Configuring Connection Information</span></span>  
 <span data-ttu-id="f4d37-228">Všechny DbActivities sdílejí stejnou konfigurační parametry.</span><span class="sxs-lookup"><span data-stu-id="f4d37-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="f4d37-229">Mohou být konfigurovány dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="f4d37-229">They can be configured in two ways:</span></span>  
  
-   <span data-ttu-id="f4d37-230">`ConnectionString + InvariantName`: Nastavte zprostředkovatele ADO.NET invariantní název a připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="f4d37-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>  
  
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
  
-   <span data-ttu-id="f4d37-231">`ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="f4d37-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   <span data-ttu-id="f4d37-232">V rámci aktivity:</span><span class="sxs-lookup"><span data-stu-id="f4d37-232">In the activity:</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a><span data-ttu-id="f4d37-233">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="f4d37-233">Running this sample</span></span>  
  
### <a name="setup-instructions"></a><span data-ttu-id="f4d37-234">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="f4d37-234">Setup instructions</span></span>  
 <span data-ttu-id="f4d37-235">Tato ukázka používá databázi.</span><span class="sxs-lookup"><span data-stu-id="f4d37-235">This sample uses a database.</span></span> <span data-ttu-id="f4d37-236">Nastavení a zatížení skript (Setup.cmd) k dispozici vzorku.</span><span class="sxs-lookup"><span data-stu-id="f4d37-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="f4d37-237">Je třeba spustit tento soubor pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f4d37-237">You must execute that file using the command prompt.</span></span>  
  
 <span data-ttu-id="f4d37-238">Skript Setup.cmd vyvolá CreateDb.sql souboru skriptu, který obsahuje příkazy SQL, které postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f4d37-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>  
  
-   <span data-ttu-id="f4d37-239">Vytvoří databázi názvem DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="f4d37-239">Creates a database called DbActivitiesSample.</span></span>  
  
-   <span data-ttu-id="f4d37-240">Vytvoří tabulku role.</span><span class="sxs-lookup"><span data-stu-id="f4d37-240">Creates the Roles table.</span></span>  
  
-   <span data-ttu-id="f4d37-241">Vytvoří tabulku Zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="f4d37-241">Creates Employees table.</span></span>  
  
-   <span data-ttu-id="f4d37-242">Vloží do tabulky role tři záznamy.</span><span class="sxs-lookup"><span data-stu-id="f4d37-242">Inserts three records into the Roles table.</span></span>  
  
-   <span data-ttu-id="f4d37-243">Vloží do tabulky Zaměstnanci dvanáct záznamy.</span><span class="sxs-lookup"><span data-stu-id="f4d37-243">Inserts twelve records into the Employees table.</span></span>  
  
##### <a name="to-run-setupcmd"></a><span data-ttu-id="f4d37-244">Ke spuštění Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="f4d37-244">To run Setup.cmd</span></span>  
  
1.  <span data-ttu-id="f4d37-245">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="f4d37-245">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="f4d37-246">Přejděte do složky DbActivities ukázka.</span><span class="sxs-lookup"><span data-stu-id="f4d37-246">Go to the DbActivities sample folder.</span></span>  
  
3.  <span data-ttu-id="f4d37-247">Zadejte "setup.cmd" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f4d37-247">Type "setup.cmd" and press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4d37-248">Setup.cmd se pokusí ukázku nainstalujete v instanci SqlExpress místního počítače.</span><span class="sxs-lookup"><span data-stu-id="f4d37-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="f4d37-249">Pokud chcete nainstalujte ho do jiné instance systému SQL server, upravte Setup.cmd s novým názvem instance.</span><span class="sxs-lookup"><span data-stu-id="f4d37-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>  
  
##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="f4d37-250">Chcete-li odinstalovat ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="f4d37-250">To uninstall the sample database</span></span>  
  
1.  <span data-ttu-id="f4d37-251">Spusťte Cleanup.cmd z ukázkové složky v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="f4d37-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>  
  
##### <a name="to-run-the-sample"></a><span data-ttu-id="f4d37-252">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f4d37-252">To run the sample</span></span>  
  
1.  <span data-ttu-id="f4d37-253">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4d37-253">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span></span>  
  
2.  <span data-ttu-id="f4d37-254">Chcete-li zkompilovat řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f4d37-254">To compile the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f4d37-255">Chcete-li spustit ukázku bez ladění, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f4d37-255">To run the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4d37-256">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f4d37-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4d37-257">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f4d37-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4d37-258">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f4d37-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4d37-259">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f4d37-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
