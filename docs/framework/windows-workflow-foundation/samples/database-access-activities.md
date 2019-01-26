---
title: Aktivity přístupu k databázi
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: db79f2d7605a71997ede134152b12395b9193f95
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066087"
---
# <a name="database-access-activities"></a><span data-ttu-id="81726-102">Aktivity přístupu k databázi</span><span class="sxs-lookup"><span data-stu-id="81726-102">Database Access Activities</span></span>
<span data-ttu-id="81726-103">Aktivity přístupu k databázi umožňují přístup k databázi v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="81726-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="81726-104">Tyto aktivity umožňují přístup k databázím nebo upravte informace a použití [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81726-105">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="81726-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81726-106">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="81726-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="81726-107">Pokud tento adresář neexistuje, přejděte na stránku (stahování) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="81726-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81726-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="81726-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="81726-109">Databázové aktivity</span><span class="sxs-lookup"><span data-stu-id="81726-109">Database Activities</span></span>
 <span data-ttu-id="81726-110">Seznam aktivit, které jsou zahrnuté v této ukázce jsou podrobně popsané v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="81726-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="81726-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="81726-111">DbUpdate</span></span>
 <span data-ttu-id="81726-112">Provede dotaz SQL, který vytváří změny v databázi (insert, update, delete a jiné úpravy).</span><span class="sxs-lookup"><span data-stu-id="81726-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="81726-113">Tato třída provádí svou práci asynchronně (se odvozuje od <xref:System.Activities.AsyncCodeActivity> a používá jeho asynchronní funkce).</span><span class="sxs-lookup"><span data-stu-id="81726-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="81726-114">Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81726-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="81726-115">Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="81726-116">Po `DbUpdate` se provedl a počet ovlivněných záznamů, které se vrátí v `AffectedRecords` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81726-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

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

|<span data-ttu-id="81726-117">Argument</span><span class="sxs-lookup"><span data-stu-id="81726-117">Argument</span></span>|<span data-ttu-id="81726-118">Popis</span><span class="sxs-lookup"><span data-stu-id="81726-118">Description</span></span>|
|-|-|
|<span data-ttu-id="81726-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="81726-119">ProviderName</span></span>|<span data-ttu-id="81726-120">Výchozí název zprostředkovatele rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="81726-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="81726-121">Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="81726-122">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="81726-122">ConnectionString</span></span>|<span data-ttu-id="81726-123">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-123">Connection string to connect to the database.</span></span> <span data-ttu-id="81726-124">Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="81726-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="81726-125">ConfigName</span></span>|<span data-ttu-id="81726-126">Název oddílu konfiguračního souboru, kde se ukládají informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="81726-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="81726-127">Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="81726-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="81726-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="81726-128">CommandType</span></span>|<span data-ttu-id="81726-129">Typ <xref:System.Data.Common.DbCommand> má být proveden.</span><span class="sxs-lookup"><span data-stu-id="81726-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="81726-130">SQL</span><span class="sxs-lookup"><span data-stu-id="81726-130">Sql</span></span>|<span data-ttu-id="81726-131">Příkaz SQL, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="81726-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="81726-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="81726-132">Parameters</span></span>|<span data-ttu-id="81726-133">Kolekce parametrů bude příkaz jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="81726-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="81726-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="81726-134">AffectedRecords</span></span>|<span data-ttu-id="81726-135">Počet záznamů ovlivněný podle poslední operaci.</span><span class="sxs-lookup"><span data-stu-id="81726-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="81726-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="81726-136">DbQueryScalar</span></span>
 <span data-ttu-id="81726-137">Provede dotaz, který načte hodnotu single z databáze.</span><span class="sxs-lookup"><span data-stu-id="81726-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="81726-138">Tato třída provádí svou práci asynchronně (se odvozuje od <xref:System.Activities.AsyncCodeActivity%601> a používá jeho asynchronní funkce).</span><span class="sxs-lookup"><span data-stu-id="81726-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="81726-139">Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81726-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="81726-140">Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="81726-141">Po `DbQueryScalar` se provedl a vytvořil skalárních se vrátí v `Result out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="81726-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="81726-142">Argument</span><span class="sxs-lookup"><span data-stu-id="81726-142">Argument</span></span>|<span data-ttu-id="81726-143">Popis</span><span class="sxs-lookup"><span data-stu-id="81726-143">Description</span></span>|
|-|-|
|<span data-ttu-id="81726-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="81726-144">ProviderName</span></span>|<span data-ttu-id="81726-145">Výchozí název zprostředkovatele rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="81726-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="81726-146">Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="81726-147">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="81726-147">ConnectionString</span></span>|<span data-ttu-id="81726-148">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-148">Connection string to connect to the database.</span></span> <span data-ttu-id="81726-149">Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="81726-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="81726-150">ConfigName</span></span>|<span data-ttu-id="81726-151">Název oddílu konfiguračního souboru, kde se ukládají informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="81726-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="81726-152">Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="81726-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="81726-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="81726-153">CommandType</span></span>|<span data-ttu-id="81726-154">Typ <xref:System.Data.Common.DbCommand> má být proveden.</span><span class="sxs-lookup"><span data-stu-id="81726-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="81726-155">SQL</span><span class="sxs-lookup"><span data-stu-id="81726-155">Sql</span></span>|<span data-ttu-id="81726-156">Příkaz SQL, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="81726-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="81726-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="81726-157">Parameters</span></span>|<span data-ttu-id="81726-158">Kolekce parametrů bude příkaz jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="81726-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="81726-159">Výsledek</span><span class="sxs-lookup"><span data-stu-id="81726-159">Result</span></span>|<span data-ttu-id="81726-160">Skalární hodnota, která se získá po spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="81726-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="81726-161">Tento argument je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="81726-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="81726-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="81726-162">DbQuery</span></span>
 <span data-ttu-id="81726-163">Provede dotaz, který načte seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="81726-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="81726-164">Po spuštění dotazu mapování funkce se provede (může být <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="81726-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="81726-165">Toto mapování funkce získá v záznamu `DbDataReader` a mapuje na objekt, který má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="81726-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="81726-166">Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81726-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="81726-167">Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="81726-168">Výsledky dotazu SQL se načítají pomocí `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="81726-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="81726-169">Aktivita Iteruje přes `DbDataReader` a řádky v tabulce se mapuje `DbDataReader` do instance `TResult`.</span><span class="sxs-lookup"><span data-stu-id="81726-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="81726-170">Uživatel `DbQuery` poskytnout mapování kódu, což lze provést dvěma způsoby: pomocí <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="81726-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="81726-171">V prvním případě mapy se provádí v jedné pulse provádění.</span><span class="sxs-lookup"><span data-stu-id="81726-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="81726-172">Proto je rychlejší, ale to nejde serializovat do XAML.</span><span class="sxs-lookup"><span data-stu-id="81726-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="81726-173">V posledním případě mapy probíhá v několika počtu impulsů.</span><span class="sxs-lookup"><span data-stu-id="81726-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="81726-174">Proto může být pomalejší, ale může být serializován XAML a vytvořené pomocí deklarace (jakékoli existující aktivitu mohl podílet na mapování).</span><span class="sxs-lookup"><span data-stu-id="81726-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

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

|<span data-ttu-id="81726-175">Argument</span><span class="sxs-lookup"><span data-stu-id="81726-175">Argument</span></span>|<span data-ttu-id="81726-176">Popis</span><span class="sxs-lookup"><span data-stu-id="81726-176">Description</span></span>|
|-|-|
|<span data-ttu-id="81726-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="81726-177">ProviderName</span></span>|<span data-ttu-id="81726-178">Výchozí název zprostředkovatele rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="81726-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="81726-179">Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="81726-180">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="81726-180">ConnectionString</span></span>|<span data-ttu-id="81726-181">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-181">Connection string to connect to the database.</span></span> <span data-ttu-id="81726-182">Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="81726-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="81726-183">ConfigName</span></span>|<span data-ttu-id="81726-184">Název oddílu konfiguračního souboru, kde se ukládají informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="81726-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="81726-185">Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="81726-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="81726-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="81726-186">CommandType</span></span>|<span data-ttu-id="81726-187">Typ <xref:System.Data.Common.DbCommand> má být proveden.</span><span class="sxs-lookup"><span data-stu-id="81726-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="81726-188">SQL</span><span class="sxs-lookup"><span data-stu-id="81726-188">Sql</span></span>|<span data-ttu-id="81726-189">Příkaz SQL, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="81726-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="81726-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="81726-190">Parameters</span></span>|<span data-ttu-id="81726-191">Kolekce parametrů bude příkaz jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="81726-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="81726-192">mapování</span><span class="sxs-lookup"><span data-stu-id="81726-192">Mapper</span></span>|<span data-ttu-id="81726-193">Mapování funkce (<xref:System.Func%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` přidávaného do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="81726-194">V takovém případě mapování se provádí v jedné pulse provádění, ale nemůže být vytvořen deklarativně pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="81726-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="81726-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="81726-195">MapperFunc</span></span>|<span data-ttu-id="81726-196">Mapování funkce (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` přidávaného do `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="81726-197">V takovém případě mapování se provádí v několika počtu impulsů provádění.</span><span class="sxs-lookup"><span data-stu-id="81726-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="81726-198">Tato funkce může serializovat do XAML a je také autorem deklarativně (jakékoli existující aktivitu mohl podílet na mapování).</span><span class="sxs-lookup"><span data-stu-id="81726-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="81726-199">Výsledek</span><span class="sxs-lookup"><span data-stu-id="81726-199">Result</span></span>|<span data-ttu-id="81726-200">Po provedení dotazu a provádění funkce mapování pro každý záznam v získat seznam objektů `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="81726-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="81726-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="81726-201">DbQueryDataSet</span></span>
 <span data-ttu-id="81726-202">Provede dotaz, který vrací <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81726-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="81726-203">Tato třída provádí svou práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="81726-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="81726-204">Se odvozuje od <xref:System.Activities.AsyncCodeActivity> < `TResult`> a jeho asynchronní funkce používá.</span><span class="sxs-lookup"><span data-stu-id="81726-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="81726-205">Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81726-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="81726-206">Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="81726-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="81726-207">Po `DbQueryDataSet` provádí `DataSet` se vrátí v `Result out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="81726-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="81726-208">Argument</span><span class="sxs-lookup"><span data-stu-id="81726-208">Argument</span></span>|<span data-ttu-id="81726-209">Popis</span><span class="sxs-lookup"><span data-stu-id="81726-209">Description</span></span>|
|-|-|
|<span data-ttu-id="81726-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="81726-210">ProviderName</span></span>|<span data-ttu-id="81726-211">Výchozí název zprostředkovatele rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="81726-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="81726-212">Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="81726-213">připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="81726-213">ConnectionString</span></span>|<span data-ttu-id="81726-214">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-214">Connection string to connect to the database.</span></span> <span data-ttu-id="81726-215">Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="81726-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="81726-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="81726-216">ConfigName</span></span>|<span data-ttu-id="81726-217">Název oddílu konfiguračního souboru, kde se ukládají informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="81726-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="81726-218">Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="81726-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="81726-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="81726-219">CommandType</span></span>|<span data-ttu-id="81726-220">Typ <xref:System.Data.Common.DbCommand> má být proveden.</span><span class="sxs-lookup"><span data-stu-id="81726-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="81726-221">SQL</span><span class="sxs-lookup"><span data-stu-id="81726-221">Sql</span></span>|<span data-ttu-id="81726-222">Příkaz SQL, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="81726-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="81726-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="81726-223">Parameters</span></span>|<span data-ttu-id="81726-224">Kolekce parametrů bude příkaz jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="81726-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="81726-225">Výsledek</span><span class="sxs-lookup"><span data-stu-id="81726-225">Result</span></span>|<span data-ttu-id="81726-226"><xref:System.Data.DataSet> který získáte po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="81726-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="81726-227">Konfigurace informací o připojení</span><span class="sxs-lookup"><span data-stu-id="81726-227">Configuring Connection Information</span></span>
 <span data-ttu-id="81726-228">Všechny DbActivities sdílet stejné parametry konfigurace.</span><span class="sxs-lookup"><span data-stu-id="81726-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="81726-229">Se dají konfigurovat dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="81726-229">They can be configured in two ways:</span></span>

-   <span data-ttu-id="81726-230">`ConnectionString + InvariantName`: Nastavení poskytovatele ADO.NET neutrální název a připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="81726-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

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

-   <span data-ttu-id="81726-231">`ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="81726-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   <span data-ttu-id="81726-232">V aktivitě:</span><span class="sxs-lookup"><span data-stu-id="81726-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="81726-233">Spuštěním této ukázky</span><span class="sxs-lookup"><span data-stu-id="81726-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="81726-234">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="81726-234">Setup instructions</span></span>
 <span data-ttu-id="81726-235">Tato ukázka používá databázi.</span><span class="sxs-lookup"><span data-stu-id="81726-235">This sample uses a database.</span></span> <span data-ttu-id="81726-236">Se vzorkem je poskytován skript nastavení a načtení (Setup.cmd).</span><span class="sxs-lookup"><span data-stu-id="81726-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="81726-237">Je třeba spustit soubor pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="81726-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="81726-238">Skriptu Setup.cmd vyvolá CreateDb.sql souboru skriptu, který obsahuje příkazy SQL, které postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="81726-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

-   <span data-ttu-id="81726-239">Vytvoří databázi s názvem DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="81726-239">Creates a database called DbActivitiesSample.</span></span>

-   <span data-ttu-id="81726-240">Vytvoří tabulku role.</span><span class="sxs-lookup"><span data-stu-id="81726-240">Creates the Roles table.</span></span>

-   <span data-ttu-id="81726-241">Vytvoří tabulku se zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="81726-241">Creates Employees table.</span></span>

-   <span data-ttu-id="81726-242">Tři záznamy se vloží do tabulky role.</span><span class="sxs-lookup"><span data-stu-id="81726-242">Inserts three records into the Roles table.</span></span>

-   <span data-ttu-id="81726-243">Vloží dvanáct záznamy do tak tabulku Employees.</span><span class="sxs-lookup"><span data-stu-id="81726-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="81726-244">Chcete-li spustit Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="81726-244">To run Setup.cmd</span></span>

1.  <span data-ttu-id="81726-245">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="81726-245">Open a command prompt.</span></span>

2.  <span data-ttu-id="81726-246">Přejděte do složky s ukázkou DbActivities.</span><span class="sxs-lookup"><span data-stu-id="81726-246">Go to the DbActivities sample folder.</span></span>

3.  <span data-ttu-id="81726-247">Zadejte "setup.cmd" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="81726-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="81726-248">Setup.cmd pokusu o instalaci ukázky v místním počítači SqlExpress instanci.</span><span class="sxs-lookup"><span data-stu-id="81726-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="81726-249">Pokud chcete nainstalovat v jiné instance systému SQL server, upravte Setup.cmd s novým názvem instance.</span><span class="sxs-lookup"><span data-stu-id="81726-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="81726-250">Chcete-li odinstalovat ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="81726-250">To uninstall the sample database</span></span>

1.  <span data-ttu-id="81726-251">Spusťte Cleanup.cmd ze složky s ukázkou v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="81726-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="81726-252">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="81726-252">To run the sample</span></span>

1.  <span data-ttu-id="81726-253">Otevřete řešení v sadě Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="81726-253">Open the solution in Visual Studio 2010</span></span>

2.  <span data-ttu-id="81726-254">Chcete-li zkompilovat řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="81726-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="81726-255">Pokud chcete ukázku spustit bez ladění, stiskněte kombinaci kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="81726-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="81726-256">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="81726-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81726-257">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="81726-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81726-258">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="81726-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81726-259">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="81726-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
