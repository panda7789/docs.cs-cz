---
title: Doprovodné materiály k zabezpečení datových sad a DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 4fe8a062c762cc70d33243e3443aa9bf55635f98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137614"
---
# <a name="dataset-and-datatable-security-guidance"></a>Doprovodné materiály k zabezpečení datových sad a DataTable

Tento článek se týká:

* .NET Framework (všechny verze)
* .NET Core a novější
* .NET 5,0 a novější

Typy [DataSet](/dotnet/api/system.data.dataset) a [DataTable](/dotnet/api/system.data.datatable) jsou starší komponenty rozhraní .NET, které umožňují reprezentace datových sad jako spravovaných objektů. Tyto součásti byly představeny v rozhraní .NET 1,0 jako součást původní [infrastruktury ADO.NET](/dotnet/framework/data/adonet/dataset-datatable-dataview/). Jejich cílem bylo poskytnout spravované zobrazení přes relační datovou sadu, a vyříznout si tak, jestli základní zdroj dat byl XML, SQL nebo jiná technologie.

Další informace o ADO.NET, včetně pokročilejších paradigmat zobrazení dat, najdete v [dokumentaci k ADO.NET](/dotnet/framework/data/adonet/).

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>Výchozí omezení při deserializaci datové sady nebo DataTable z XML

Na všech podporovaných verzích .NET Framework, .NET Core a .NET `DataSet` a `DataTable` umístěte následující omezení pro typy objektů, které mohou být k dispozici v deserializovaných datech. Ve výchozím nastavení je tento seznam omezen na:

* Primitivní a primitivní ekvivalenty: `bool` ,,,, `char` `sbyte` `byte` `short` , `ushort` , `int` , `uint` , `long` ,,,, `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, a.
* Běžně používané neprimitivní prvky: `Type` , a `Uri` `BigInteger` .
* Běžně používané typy _System. Drawing_ : `Color` , `Point` , `PointF` , `Rectangle` , `RectangleF` , a `Size` `SizeF` .
* `Enum` druhy.
* Pole a seznamy výše uvedených typů.

Pokud příchozí XML data obsahují objekt, jehož typ není v tomto seznamu:

* V následující zprávě a trasování zásobníku je vyvolána výjimka.  
Chybová zpráva:  
System. InvalidOperationException: type \<Type Name\> , Version = \<n.n.n.n\> , Culture = \<culture\> , PublicKeyToken = není \<token value\> tady povolený. Další podrobnosti najdete v tématu [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) .  
Trasování zásobníku:  
v System. data. TypeLimiter. EnsureTypeIsAllowed (typ typu, TypeLimiter capturedLimiter)  
v System. data. DataColumn. UpdateColumnType (typ typu, StorageType typeCode)  
v System. data. DataColumn. set_DataType (hodnota typu)  

* Operace deserializace se nezdařila.

Při načítání kódu XML do existující `DataSet` `DataTable` instance nebo je také nutné vzít v úvahu existující definice sloupců. Pokud tabulka již obsahuje definici sloupce vlastního typu, tento typ je dočasně přidán do seznamu povolených po dobu trvání operace deserializace XML.

> [!NOTE]
> Po přidání sloupců do nástroje nebude `DataTable` `ReadXml` ze souboru XML Přečtěte schéma a pokud se schéma neshoduje, nebude se v záznamech číst, takže budete muset přidat všechny sloupce sami, abyste mohli tuto metodu použít.

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

Omezení typu objektu platí také při použití `XmlSerializer` k deserializaci instance `DataSet` nebo `DataTable` . Nemusí však platit při použití `BinaryFormatter` k deserializaci instance `DataSet` nebo `DataTable` .

Omezení typu objektu neplatí při použití `DataAdapter.Fill` , například pokud `DataTable` je instance naplněna přímo z databáze bez použití rozhraní API deserializace XML.

### <a name="extend-the-list-of-allowed-types"></a>Rozšíří seznam povolených typů.

Aplikace může rozšířit seznam povolených typů tak, aby kromě předdefinovaných typů uvedených výše zahrnoval vlastní typy. Pokud se seznam povolených typů rozšíří, ovlivní tato změna _všechny_ `DataSet` `DataTable` instance a v rámci aplikace. Typy nelze odebrat z předdefinovaných povolených typů.

#### <a name="extend-through-configuration-net-framework-40---48"></a>Rozšířené konfigurace (.NET Framework 4,0-4,8)

_App.config_ lze použít k roztažení seznamu povolených typů. Chcete-li roztáhnout seznam povolených typů:

* Pomocí `<configSections>` elementu přidejte odkaz na oddíl _System. data_ Configuration.
* Použijte `<system.data.dataset.serialization>` / `<allowedTypes>` k určení dalších typů.

Každý `<add>` prvek musí určovat pouze jeden typ pomocí kvalifikovaného názvu typu sestavení. Chcete-li přidat další typy do seznamu povolených typů, použijte více `<add>` prvků.

Následující příklad ukazuje rozšíření seznamu povolených typů přidáním vlastního typu `Fabrikam.CustomType` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Chcete-li načíst kvalifikovaný název sestavení typu, použijte vlastnost [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , jak je znázorněno v následujícím kódu.

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>Rozšířené konfigurace (.NET Framework 2,0-3,5)

Pokud se vaše aplikace zaměřuje .NET Framework 2,0 nebo 3,5, můžete k roztažení seznamu povolených typů dál použít výše uvedený _App.config_ mechanismus. Váš element však `<configSections>` bude vypadat mírně odlišně, jak je znázorněno v následujícím kódu:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>Roztažení programově (.NET Framework, .NET Core, .NET 5.0 +)

Seznam povolených typů lze také programově rozšířit pomocí [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) s dobře známým klíčem _System. data. DataSetDefaultAllowedTypes_, jak je znázorněno v následujícím kódu.

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

Při použití mechanismu rozšíření musí být hodnota přidružená k klíči _System. data. DataSetDefaultAllowedTypes_ typu `Type[]` .

V .NET Framework lze seznam povolených typů rozšířit pomocí _App.config_ a `AppDomain.SetData` . V tomto případě `DataSet` a `DataTable` povolí, aby objekt byl rekonstruován jako součást dat, pokud je jeho typ přítomen v obou seznamech.

### <a name="run-an-app-in-audit-mode-net-framework"></a>Spuštění aplikace v režimu auditování (.NET Framework)

V .NET Framework `DataSet` a `DataTable` Poskytněte možnost režimu auditování. Když je povolen režim auditování `DataSet` a `DataTable` porovná typy příchozích objektů se seznamem povolených typů. Nicméně pokud objekt, jehož typ není povolen, **není vyvolána výjimka** . Místo toho `DataSet` a `DataTable` upozorněte všechny připojené `TraceListener` instance, které jsou k dispozici podezřelý typ, což umožňuje `TraceListener` Protokolovat tyto informace. Není vyvolána žádná výjimka a operace deserializace pokračuje.

> [!WARNING]
> Spuštění aplikace v režimu auditu by mělo být jenom dočasnou mírou, která se používá pro testování. Když je povolen režim auditu `DataSet` a `DataTable` nevynutila se omezení typů, která můžou do aplikace zavádět bezpečnostní otvor. Další informace najdete v oddílech s názvem [Odebrání všech omezení typu](#ratr) a [bezpečnosti s ohledem na nedůvěryhodný vstup](#swr).

Režim auditování lze povolit prostřednictvím _App.config_:

* Informace o správné hodnotě pro vložení elementu najdete v části [rozšíření prostřednictvím konfiguračního](#etc) souboru v tomto dokumentu `<configSections>` .
* Použijte `<allowedTypes auditOnly="true">` k povolení režimu auditování, jak je znázorněno v následujícím kódu.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Po povolení režimu auditu můžete použít _App.config_ pro připojení k `TraceListener` `DataSet` předdefinovanému `TraceSource.` názvu integrovaného zdroje trasování je _System. data. DataSet_. Následující příklad ukazuje zápis událostí trasování do konzoly nástroje _a_ do souboru protokolu na disku.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

Další informace o `TraceSource` a `TraceListener` najdete v dokumentu [Postupy: použití TraceSource a filtrů s naslouchacími procesy trasování](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).

> [!NOTE]
> Spuštění aplikace v režimu auditování není v rozhraní .NET Core nebo .NET 5,0 a novějších k dispozici.

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>Odebrat všechna omezení typů

Pokud aplikace musí odebrat všechny omezující omezení typu `DataSet` a `DataTable` :

* Existuje několik možností, jak potlačit omezení typu omezení.
* Dostupné možnosti závisí na architektuře, na kterou aplikace cílí.

> [!WARNING]
> Odebrání všech omezení typu může do aplikace zavádět bezpečnostní otvor. Při použití tohoto mechanismu ověřte, že aplikace **nepoužívá** `DataSet` nebo `DataTable` čte nedůvěryhodný vstup. Další informace najdete v článku [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) a v následující části [s názvem bezpečnost s ohledem na nedůvěryhodný vstup](#swr).

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>Prostřednictvím konfigurace AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 a novější, .NET 5,0 a novější)

`AppContext`Přepínač, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , pokud je nastaveno na `true` Odebrat všechny omezující omezení typu z `DataSet` a `DataTable` .

V .NET Framework lze tento přepínač Povolit prostřednictvím _App.config_, jak je znázorněno v následující konfiguraci:

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

V ASP.NET není `<AppContextSwitchOverrides>` element k dispozici. Místo toho lze přepínač Povolit prostřednictvím _Web.config_, jak je znázorněno v následující konfiguraci:

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

Další informace naleznete v tématu [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu.

V rozhraní .NET Core, .NET 5 a ASP.NET Core toto nastavení ovládá _runtimeconfig.jsna_, jak je znázorněno v následujícím kódu JSON:

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

Další informace naleznete v tématu ["nastavení konfigurace runtime .NET Core"](/dotnet/core/run-time-config/).

`AllowArbitraryDataSetTypeInstantiation` lze také nastavit programově prostřednictvím [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) namísto použití konfiguračního souboru, jak je znázorněno v následujícím kódu:

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 Pokud zvolíte předchozí programový přístup, volání, které `AppContext.SetSwitch` by mělo probíhat na začátku ve spuštění aplikace.

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>V registru v rámci počítače (.NET Framework 2,0-4,8)

Pokud `AppContext` není k dispozici, můžete zakázat kontrolu typu v registru systému Windows:

* Správce musí nakonfigurovat registr.
* Použití registru je změnou celého počítače a bude mít vliv na _všechny_ aplikace běžící v počítači.

| Typ  |  Hodnota |
|---|---|
| **Klíč registru** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **Název hodnoty** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **Typ hodnoty** | `REG_SZ` |
| **Údaj hodnoty** | `true` |

V 64 operačním systému musí být tato hodnota přičtena pro 64 klíč (zobrazený výše) a 32-bitový klíč. 32 bitový klíč se nachází na adrese `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .

Další informace o tom, jak nakonfigurovat registr ke konfiguraci `AppContext` , najdete v tématu ["AppContext pro příjemce knihovny"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>Bezpečnost s ohledem na nedůvěryhodný vstup

Nicméně `DataSet` a `DataTable` ukládají výchozí omezení pro typy, které mohou být přítomny při deserializaci datových částí XML __ `DataSet` a `DataTable` obecně nejsou bezpečné, pokud jsou naplněny nedůvěryhodnými vstupy.__ Následující seznam nevyčerpávajících způsobů, jak `DataSet` `DataTable` může instance nebo číst nedůvěryhodný vstup.

* `DataAdapter`Odkazuje na databázi a `DataAdapter.Fill` metoda se používá k naplnění `DataSet` obsahu databázového dotazu.
* `DataSet.ReadXml`Metoda nebo `DataTable.ReadXml` se používá ke čtení souboru XML obsahujícího informace o sloupci a řádku.
* `DataSet`Instance nebo `DataTable` je serializována jako součást webových služeb ASP.NET (SOAP) nebo z koncového bodu WCF.
* Serializátor, jako je například, `XmlSerializer` slouží k deserializaci `DataSet` `DataTable` instance nebo z datového proudu XML.
* Serializátor, jako je například, `JsonConvert` slouží k deserializaci `DataSet` `DataTable` instance nebo z datového proudu JSON. `JsonConvert` je metoda v oblíbenýchNewtonsoft.Jstřetích stran [ v](https://www.newtonsoft.com/json) knihovně.
* Serializátor, jako je například, `BinaryFormatter` se používá k deserializaci `DataSet` `DataTable` instance nebo z nezpracovaného bajtového datového proudu.

Tento dokument popisuje bezpečnostní požadavky pro předchozí scénáře.

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>Použijte `DataAdapter.Fill` k naplnění `DataSet` z nedůvěryhodného zdroje dat.

`DataSet`Instanci lze naplnit `DataAdapter` pomocí [ `DataAdapter.Fill` metody](/dotnet/api/system.data.common.dataadapter.fill), jak je znázorněno v následujícím příkladu.

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

(Výše uvedená ukázka kódu je součástí většího vzorku, který byl nalezen při [naplnění datové sady z objektu DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)

> Většina aplikací může zjednodušit a předpokládat, že je jejich databázová vrstva důvěryhodná. Nicméně, pokud jste [ve výrobním prostředí pro vaše](https://www.microsoft.com/securityengineering/sdl/threatmodeling) aplikace, váš model hrozeb může považovat za hranice důvěry mezi aplikací (klientem) a vrstvou databáze (serverem). Použití [vzájemného ověřování](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) nebo [ověřování AAD](/azure/azure-sql/database/authentication-aad-overview) mezi klientem a serverem je jedním ze způsobů, jak pomoci vyřešit rizika spojená s tímto. Zbývající část této části popisuje možný výsledek připojení klienta k nedůvěryhodnému serveru.

Důsledky ukazatele myši `DataAdapter` na nedůvěryhodný zdroj dat závisí na implementaci `DataAdapter` samotného.

### <a name="sqldataadapter"></a>SqlDataAdapter

Pro předdefinovaný typ [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), který odkazuje na nedůvěryhodný zdroj dat, by mohlo dojít k útokům DOS (Denial of Service). Útok DoS by mohl způsobit, že aplikace přestane reagovat nebo dojde k chybě. Pokud může útočník vysázet knihovnu DLL společně s aplikací, mohou být také schopny dosáhnout místního spuštění kódu.

### <a name="other-dataadapter-types"></a>Jiné typy DataAdapter

Implementace třetích stran `DataAdapter` musí učinit vlastní posouzení o tom, jaké záruky zabezpečení poskytují na tvář nedůvěryhodných vstupů. Rozhraní .NET nemůže žádným bezpečnostním zárukám souvisejícím s těmito implementacemi dělat.

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet. ReadXml a DataTable. ReadXml

`DataSet.ReadXml`Metody a `DataTable.ReadXml` nejsou bezpečné při použití s nedůvěryhodným vstupem. Důrazně doporučujeme, aby spotřebitelé místo toho měli možnost použít jednu z alternativ uvedených v tomto dokumentu později.

Implementace `DataSet.ReadXml` a `DataTable.ReadXml` byly původně vytvořené před chybami zabezpečení serializace byly dobře srozumitelnější kategorie hrozeb. V důsledku toho kód nedodržuje aktuální osvědčené postupy zabezpečení. Tato rozhraní API je možné použít jako vektory pro útočníky k provádění útoků DoS proti webovým aplikacím. Tyto útoky mohou vykreslovat webovou službu jako nereagující nebo vést k neočekávanému ukončení procesu. Rozhraní neposkytuje omezení pro tyto kategorie útoků a rozhraní .NET toto chování považuje za "podle návrhu".

Rozhraní .NET vydala aktualizace zabezpečení, které umožňují zmírnit některé problémy, například vyzrazení informací nebo vzdálené spuštění kódu v `DataSet.ReadXml` a `DataTable.ReadXml` . Aktualizace zabezpečení .NET nemusí poskytovat kompletní ochranu proti těmto kategoriím hrozeb. Spotřebitelé by měli vyhodnotit své jednotlivé scénáře a vzít v úvahu potenciální ozáření těchto rizik.

Spotřebitelé by měli vědět, že aktualizace zabezpečení těchto rozhraní API můžou v některých situacích ovlivnit kompatibilitu aplikací. Kromě toho existuje možnost, že se zjistí nová chyba zabezpečení v těchto rozhraních API, pro kterou .NET nedokáže prakticky publikovat aktualizaci zabezpečení.

Zákazníkům těchto rozhraní API doporučujeme:

* Zvažte použití jedné z alternativ uvedených níže v tomto dokumentu.
* Provádějte individuální posouzení rizik na svých aplikacích.

K určení, jestli se mají používat tato rozhraní API, se jedná výhradně o zodpovědnost spotřebitele. Spotřebitelé by měli vyhodnotit jakákoli bezpečnostní, technická a zákonná rizika, včetně regulativních požadavků, které mohou doprovázet pomocí těchto rozhraní API.

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>Datová sada a DataTable prostřednictvím webových služeb ASP.NET nebo WCF

Je možné přijmout `DataSet` `DataTable` instanci nebo instance v rámci webové služby ASP.NET (SOAP), jak je znázorněno v následujícím kódu:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

Variace v této podobě není akceptovat `DataSet` ani `DataTable` přímo jako parametr, ale místo toho ji přijmout jako součást celkového grafu serializovaného objektu SOAP, jak je znázorněno v následujícím kódu:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Nebo pomocí služby WCF namísto webových služeb ASP.NET:

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Ve všech těchto případech jsou modely hrozeb a záruky zabezpečení stejné jako v [části DataSet. ReadXml a DataTable. ReadXml](#dsrdtr).

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>Deserializace datové sady nebo objektu DataTable přes XmlSerializer

Vývojáři mohou použít `XmlSerializer` k deserializaci `DataSet` a `DataTable` instancí, jak je znázorněno v následujícím kódu:

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

V těchto případech jsou modely hrozeb a záruky zabezpečení stejné jako v [části DataSet. ReadXml a DataTable. ReadXml.](#dsrdtr)

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>Deserializace datové sady nebo objektu DataTable prostřednictvím JsonConvert

Oblíbená [Knihovna Newtonsoft](https://www.newtonsoft.com/json) třetí strany se dá použít k deserializaci `DataSet` a `DataTable` instancím, jak je znázorněno v následujícím kódu:

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Deserializace `DataSet` nebo `DataTable` tímto způsobem z nedůvěryhodného objektu BLOB JSON není bezpečná. Tento model je zranitelný vůči útokům DOS (Denial of Service). Takový útok může způsobit chybu aplikace nebo vykreslování, která neodpovídá.

> [!NOTE]
> Společnost Microsoft nezaručuje ani nepodporuje implementaci knihoven třetích stran, jako je _Newtonsoft.Js_. Tyto informace jsou k dispozici pro úplnost a jsou přesné v době psaní tohoto zápisu.

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>Deserializace datové sady nebo objektu DataTable prostřednictvím BinaryFormatter

`BinaryFormatter` `NetDataContractSerializer` `SoapFormatter` Pro ***unsafe*** deserializaci `DataSet` `DataTable` instance nebo z nedůvěryhodné datové části nesmějí vývojáři nikdy používat,, ani související nezabezpečené formátovací moduly:

* To je náchylné k úplnému útoku vzdáleného spuštění kódu.
* Použití vlastní není `SerializationBinder` dostačující k tomu, aby se zabránilo takovým útokům.

## <a name="safe-replacements"></a>Bezpečné náhrady

Pro aplikace, které:

* Přijměte `DataSet` nebo prostřednictvím koncového `DataTable` bodu protokolu SOAP. asmx nebo koncového bodu WCF.
* Deserializace nedůvěryhodných dat do instance `DataSet` nebo `DataTable` .

Zvažte nahrazení objektového modelu, který chcete použít [Entity Framework](/ef). Entity Framework:

* Je bohatě moderní rozhraní orientované na objekty, které může představovat relační data.
* Přináší [různorodý ekosystém](/ef/core/providers/) zprostředkovatelů databází, aby bylo možné snadno projektovat databázové dotazy pomocí vašich entity Frameworkch objektových modelů.
* Nabízí integrované ochrany při deserializaci dat z nedůvěryhodných zdrojů.

Pro aplikace, které používají `.aspx` koncové body SOAP, zvažte změnu těchto koncových bodů tak, aby používaly [WCF](/dotnet/framework/wcf/). Služba WCF je plně vybavená náhrada za `.asmx` webové služby. Koncové body WCF [je možné zveřejnit prostřednictvím protokolu SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) kvůli kompatibilitě se stávajícími volajícími.

## <a name="code-analyzers"></a>Analyzátory kódu

Pravidla zabezpečení analyzátoru kódu, která se spouštějí při kompilaci zdrojového kódu, mohou pomáhat najít ohrožení zabezpečení související s tímto problémem zabezpečení v jazyce C# a Visual Basic kódu. Microsoft. CodeAnalysis. FxCopAnalyzers je balíček NuGet analyzátorů kódu, který je distribuován v [NuGet.org](https://www.nuget.org/).

Přehled analyzátorů kódu najdete v tématu [Přehled analyzátorů zdrojového kódu](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).

Povolte následující pravidla Microsoft. CodeAnalysis. FxCopAnalyzers:

- [CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Nepoužívejte DataTable. ReadXml () s nedůvěryhodnými daty
- [CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Nepoužívejte DataSet. ReadXml () s nedůvěryhodnými daty
- [CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): nebezpečná datová sada nebo DataTable v serializovatelným typu může být zranitelná vůči útokům na vzdálené spuštění kódu.
- [CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): nebezpečná datová sada nebo DataTable v serializovatelným typu
- [CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): nebezpečná datová sada nebo DataTable v deserializovaném objektovém grafu může být zranitelná vůči útokům na vzdálené spuštění kódu.
- [CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): v grafu deserializovatelných objektů se našel nezabezpečená datová sada nebo typ DataTable.
- [CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): nebezpečná datová sada nebo typ DataTable ve webovém deserializaci objektu grafu
- [CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ujistěte se, že automaticky vygenerovaná třída obsahující DataSet. ReadXml () se nepoužívá s nedůvěryhodnými daty.
- [CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): nebezpečná datová sada nebo DataTable v automaticky generovaném serializovatelným typu může být zranitelná proti útokům na vzdálené spuštění kódu.

Další informace o konfiguraci pravidel najdete v tématu [použití analyzátorů kódu](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).

Nová pravidla zabezpečení jsou k dispozici v následujících balíčcích NuGet:

- Microsoft. CodeAnalysis. FxCopAnalyzers 3.3.0: pro Visual Studio 2019 verze 16,3 nebo novější
- Microsoft. CodeAnalysis. FxCopAnalyzers 2.9.11: pro Visual Studio 2017 verze 15,9 nebo novější
