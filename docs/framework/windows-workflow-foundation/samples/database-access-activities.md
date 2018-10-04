---
title: Aktivity přístupu k databázi
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: efcdd25ee3e6b86d87d551623b166eab4fa76845
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777903"
---
# <a name="database-access-activities"></a>Aktivity přístupu k databázi
Aktivity přístupu k databázi umožňují přístup k databázi v rámci pracovního postupu. Tyto aktivity umožňují přístup k databázím nebo upravte informace a použití [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  Pokud tento adresář neexistuje, přejděte na stránku (stahování) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Databázové aktivity
 Seznam aktivit, které jsou zahrnuté v této ukázce jsou podrobně popsané v následujících částech.

## <a name="dbupdate"></a>DbUpdate
 Provede dotaz SQL, který vytváří změny v databázi (insert, update, delete a jiné úpravy).

 Tato třída provádí svou práci asynchronně (se odvozuje od <xref:System.Activities.AsyncCodeActivity> a používá jeho asynchronní funkce).

 Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

 Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.

 Po `DbUpdate` se provedl a počet ovlivněných záznamů, které se vrátí v `AffectedRecords` vlastnost.

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

|Argument|Popis|
|-|-|
|ProviderName|Výchozí název zprostředkovatele rozhraní ADO.NET. Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.|
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.|
|ConfigName|Název oddílu konfiguračního souboru, kde se ukládají informace o připojení. Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> má být proveden.|
|SQL|Příkaz SQL, který se spustí.|
|Parametry|Kolekce parametrů bude příkaz jazyka SQL.|
|AffectedRecords|Počet záznamů ovlivněný podle poslední operaci.|

## <a name="dbqueryscalar"></a>DbQueryScalar
 Provede dotaz, který načte hodnotu single z databáze.

 Tato třída provádí svou práci asynchronně (se odvozuje od <xref:System.Activities.AsyncCodeActivity%601> a používá jeho asynchronní funkce).

 Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

 Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.

 Po `DbQueryScalar` se provedl a vytvořil skalárních se vrátí v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).

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

|Argument|Popis|
|-|-|
|ProviderName|Výchozí název zprostředkovatele rozhraní ADO.NET. Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.|
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.|
|ConfigName|Název oddílu konfiguračního souboru, kde se ukládají informace o připojení. Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> má být proveden.|
|SQL|Příkaz SQL, který se spustí.|
|Parametry|Kolekce parametrů bude příkaz jazyka SQL.|
|Výsledek|Skalární hodnota, která se získá po spuštění dotazu. Tento argument je typu `TResult`.|

## <a name="dbquery"></a>DbQuery
 Provede dotaz, který načte seznam objektů. Po spuštění dotazu mapování funkce se provede (může být <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Toto mapování funkce získá v záznamu `DbDataReader` a mapuje na objekt, který má být vrácen.

 Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

 Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.

 Výsledky dotazu SQL se načítají pomocí `DbDataReader`. Aktivita Iteruje přes `DbDataReader` a řádky v tabulce se mapuje `DbDataReader` do instance `TResult`. Uživatel `DbQuery` poskytnout mapování kódu, což lze provést dvěma způsoby: pomocí <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. V prvním případě mapy se provádí v jedné pulse provádění. Proto je rychlejší, ale to nejde serializovat do XAML. V posledním případě mapy probíhá v několika počtu impulsů. Proto může být pomalejší, ale může být serializován XAML a vytvořené pomocí deklarace (jakékoli existující aktivitu mohl podílet na mapování).

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

|Argument|Popis|
|-|-|
|ProviderName|Výchozí název zprostředkovatele rozhraní ADO.NET. Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.|
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.|
|ConfigName|Název oddílu konfiguračního souboru, kde se ukládají informace o připojení. Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> má být proveden.|
|SQL|Příkaz SQL, který se spustí.|
|Parametry|Kolekce parametrů bude příkaz jazyka SQL.|
|mapování|Mapování funkce (<xref:System.Func%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` přidávaného do `Result` kolekce.<br /><br /> V takovém případě mapování se provádí v jedné pulse provádění, ale nemůže být vytvořen deklarativně pomocí návrháře.|
|MapperFunc|Mapování funkce (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` přidávaného do `Result` kolekce.<br /><br /> V takovém případě mapování se provádí v několika počtu impulsů provádění. Tato funkce může serializovat do XAML a je také autorem deklarativně (jakékoli existující aktivitu mohl podílet na mapování).|
|Výsledek|Po provedení dotazu a provádění funkce mapování pro každý záznam v získat seznam objektů `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet
 Provede dotaz, který vrací <xref:System.Data.DataSet>. Tato třída provádí svou práci asynchronně. Se odvozuje od <xref:System.Activities.AsyncCodeActivity> < `TResult`> a jeho asynchronní funkce používá.

 Informace o připojení se dá nakonfigurovat pomocí nastavení výchozí název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

 Provedení dotazu je nakonfigurovaný v jeho `Sql` vlastnost a parametry jsou předány prostřednictvím `Parameters` kolekce.

 Po `DbQueryDataSet` provádí `DataSet` se vrátí v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).

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

|Argument|Popis|
|-|-|
|ProviderName|Výchozí název zprostředkovatele rozhraní ADO.NET. Pokud tento argument je nastavena, pak bude `ConnectionString` musí být také nastavena.|
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud tento argument je nastaven, pak `ProviderName` musí být také nastavena.|
|ConfigName|Název oddílu konfiguračního souboru, kde se ukládají informace o připojení. Pokud je tento argument nastavená `ProviderName` a `ConnectionString` se nevyžadují.|
|CommandType|Typ <xref:System.Data.Common.DbCommand> má být proveden.|
|SQL|Příkaz SQL, který se spustí.|
|Parametry|Kolekce parametrů bude příkaz jazyka SQL.|
|Výsledek|<xref:System.Data.DataSet> který získáte po provedení dotazu.|

## <a name="configuring-connection-information"></a>Konfigurace informací o připojení
 Všechny DbActivities sdílet stejné parametry konfigurace. Se dají konfigurovat dvěma způsoby:

-   `ConnectionString + InvariantName`: Nastavte zprostředkovatele ADO.NET neutrální název a připojovací řetězec.

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

-   `ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   V aktivitě:

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a>Spuštěním této ukázky

### <a name="setup-instructions"></a>Pokyny k instalaci
 Tato ukázka používá databázi. Se vzorkem je poskytován skript nastavení a načtení (Setup.cmd). Je třeba spustit soubor pomocí příkazového řádku.

 Skriptu Setup.cmd vyvolá CreateDb.sql souboru skriptu, který obsahuje příkazy SQL, které postupujte takto:

-   Vytvoří databázi s názvem DbActivitiesSample.

-   Vytvoří tabulku role.

-   Vytvoří tabulku se zaměstnanci.

-   Tři záznamy se vloží do tabulky role.

-   Vloží dvanáct záznamy do tak tabulku Employees.

##### <a name="to-run-setupcmd"></a>Chcete-li spustit Setup.cmd

1.  Otevřete příkazový řádek.

2.  Přejděte do složky s ukázkou DbActivities.

3.  Zadejte "setup.cmd" a stiskněte klávesu ENTER.

    > [!NOTE]
    >  Setup.cmd pokusu o instalaci ukázky v místním počítači SqlExpress instanci. Pokud chcete nainstalovat v jiné instance systému SQL server, upravte Setup.cmd s novým názvem instance.

##### <a name="to-uninstall-the-sample-database"></a>Chcete-li odinstalovat ukázkové databáze

1.  Spusťte Cleanup.cmd ze složky s ukázkou v příkazovém řádku.

##### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1.  Otevřete řešení v sadě Visual Studio 2010

2.  Chcete-li zkompilovat řešení, stiskněte CTRL + SHIFT + B.

3.  Pokud chcete ukázku spustit bez ladění, stiskněte kombinaci kláves CTRL + F5.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
