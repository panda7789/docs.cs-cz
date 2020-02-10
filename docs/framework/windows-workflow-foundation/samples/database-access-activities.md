---
title: Aktivity přístupu k databázi
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: ed3f0ad3f2fd19f622c9cb0faf7d5cd864b81995
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094641"
---
# <a name="database-access-activities"></a>Aktivity přístupu k databázi

Aktivity přístupu k databázi umožňují přístup k databázi v rámci pracovního postupu. Tyto aktivity umožňují přístup k databázím k načtení nebo úpravám informací a použití [ADO.NET](../../data/adonet/index.md) pro přístup k databázi.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, Stáhněte si všechny ukázky Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples (stáhnout stránku). Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Databázové aktivity

Následující části podrobně popisují seznam aktivit obsažených v této ukázce.

## <a name="dbupdate"></a>DbUpdate

Provede dotaz SQL, který vytvoří změnu v databázi (vložení, aktualizace, odstranění a další úpravy).

Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity> a používá své asynchronní funkce).

Informace o připojení lze nakonfigurovat nastavením neutrálního názvu poskytovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfigurace připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

Dotaz, který má být spuštěn, je konfigurován ve své vlastnosti `Sql` a parametry jsou předány prostřednictvím kolekce `Parameters`.

Po spuštění `DbUpdate` se v vlastnosti `AffectedRecords` vrátí počet ovlivněných záznamů.

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

|Argument|Popis|
|-|-|
|ProviderName|Neutrální název poskytovatele ADO.NET Pokud je tento argument nastaven, musí být také nastavena `ConnectionString`.|
|Vlastnosti|Připojovací řetězec pro připojení k databázi. Pokud je tento argument nastaven, musí být také nastavena `ProviderName`.|
|Config|Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení. Pokud je tento argument nastaven `ProviderName` a `ConnectionString` nejsou požadovány.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, který se má provést|
|Sql|Příkaz jazyka SQL, který má být spuštěn.|
|Parametry|Kolekce parametrů dotazu SQL|
|AffectedRecords|Počet záznamů ovlivněných poslední operací.|

## <a name="dbqueryscalar"></a>DbQueryScalar

Spustí dotaz, který načte jednu hodnotu z databáze.

Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a používá své asynchronní funkce).

Informace o připojení lze nakonfigurovat nastavením neutrálního názvu poskytovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfigurace připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

Dotaz, který má být spuštěn, je konfigurován ve své vlastnosti `Sql` a parametry jsou předány prostřednictvím kolekce `Parameters`.

Po spuštění `DbQueryScalar` se skalární hodnota vrátí v argumentu `Result out` (typu `TResult`, který je definován v <xref:System.Activities.AsyncCodeActivity%601>základní třídy).

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

|Argument|Popis|
|-|-|
|ProviderName|Neutrální název poskytovatele ADO.NET Pokud je tento argument nastaven, musí být také nastavena `ConnectionString`.|
|Vlastnosti|Připojovací řetězec pro připojení k databázi. Pokud je tento argument nastaven, musí být také nastavena `ProviderName`.|
|Config|Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení. Pokud je tento argument nastaven `ProviderName` a `ConnectionString` nejsou požadovány.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, který se má provést|
|Sql|Příkaz jazyka SQL, který má být spuštěn.|
|Parametry|Kolekce parametrů dotazu SQL|
|Výsledek|Skalární, který se získá po provedení dotazu. Tento argument je typu `TResult`.|

## <a name="dbquery"></a>DbQuery

Spustí dotaz, který načte seznam objektů. Po provedení dotazu se spustí funkce mapování (může být <xref:System.Func%601><`DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>). Tato funkce mapování získá záznam v `DbDataReader` a namapuje jej na objekt, který má být vrácen.

Informace o připojení lze nakonfigurovat nastavením neutrálního názvu poskytovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfigurace připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

Dotaz, který má být spuštěn, je konfigurován ve své vlastnosti `Sql` a parametry jsou předány prostřednictvím kolekce `Parameters`.

Výsledky dotazu SQL jsou načteny pomocí `DbDataReader`. Aktivita prochází `DbDataReader` a mapuje řádky v `DbDataReader` na instanci `TResult`. Uživatel `DbQuery` musí poskytovat mapovací kód a může to udělat dvěma způsoby: pomocí <xref:System.Func%601><`DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>. V prvním případě se mapa provádí v rámci jednoho Pulse spuštění. Proto je rychlejší, ale nelze jej serializovat do XAML. V posledním případě se mapa provádí ve více impulsech. Proto může být pomalejší, ale může být serializována do jazyka XAML a vytvořena deklarativně (každá existující aktivita se může účastnit mapování).

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

|Argument|Popis|
|-|-|
|ProviderName|Neutrální název poskytovatele ADO.NET Pokud je tento argument nastaven, musí být také nastavena `ConnectionString`.|
|Vlastnosti|Připojovací řetězec pro připojení k databázi. Pokud je tento argument nastaven, musí být také nastavena `ProviderName`.|
|Config|Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení. Pokud je tento argument nastaven `ProviderName` a `ConnectionString` nejsou požadovány.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, který se má provést|
|Sql|Příkaz jazyka SQL, který má být spuštěn.|
|Parametry|Kolekce parametrů dotazu SQL|
|Mapper|Funkce Mapping (<xref:System.Func%601><`DbDataReader``TResult`>), která přebírá záznam v `DataReader` získaný jako výsledek provedení dotazu a vrací instanci objektu typu `TResult`, který se má přidat do kolekce `Result`.<br /><br /> V tomto případě se mapování provádí v rámci jednoho Pulse provádění, ale nelze je vytvořit deklarativně pomocí návrháře.|
|MapperFunc|Funkce Mapping (<xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>), která přebírá záznam v `DataReader` získaný jako výsledek provedení dotazu a vrací instanci objektu typu `TResult`, který se má přidat do kolekce `Result`.<br /><br /> V tomto případě se mapování provádí ve více impulsech spuštění. Tato funkce se dá serializovat do XAML a vytvořit deklarativně (jakékoli existující aktivity se můžou účastnit mapování).|
|Výsledek|Seznam objektů získaných jako výsledek provedení dotazu a provedení funkce mapování pro každý záznam v `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet

Spustí dotaz, který vrátí <xref:System.Data.DataSet>. Tato třída provádí svou práci asynchronně. Je odvozen z <xref:System.Activities.AsyncCodeActivity><`TResult`> a používá jeho asynchronní možnosti.

Informace o připojení lze nakonfigurovat nastavením neutrálního názvu poskytovatele (`ProviderName`) a připojovacího řetězce (`ConnectionString`) nebo pouze pomocí názvu konfigurace připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.

Dotaz, který má být spuštěn, je konfigurován ve své vlastnosti `Sql` a parametry jsou předány prostřednictvím kolekce `Parameters`.

Po spuštění `DbQueryDataSet` `DataSet` je vrácen v argumentu `Result out` (typ `TResult`, který je definován v <xref:System.Activities.AsyncCodeActivity%601>základní třídy).

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

|Argument|Popis|
|-|-|
|ProviderName|Neutrální název poskytovatele ADO.NET Pokud je tento argument nastaven, musí být také nastavena `ConnectionString`.|
|Vlastnosti|Připojovací řetězec pro připojení k databázi. Pokud je tento argument nastaven, musí být také nastavena `ProviderName`.|
|Config|Název oddílu konfiguračního souboru, ve kterém jsou uloženy informace o připojení. Pokud je tento argument nastaven `ProviderName` a `ConnectionString` nejsou požadovány.|
|CommandType|Typ <xref:System.Data.Common.DbCommand>, který se má provést|
|Sql|Příkaz jazyka SQL, který má být spuštěn.|
|Parametry|Kolekce parametrů dotazu SQL|
|Výsledek|<xref:System.Data.DataSet>, která se získá po provedení dotazu.|

## <a name="configuring-connection-information"></a>Konfigurace informací o připojení

Všechny DbActivities mají stejné parametry konfigurace. Lze je nakonfigurovat dvěma způsoby:

- `ConnectionString + InvariantName`: nastavte neutrální název poskytovatele ADO.NET a připojovací řetězec.

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

- `ConfigName`: Nastavte název konfiguračního oddílu, který obsahuje informace o připojení.

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- V aktivitě:

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a>Spuštění této ukázky

### <a name="setup-instructions"></a>Pokyny k instalaci

V této ukázce se používá databáze. S ukázkou je k dispozici skript nastavení a načtení skriptu (Setup. cmd). Tento soubor musíte spustit pomocí příkazového řádku.

Skript Setup. cmd vyvolá soubor skriptu CreateDb. SQL, který obsahuje příkazy jazyka SQL, které jsou následující:

- Vytvoří databázi s názvem DbActivitiesSample.

- Vytvoří tabulku rolí.

- Vytvoří tabulku Employees.

- Vloží do tabulky rolí tři záznamy.

- Vloží do tabulky Employees 12 záznamů.

##### <a name="to-run-setupcmd"></a>Spuštění instalačního programu. cmd

1. Otevřete příkazový řádek.

2. Přejít do ukázkové složky DbActivities

3. Zadejte "Setup. cmd" a stiskněte klávesu ENTER.

    > [!NOTE]
    > Setup. cmd se pokusí nainstalovat ukázku do vaší místní instance počítače SqlExpress. Pokud ho chcete nainstalovat do jiné instance SQL serveru, upravte Setup. cmd s novým názvem instance.

##### <a name="to-uninstall-the-sample-database"></a>Odinstalace ukázkové databáze

1. Spusťte příkaz Cleanup. cmd z ukázkové složky na příkazovém řádku.

##### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Otevřete řešení v aplikaci Visual Studio 2010

2. Pro zkompilování řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Chcete-li spustit ukázku bez ladění, stiskněte klávesy CTRL + F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
