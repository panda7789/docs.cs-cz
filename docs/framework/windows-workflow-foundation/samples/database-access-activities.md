---
title: Aktivity přístupu k databázi
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 31794a583e87b5948457fac754cb5bf66fafa09c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016036"
---
# <a name="database-access-activities"></a><span data-ttu-id="09c49-102">Aktivity přístupu k databázi</span><span class="sxs-lookup"><span data-stu-id="09c49-102">Database Access Activities</span></span>

<span data-ttu-id="09c49-103">Aktivity přístupu k databázi umožňují přístup k databázi v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="09c49-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="09c49-104">Tyto aktivity umožňují přístup k databázím k načtení nebo úpravám informací a použití [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="09c49-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09c49-105">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="09c49-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="09c49-106">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="09c49-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="09c49-107">Pokud tento adresář neexistuje, Stáhněte si všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky na stránce (stáhnout stránku).</span><span class="sxs-lookup"><span data-stu-id="09c49-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09c49-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="09c49-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="09c49-109">Databázové aktivity</span><span class="sxs-lookup"><span data-stu-id="09c49-109">Database Activities</span></span>

<span data-ttu-id="09c49-110">Následující části podrobně popisují seznam aktivit obsažených v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="09c49-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="09c49-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="09c49-111">DbUpdate</span></span>

<span data-ttu-id="09c49-112">Provede dotaz SQL, který vytvoří změnu v databázi (vložení, aktualizace, odstranění a další úpravy).</span><span class="sxs-lookup"><span data-stu-id="09c49-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="09c49-113">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity> a používá její asynchronní funkce).</span><span class="sxs-lookup"><span data-stu-id="09c49-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="09c49-114">Informace o připojení lze konfigurovat nastavením neutrálního názvu zprostředkovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfiguračního řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="09c49-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="09c49-115">Dotaz, který má být spuštěn, je konfigurován `Sql` ve své vlastnosti a parametry jsou předány `Parameters` prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="09c49-116">Po `DbUpdate` spuštění se `AffectedRecords` v vlastnosti vrátí počet ovlivněných záznamů.</span><span class="sxs-lookup"><span data-stu-id="09c49-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
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

|<span data-ttu-id="09c49-117">Argument</span><span class="sxs-lookup"><span data-stu-id="09c49-117">Argument</span></span>|<span data-ttu-id="09c49-118">Popis</span><span class="sxs-lookup"><span data-stu-id="09c49-118">Description</span></span>|
|-|-|
|<span data-ttu-id="09c49-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="09c49-119">ProviderName</span></span>|<span data-ttu-id="09c49-120">Neutrální název poskytovatele ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c49-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="09c49-121">Pokud je tento argument nastaven, `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="09c49-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09c49-122">ConnectionString</span></span>|<span data-ttu-id="09c49-123">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="09c49-123">Connection string to connect to the database.</span></span> <span data-ttu-id="09c49-124">Je-li tento argument nastaven, `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="09c49-125">Config</span><span class="sxs-lookup"><span data-stu-id="09c49-125">ConfigName</span></span>|<span data-ttu-id="09c49-126">Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="09c49-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="09c49-127">Pokud je tento argument nastaven `ProviderName` a `ConnectionString` není požadován.</span><span class="sxs-lookup"><span data-stu-id="09c49-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="09c49-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="09c49-128">CommandType</span></span>|<span data-ttu-id="09c49-129">Typ, <xref:System.Data.Common.DbCommand> který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="09c49-130">SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-130">Sql</span></span>|<span data-ttu-id="09c49-131">Příkaz jazyka SQL, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="09c49-132">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c49-132">Parameters</span></span>|<span data-ttu-id="09c49-133">Kolekce parametrů dotazu SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="09c49-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="09c49-134">AffectedRecords</span></span>|<span data-ttu-id="09c49-135">Počet záznamů ovlivněných poslední operací.</span><span class="sxs-lookup"><span data-stu-id="09c49-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="09c49-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="09c49-136">DbQueryScalar</span></span>

<span data-ttu-id="09c49-137">Spustí dotaz, který načte jednu hodnotu z databáze.</span><span class="sxs-lookup"><span data-stu-id="09c49-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="09c49-138">Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a používá její asynchronní funkce).</span><span class="sxs-lookup"><span data-stu-id="09c49-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="09c49-139">Informace o připojení lze konfigurovat nastavením neutrálního názvu zprostředkovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfiguračního řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="09c49-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="09c49-140">Dotaz, který má být spuštěn, je konfigurován `Sql` ve své vlastnosti a parametry jsou předány `Parameters` prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="09c49-141">Po `DbQueryScalar` spuštění se skalární hodnota vrátí `Result out` v argumentu (typu `TResult`, který je definován v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="09c49-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
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

|<span data-ttu-id="09c49-142">Argument</span><span class="sxs-lookup"><span data-stu-id="09c49-142">Argument</span></span>|<span data-ttu-id="09c49-143">Popis</span><span class="sxs-lookup"><span data-stu-id="09c49-143">Description</span></span>|
|-|-|
|<span data-ttu-id="09c49-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="09c49-144">ProviderName</span></span>|<span data-ttu-id="09c49-145">Neutrální název poskytovatele ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c49-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="09c49-146">Pokud je tento argument nastaven, `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="09c49-147">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09c49-147">ConnectionString</span></span>|<span data-ttu-id="09c49-148">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="09c49-148">Connection string to connect to the database.</span></span> <span data-ttu-id="09c49-149">Je-li tento argument nastaven, `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="09c49-150">Config</span><span class="sxs-lookup"><span data-stu-id="09c49-150">ConfigName</span></span>|<span data-ttu-id="09c49-151">Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="09c49-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="09c49-152">Pokud je tento argument nastaven `ProviderName` a `ConnectionString` není požadován.</span><span class="sxs-lookup"><span data-stu-id="09c49-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="09c49-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="09c49-153">CommandType</span></span>|<span data-ttu-id="09c49-154">Typ, <xref:System.Data.Common.DbCommand> který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="09c49-155">SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-155">Sql</span></span>|<span data-ttu-id="09c49-156">Příkaz jazyka SQL, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="09c49-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c49-157">Parameters</span></span>|<span data-ttu-id="09c49-158">Kolekce parametrů dotazu SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="09c49-159">Výsledek</span><span class="sxs-lookup"><span data-stu-id="09c49-159">Result</span></span>|<span data-ttu-id="09c49-160">Skalární, který se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="09c49-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="09c49-161">Tento argument je typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="09c49-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="09c49-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="09c49-162">DbQuery</span></span>

<span data-ttu-id="09c49-163">Spustí dotaz, který načte seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="09c49-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="09c49-164">Po <xref:System.Func%601>provedení dotazu se provede funkce mapování (může to být `DbDataReader` <xref:System.Activities.ActivityFunc%601> `DbDataReader` <, `TResult`> < nebo`TResult`>).</span><span class="sxs-lookup"><span data-stu-id="09c49-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="09c49-165">Tato funkce mapování načte záznam v `DbDataReader` a a provede jeho mapování na objekt, který má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="09c49-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="09c49-166">Informace o připojení lze konfigurovat nastavením neutrálního názvu zprostředkovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfiguračního řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="09c49-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="09c49-167">Dotaz, který má být spuštěn, je konfigurován `Sql` ve své vlastnosti a parametry jsou předány `Parameters` prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="09c49-168">Výsledky dotazu SQL jsou načteny pomocí `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="09c49-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="09c49-169">Aktivita prochází `DbDataReader` a mapuje řádky `DbDataReader` v objektu na instanci `TResult`.</span><span class="sxs-lookup"><span data-stu-id="09c49-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="09c49-170">`DbQuery` Uživatel musí poskytnout mapování kódu a může to provést dvěma způsoby: < <xref:System.Func%601> <xref:System.Activities.ActivityFunc%601> < `DbDataReader`pomocí `TResult`> nebo `DbDataReader` >.`TResult`</span><span class="sxs-lookup"><span data-stu-id="09c49-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="09c49-171">V prvním případě se mapa provádí v rámci jednoho Pulse spuštění.</span><span class="sxs-lookup"><span data-stu-id="09c49-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="09c49-172">Proto je rychlejší, ale nelze jej serializovat do XAML.</span><span class="sxs-lookup"><span data-stu-id="09c49-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="09c49-173">V posledním případě se mapa provádí ve více impulsech.</span><span class="sxs-lookup"><span data-stu-id="09c49-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="09c49-174">Proto může být pomalejší, ale může být serializována do jazyka XAML a vytvořena deklarativně (každá existující aktivita se může účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="09c49-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
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

|<span data-ttu-id="09c49-175">Argument</span><span class="sxs-lookup"><span data-stu-id="09c49-175">Argument</span></span>|<span data-ttu-id="09c49-176">Popis</span><span class="sxs-lookup"><span data-stu-id="09c49-176">Description</span></span>|
|-|-|
|<span data-ttu-id="09c49-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="09c49-177">ProviderName</span></span>|<span data-ttu-id="09c49-178">Neutrální název poskytovatele ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c49-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="09c49-179">Pokud je tento argument nastaven, `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="09c49-180">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09c49-180">ConnectionString</span></span>|<span data-ttu-id="09c49-181">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="09c49-181">Connection string to connect to the database.</span></span> <span data-ttu-id="09c49-182">Je-li tento argument nastaven, `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="09c49-183">Config</span><span class="sxs-lookup"><span data-stu-id="09c49-183">ConfigName</span></span>|<span data-ttu-id="09c49-184">Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="09c49-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="09c49-185">Pokud je tento argument nastaven `ProviderName` a `ConnectionString` není požadován.</span><span class="sxs-lookup"><span data-stu-id="09c49-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="09c49-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="09c49-186">CommandType</span></span>|<span data-ttu-id="09c49-187">Typ, <xref:System.Data.Common.DbCommand> který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="09c49-188">SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-188">Sql</span></span>|<span data-ttu-id="09c49-189">Příkaz jazyka SQL, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="09c49-190">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c49-190">Parameters</span></span>|<span data-ttu-id="09c49-191">Kolekce parametrů dotazu SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="09c49-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="09c49-192">Mapper</span></span>|<span data-ttu-id="09c49-193">Funkce Mapping (<xref:System.Func%601>< `DataReader` , >), která přebírá záznam ve získaný jako výsledek provedení dotazu a vrací instanci objektu typu `TResult` , který se má přidat do `TResult``DbDataReader` `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="09c49-194">V tomto případě se mapování provádí v rámci jednoho Pulse provádění, ale nelze je vytvořit deklarativně pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="09c49-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="09c49-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="09c49-195">MapperFunc</span></span>|<span data-ttu-id="09c49-196">Funkce Mapping (<xref:System.Activities.ActivityFunc%601>< `DataReader` , >), která přebírá záznam ve získaný jako výsledek provedení dotazu a vrací instanci objektu typu `TResult` , který se má přidat do `TResult``DbDataReader` `Result` kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="09c49-197">V tomto případě se mapování provádí ve více impulsech spuštění.</span><span class="sxs-lookup"><span data-stu-id="09c49-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="09c49-198">Tato funkce se dá serializovat do XAML a vytvořit deklarativně (jakékoli existující aktivity se můžou účastnit mapování).</span><span class="sxs-lookup"><span data-stu-id="09c49-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="09c49-199">Výsledek</span><span class="sxs-lookup"><span data-stu-id="09c49-199">Result</span></span>|<span data-ttu-id="09c49-200">Seznam objektů získaných jako výsledek provedení dotazu a provedení funkce mapování pro každý záznam v `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="09c49-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="09c49-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="09c49-201">DbQueryDataSet</span></span>

<span data-ttu-id="09c49-202">Spustí dotaz, který vrátí <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="09c49-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="09c49-203">Tato třída provádí svou práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="09c49-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="09c49-204">Je odvozen z <xref:System.Activities.AsyncCodeActivity> < >apoužívájehoasynchronnímožnosti`TResult`.</span><span class="sxs-lookup"><span data-stu-id="09c49-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="09c49-205">Informace o připojení lze konfigurovat nastavením neutrálního názvu zprostředkovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfiguračního řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="09c49-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="09c49-206">Dotaz, který má být spuštěn, je konfigurován `Sql` ve své vlastnosti a parametry jsou předány `Parameters` prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="09c49-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="09c49-207">`Result out` `TResult`Po spuštění se vrátí v argumentu (typu, který je definován v základní třídě <xref:System.Activities.AsyncCodeActivity%601>). `DataSet` `DbQueryDataSet`</span><span class="sxs-lookup"><span data-stu-id="09c49-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
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

|<span data-ttu-id="09c49-208">Argument</span><span class="sxs-lookup"><span data-stu-id="09c49-208">Argument</span></span>|<span data-ttu-id="09c49-209">Popis</span><span class="sxs-lookup"><span data-stu-id="09c49-209">Description</span></span>|
|-|-|
|<span data-ttu-id="09c49-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="09c49-210">ProviderName</span></span>|<span data-ttu-id="09c49-211">Neutrální název poskytovatele ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c49-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="09c49-212">Pokud je tento argument nastaven, `ConnectionString` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="09c49-213">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09c49-213">ConnectionString</span></span>|<span data-ttu-id="09c49-214">Připojovací řetězec pro připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="09c49-214">Connection string to connect to the database.</span></span> <span data-ttu-id="09c49-215">Je-li tento argument nastaven, `ProviderName` musí být také nastavena.</span><span class="sxs-lookup"><span data-stu-id="09c49-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="09c49-216">Config</span><span class="sxs-lookup"><span data-stu-id="09c49-216">ConfigName</span></span>|<span data-ttu-id="09c49-217">Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="09c49-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="09c49-218">Pokud je tento argument nastaven `ProviderName` a `ConnectionString` není požadován.</span><span class="sxs-lookup"><span data-stu-id="09c49-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="09c49-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="09c49-219">CommandType</span></span>|<span data-ttu-id="09c49-220">Typ, <xref:System.Data.Common.DbCommand> který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="09c49-221">SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-221">Sql</span></span>|<span data-ttu-id="09c49-222">Příkaz jazyka SQL, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="09c49-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="09c49-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c49-223">Parameters</span></span>|<span data-ttu-id="09c49-224">Kolekce parametrů dotazu SQL</span><span class="sxs-lookup"><span data-stu-id="09c49-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="09c49-225">Výsledek</span><span class="sxs-lookup"><span data-stu-id="09c49-225">Result</span></span>|<span data-ttu-id="09c49-226"><xref:System.Data.DataSet>který se získá po provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="09c49-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="09c49-227">Konfigurace informací o připojení</span><span class="sxs-lookup"><span data-stu-id="09c49-227">Configuring Connection Information</span></span>

<span data-ttu-id="09c49-228">Všechny DbActivities mají stejné parametry konfigurace.</span><span class="sxs-lookup"><span data-stu-id="09c49-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="09c49-229">Lze je nakonfigurovat dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="09c49-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="09c49-230">`ConnectionString + InvariantName`: Nastavte neutrální název poskytovatele ADO.NET a připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="09c49-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="09c49-231">`ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.</span><span class="sxs-lookup"><span data-stu-id="09c49-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="09c49-232">V aktivitě:</span><span class="sxs-lookup"><span data-stu-id="09c49-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="09c49-233">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="09c49-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="09c49-234">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="09c49-234">Setup instructions</span></span>

<span data-ttu-id="09c49-235">V této ukázce se používá databáze.</span><span class="sxs-lookup"><span data-stu-id="09c49-235">This sample uses a database.</span></span> <span data-ttu-id="09c49-236">S ukázkou je k dispozici skript nastavení a načtení skriptu (Setup. cmd).</span><span class="sxs-lookup"><span data-stu-id="09c49-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="09c49-237">Tento soubor musíte spustit pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="09c49-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="09c49-238">Skript Setup. cmd vyvolá soubor skriptu CreateDb. SQL, který obsahuje příkazy jazyka SQL, které jsou následující:</span><span class="sxs-lookup"><span data-stu-id="09c49-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="09c49-239">Vytvoří databázi s názvem DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="09c49-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="09c49-240">Vytvoří tabulku rolí.</span><span class="sxs-lookup"><span data-stu-id="09c49-240">Creates the Roles table.</span></span>

- <span data-ttu-id="09c49-241">Vytvoří tabulku Employees.</span><span class="sxs-lookup"><span data-stu-id="09c49-241">Creates Employees table.</span></span>

- <span data-ttu-id="09c49-242">Vloží do tabulky rolí tři záznamy.</span><span class="sxs-lookup"><span data-stu-id="09c49-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="09c49-243">Vloží do tabulky Employees 12 záznamů.</span><span class="sxs-lookup"><span data-stu-id="09c49-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="09c49-244">Spuštění instalačního programu. cmd</span><span class="sxs-lookup"><span data-stu-id="09c49-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="09c49-245">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="09c49-245">Open a command prompt.</span></span>

2. <span data-ttu-id="09c49-246">Přejít do ukázkové složky DbActivities</span><span class="sxs-lookup"><span data-stu-id="09c49-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="09c49-247">Zadejte "Setup. cmd" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="09c49-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="09c49-248">Setup. cmd se pokusí nainstalovat ukázku do vaší místní instance počítače SqlExpress.</span><span class="sxs-lookup"><span data-stu-id="09c49-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="09c49-249">Pokud ho chcete nainstalovat do jiné instance SQL serveru, upravte Setup. cmd s novým názvem instance.</span><span class="sxs-lookup"><span data-stu-id="09c49-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="09c49-250">Odinstalace ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="09c49-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="09c49-251">Spusťte příkaz Cleanup. cmd z ukázkové složky na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="09c49-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="09c49-252">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="09c49-252">To run the sample</span></span>

1. <span data-ttu-id="09c49-253">Otevřete řešení v aplikaci Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="09c49-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="09c49-254">Pro zkompilování řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="09c49-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="09c49-255">Chcete-li spustit ukázku bez ladění, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="09c49-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09c49-256">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="09c49-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="09c49-257">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="09c49-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="09c49-258">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="09c49-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09c49-259">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="09c49-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
