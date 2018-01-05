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
ms.workload: dotnet
ms.openlocfilehash: dfc99593e1c705cff5069b5dd864d372f8afda8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="database-access-activities"></a>Databáze Access aktivity
Databáze access aktivity umožňují přístup k databázi v rámci pracovního postupu. Tyto aktivity povolit přístup k databázím načtení nebo upravte informace a použití [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a>Databázové aktivity  
 V následujících oddílech jsou upřesněny seznam aktivit, které jsou součástí této ukázky.  
  
## <a name="dbupdate"></a>DbUpdate  
 Provede dotaz SQL, který vytváří změny v databázi (vložení, aktualizaci, odstranění a jiné změny).  
  
 Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity> a používá možnosti asynchronní).  
  
 Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.  
  
 Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.  
  
 Po `DbUpdate` je proveden, počet ovlivněných záznamů je vrácený v `AffectedRecords` vlastnost.  
  
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
|ProviderName|Neutrální název zprostředkovatele ADO.NET. Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.|  
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.|  
|ConfigName|Název oddílu konfiguračního souboru se uloží informace o připojení. Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.|  
|Typ příkazu CommandType|Typ <xref:System.Data.Common.DbCommand> spouštění.|  
|SQL|Příkaz SQL, který má být proveden.|  
|Parametry|Kolekce parametrů příkazu jazyka SQL.|  
|AffectedRecords|Počet záznamů ovlivněný poslední operace.|  
  
## <a name="dbqueryscalar"></a>DbQueryScalar  
 Provede dotaz, který načte jednu hodnotu z databáze.  
  
 Tato třída provádí svou práci asynchronně (je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a používá možnosti asynchronní).  
  
 Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.  
  
 Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.  
  
 Po `DbQueryScalar` je proveden, skalárních je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).  
  
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
|ProviderName|Neutrální název zprostředkovatele ADO.NET. Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.|  
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.|  
|ConfigName|Název oddílu konfiguračního souboru se uloží informace o připojení. Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.|  
|Typ příkazu CommandType|Typ <xref:System.Data.Common.DbCommand> spouštění.|  
|SQL|Příkaz SQL, který má být proveden.|  
|Parametry|Kolekce parametrů příkazu jazyka SQL.|  
|Výsledek|Skalární hodnota, která se získá po provedení dotazu. Tento argument je typu `TResult`.|  
  
## <a name="dbquery"></a>DbQuery  
 Provede dotaz, který načte seznam objektů. Po provedení dotazu provedení funkce mapování (může být <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Toto mapování funkce získá záznam v `DbDataReader` a mapuje na objekt, který má být vrácen.  
  
 Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.  
  
 Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.  
  
 Výsledky dotazu SQL se načítají pomocí `DbDataReader`. Aktivity provádí iteraci `DbDataReader` a mapuje řádky v `DbDataReader` na instanci `TResult`. Uživatel `DbQuery` musí zadat kód mapování a to můžete provést dvěma způsoby: pomocí <xref:System.Func%601> < `DbDataReader`, `TResult`> nebo <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. V prvním případě mapy probíhá v jednom pulse provádění. Proto je rychlejší, ale to nelze serializovat do jazyka XAML. V případě poslední mapy probíhá v několika impulsů. Proto může být pomalejší, ale může být serializován do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).  
  
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
|ProviderName|Neutrální název zprostředkovatele ADO.NET. Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.|  
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.|  
|ConfigName|Název oddílu konfiguračního souboru se uloží informace o připojení. Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.|  
|Typ příkazu CommandType|Typ <xref:System.Data.Common.DbCommand> spouštění.|  
|SQL|Příkaz SQL, který má být proveden.|  
|Parametry|Kolekce parametrů příkazu jazyka SQL.|  
|Mapper|Mapování funkce (<xref:System.Func%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.<br /><br /> V takovém případě mapování se provádí v jednom pulse spuštění, ale nemůže být vytvořené deklarativně pomocí návrháře.|  
|MapperFunc|Mapování funkce (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>), která má záznam `DataReader` získat po provedení dotazu a vrátí instanci objektu typu `TResult` být přidán do `Result` kolekce.<br /><br /> V takovém případě mapování se provádí v několika impulsů provádění. Tato funkce může serializovat do jazyka XAML a vytvořené deklarativně (všechny existující aktivitu mohl účastnit mapování).|  
|Výsledek|Po provedení dotazu a provádění mapování funkce pro každý záznam v získat seznam objektů `DataReader`.|  
  
## <a name="dbquerydataset"></a>DbQueryDataSet  
 Provede dotaz, který vrátí <xref:System.Data.DataSet>. Tato třída provádí svou práci asynchronně. Je odvozena z <xref:System.Activities.AsyncCodeActivity> < `TResult`> a používá možnosti asynchronní.  
  
 Informace o připojení se dá nakonfigurovat nastavení neutrální název zprostředkovatele (`ProviderName`) a připojovací řetězec (`ConnectionString`) nebo pouze pomocí konfigurace název připojovacího řetězce (`ConfigFileSectionName`) z konfiguračního souboru aplikace.  
  
 Provedení dotazu je nakonfigurovaný v jeho `Sql` předána vlastnost a parametry `Parameters` kolekce.  
  
 Po `DbQueryDataSet` se spustí `DataSet` je vrácený v `Result``out` argument (typu `TResult`, která je definována v základní třídě <xref:System.Activities.AsyncCodeActivity%601>).  
  
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
|ProviderName|Neutrální název zprostředkovatele ADO.NET. Pokud je nastavený tento argument, pak se `ConnectionString` musí být také nastavena.|  
|připojovací řetězec|Připojovací řetězec pro připojení k databázi. Pokud je nastaven tento argument, pak `ProviderName` musí být také nastavena.|  
|ConfigName|Název oddílu konfiguračního souboru se uloží informace o připojení. Když je nastavená na tomto argumentu `ProviderName` a `ConnectionString` nejsou potřeba.|  
|Typ příkazu CommandType|Typ <xref:System.Data.Common.DbCommand> spouštění.|  
|SQL|Příkaz SQL, který má být proveden.|  
|Parametry|Kolekce parametrů příkazu jazyka SQL.|  
|Výsledek|<xref:System.Data.DataSet>která se získá po provedení dotazu.|  
  
## <a name="configuring-connection-information"></a>Konfigurace informací o připojení  
 Všechny DbActivities sdílejí stejnou konfigurační parametry. Mohou být konfigurovány dvěma způsoby:  
  
-   `ConnectionString + InvariantName`: Nastavte zprostředkovatele ADO.NET invariantní název a připojovací řetězec.  
  
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
  
-   V rámci aktivity:  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a>Spuštění této ukázky  
  
### <a name="setup-instructions"></a>Pokyny k instalaci  
 Tato ukázka používá databázi. Nastavení a zatížení skript (Setup.cmd) k dispozici vzorku. Je třeba spustit tento soubor pomocí příkazového řádku.  
  
 Skript Setup.cmd vyvolá CreateDb.sql souboru skriptu, který obsahuje příkazy SQL, které postupujte takto:  
  
-   Vytvoří databázi názvem DbActivitiesSample.  
  
-   Vytvoří tabulku role.  
  
-   Vytvoří tabulku Zaměstnanci.  
  
-   Vloží do tabulky role tři záznamy.  
  
-   Vloží do tabulky Zaměstnanci dvanáct záznamy.  
  
##### <a name="to-run-setupcmd"></a>Ke spuštění Setup.cmd  
  
1.  Otevřete příkazový řádek.  
  
2.  Přejděte do složky DbActivities ukázka.  
  
3.  Zadejte "setup.cmd" a stiskněte klávesu ENTER.  
  
    > [!NOTE]
    >  Setup.cmd se pokusí ukázku nainstalujete v instanci SqlExpress místního počítače. Pokud chcete nainstalujte ho do jiné instance systému SQL server, upravte Setup.cmd s novým názvem instance.  
  
##### <a name="to-uninstall-the-sample-database"></a>Chcete-li odinstalovat ukázkové databáze  
  
1.  Spusťte Cleanup.cmd z ukázkové složky v příkazovém řádku.  
  
##### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení v[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
2.  Chcete-li zkompilovat řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit ukázku bez ladění, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
