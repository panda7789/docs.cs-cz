---
title: Přehled modelu programování s přidělenými atributy (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: c6b1093d2e821a55cc5513b077a270748a780b71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347632"
---
# <a name="attributed-programming-model-overview-mef"></a>Přehled modelu programování s přidělenými atributy (MEF)

V Managed Extensibility Framework (MEF) je *programovací model* specifickou metodou pro definování sady konceptuálních objektů, na kterých funguje MEF. Tyto koncepční objekty zahrnují součásti, importy a exporty. MEF používá tyto objekty, ale neurčuje, jak by měly být reprezentovány. Proto je možné využít širokou škálu programovacích modelů, včetně přizpůsobených programovacích modelů.

Výchozím programovacím modelem používaným v MEF je *model programování s atributy*. V částech modelu programování s atributy jsou importy, exporty a další objekty definovány s atributy, které upraví běžné .NET Framework třídy. V tomto tématu se dozvíte, jak pomocí atributů poskytovaných programovacím modelem s atributy vytvořit aplikaci MEF.

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a>Základy importu a exportu

*Export* je hodnota, kterou část poskytuje jiným částem v kontejneru a *Import* je požadavek, aby část, která je vyjádřena v kontejneru, byla vyplněna z dostupných exportů. V programovacím modelu s atributy jsou importy a exporty deklarovány pomocí tříd upravení nebo členů pomocí atributů `Import` a `Export`. Atribut `Export` může setřídět třídu, pole, vlastnost nebo metodu, zatímco atribut `Import` může setřídit pole, vlastnost nebo parametr konstruktoru.

Aby se import shodoval s exportem, musí mít import a export stejný *kontrakt*. Smlouva se skládá z řetězce, který se označuje jako *název kontraktu*a typ exportovaného nebo importovaného objektu, který se označuje jako *Typ kontraktu*. Pouze v případě, že shoda názvu kontraktu a typu smlouvy je exportem, který je považován za splnění konkrétního importu.

Buď nebo oba parametry kontraktu mohou být implicitní nebo explicitní. Následující kód ukazuje třídu, která deklaruje základní import.

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

V tomto importu nemá atribut `Import` žádný typ kontraktu ani připojený parametr názvu kontraktu. Proto obě budou odvozeny z dekorované vlastnosti. V takovém případě bude typ kontraktu `IMyAddin`a název kontraktu bude jedinečným řetězcem vytvořeným z typu kontraktu. (Jinými slovy, název kontraktu bude odpovídat pouze exportům, jejichž názvy jsou také odvozeny z typu `IMyAddin`.)

Následující příklad ukazuje export, který odpovídá předchozímu importu.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

V tomto exportu je typ kontraktu `IMyAddin`, protože je zadaný jako parametr `Export` atributu. Exportovaný typ musí být buď stejný jako typ kontraktu, odvozený od typu kontraktu, nebo implementovat typ kontraktu, pokud se jedná o rozhraní. V tomto exportu vlastní typ `MyLogger` implementuje rozhraní `IMyAddin`. Název kontraktu je odvozený od typu kontraktu, což znamená, že tento export bude odpovídat předchozímu importu.

> [!NOTE]
> Exporty a importy by měly být obvykle deklarovány ve veřejných třídách nebo členech. Další deklarace jsou podporovány, ale export nebo import privátního, chráněného nebo interního člena přerušuje model izolace pro danou část a proto se nedoporučuje.

Typ kontraktu se musí přesně shodovat s exportem a importem, aby se dalo považovat za shodu. Vezměte v úvahu následující export.

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

V tomto exportu se místo `IMyAddin``MyLogger` typ kontraktu. I když `MyLogger` implementuje `IMyAddin`a proto může být převedena na objekt `IMyAddin`, tento export nebude odpovídat předchozímu importu, protože typy kontraktů nejsou stejné.

Obecně není nutné zadávat název kontraktu a většina kontraktů by měla být definována v souvislosti s typem a metadaty kontraktu. Za určitých okolností je však důležité zadat název kontraktu přímo. Nejběžnějším případem je, že třída exportuje několik hodnot, které sdílejí společný typ, jako jsou primitivní. Název kontraktu lze zadat jako první parametr atributu `Import` nebo `Export`. Následující kód ukazuje import a export se zadaným názvem kontraktu `MajorRevision`.

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

Pokud není zadán typ kontraktu, bude stále odvozen od typu importu nebo exportu. Nicméně i v případě, že je název kontraktu zadán explicitně, musí se typ kontraktu přesně shodovat s importem a exportem, aby bylo možné považovat za shodu. Například pokud se pole `MajorRevision` jako řetězec, typy odvozených kontraktů se neshodují a export by neodpovídal importu, i když má stejný název kontraktu.

### <a name="importing-and-exporting-a-method"></a>Import a export metody

Atribut `Export` může také roztřídit metodu stejným způsobem jako třída, vlastnost nebo funkce. Exporty metod musí určovat typ kontraktu nebo název kontraktu, protože typ nelze odvodit. Zadaný typ může být buď vlastní delegát, nebo obecný typ, například `Func`. Následující třída exportuje metodu s názvem `DoSomething`.

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

V této třídě metoda `DoSomething` přijímá jeden parametr `int` a vrátí `string`. Aby bylo možné tento export vyhledat, musí součást importu deklarovat příslušného člena. Následující třída importuje metodu `DoSomething`.

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

Další informace o použití objektu `Func<T, T>` naleznete v tématu <xref:System.Func%602>.

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a>Typy importů

Rozhraní MEF podporují několik typů importu, včetně dynamického, opožděného, předpokladu a volitelného.

### <a name="dynamic-imports"></a>Dynamické importy

V některých případech je možné, že import třídy bude odpovídat exportům libovolného typu, který má konkrétní název kontraktu. V tomto scénáři třída může deklarovat *dynamický import*. Následující import odpovídá jakémukoli exportu s názvem kontraktu "TheString".

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

Pokud je typ kontraktu odvozen z klíčového slova `dynamic`, bude odpovídat jakémukoli typu kontraktu. V takovém případě by měl import **vždy** určovat název kontraktu, na kterém se bude shodovat. (Pokud není zadaný žádný název kontraktu, import se považuje za neodpovídající žádným exportům.) Oba následující exporty by odpovídaly předchozímu importu.

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

Import třídy musí být připravený k práci s objektem libovolného typu.

### <a name="lazy-imports"></a>Opožděné importy

V některých případech importovaná třída může vyžadovat nepřímý odkaz na importovaný objekt, aby se objekt nevytvořil okamžitě. V tomto scénáři třída může deklarovat *opožděný import* pomocí typu kontraktu `Lazy<T>`. Následující importovaná vlastnost deklaruje opožděný import.

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

Z hlediska modulu kompozice je typ kontraktu `Lazy<T>` považován za shodný s typem kontraktu `T`. Předchozí import proto odpovídá následujícímu exportu.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

Název kontraktu a typ kontraktu lze zadat v atributu `Import` pro opožděné importy, jak je popsáno výše v části "základní import a export".

### <a name="prerequisite-imports"></a>Import požadovaných součástí

Exportované části MEF jsou obvykle vytvářeny modulem složení, a to v reakci na přímý požadavek nebo na nutnost vyplnit odpovídající import. Ve výchozím nastavení používá modul kompozice při vytváření součásti konstruktor bez parametrů. Chcete-li, aby modul používal jiný konstruktor, můžete jej označit atributem `ImportingConstructor`.

Každá část může mít pouze jeden konstruktor pro použití modulem složení. Pokud neposkytnete žádné konstruktory bez parametrů ani atribut `ImportingConstructor` ani zadáním více než jednoho atributu `ImportingConstructor`, dojde k chybě.

Chcete-li vyplnit parametry konstruktoru označeného atributem `ImportingConstructor`, všechny tyto parametry jsou automaticky deklarovány jako import. Toto je pohodlný způsob, jak deklarovat importy, které se používají při inicializaci části. Následující třída používá `ImportingConstructor` k deklaraci importu.

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

Ve výchozím nastavení používá atribut `ImportingConstructor` odvozený typ kontraktu a názvy kontraktů pro všechny importy parametrů. To lze přepsat upravení parametrů pomocí atributů `Import`, které mohou následně definovat typ kontraktu a název kontraktu explicitně. Následující kód demonstruje konstruktor, který používá tuto syntaxi k importu odvozené třídy namísto nadřazené třídy.

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

Konkrétně byste měli být opatrní s parametry kolekce. Například pokud zadáte `ImportingConstructor` v konstruktoru s parametrem typu `IEnumerable<int>`, import bude odpovídat jedinému exportu typu `IEnumerable<int>`namísto sady EXPORTS typu `int`. Chcete-li porovnat sadu exportů typu `int`, je nutné zadat parametr s atributem `ImportMany`.

Parametry deklarované jako Imports pomocí atributu `ImportingConstructor` jsou také označeny jako *požadované importy*. MEF normálně umožňuje exportům a importům vytvořit *cyklus*. Například cyklus je místo, kde objekt A importuje objekt B, který zase importuje objekt A. Za běžných okolností není cyklem problém a kontejner kompozice vytvoří oba objekty normálně.

Pokud je importovaná hodnota požadována konstruktorem součásti, tento objekt se nemůže zúčastnit cyklu. Pokud objekt A vyžaduje, aby byl objekt B vytvořen před samotným sestavením a objekt B importuje objekt A, pak se cyklus nebude moci vyřešit a dojde k chybě kompozice. Importy deklarované v parametrech konstruktoru jsou tedy požadavky na importy, které musí být vyplněny před jakýmkoli exportem z objektu, který je vyžaduje, aby je bylo možné použít.

### <a name="optional-imports"></a>Volitelné importy

Atribut `Import` určuje požadavek, který má součást fungovat. Pokud import nelze splnit, složení této součásti selže a součást nebude k dispozici.

Pomocí vlastnosti `AllowDefault` můžete určit, že import je *nepovinný* . V tomto případě bude kompozice úspěšná i v případě, že import neodpovídá žádnému dostupnému exportu a vlastnost import bude nastavena na výchozí hodnotu pro svůj typ vlastnosti (`null` pro vlastnosti objektu, `false` pro logické hodnoty nebo nula pro číselné vlastnosti.) Následující třída používá volitelný import.

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a>Importování více objektů

Atribut `Import` bude úspěšně sestaven pouze v případě, že odpovídá jednomu a pouze jednomu exportu. Jiné případy vytvoří chybu složení. Chcete-li importovat více než jeden export, který odpovídá stejné smlouvě, použijte atribut `ImportMany`. Importy označené pomocí tohoto atributu jsou vždycky volitelné. Například složení nebude úspěšné, pokud nejsou k dispozici žádné vyhovující exporty. Následující třída importuje libovolný počet exportů typu `IMyAddin`.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

K importovanému poli lze přistupovat pomocí běžné `IEnumerable<T>` syntaxe a metod. Místo toho je také možné použít běžné pole (`IMyAddin[]`).

Tento model může být velmi důležitý při použití v kombinaci s syntaxí `Lazy<T>`. Například pomocí `ImportMany`, `IEnumerable<T>`a `Lazy<T>`, můžete importovat nepřímé odkazy na libovolný počet objektů a pouze vytvořit instance těch, které jsou nezbytné. Následující třída zobrazuje tento model.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a>Zamezení zjišťování

V některých případech můžete chtít zabránit tomu, aby se součást zjistila jako součást katalogu. Například část může být základní třídou, která má být zděděna z, ale není použita. To můžete provést dvěma způsoby. Nejprve můžete použít klíčové slovo `abstract` pro třídu Part. Abstraktní třídy nikdy neposkytují export, i když mohou poskytnout děděné exporty třídám, které jsou z nich odvozeny.

Pokud třídu nelze nastavit jako abstraktní, lze ji roztřídit pomocí atributu `PartNotDiscoverable`. Část upravená pomocí tohoto atributu nebude zahrnuta do žádných katalogů. Následující příklad znázorňuje tyto vzory. Katalog bude vyhledán `DataOne`. Vzhledem k tomu, že `DataTwo` je abstraktní, nebude zjištěno. Vzhledem k tomu, že `DataThree` používal atribut `PartNotDiscoverable`, nebude zjištěno.

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a>Metadata a zobrazení metadat

Exporty můžou poskytnout další informace o samotných údajích, které se nazývají *metadata*. Metadata lze použít k předávání vlastností exportovaného objektu do importované části. Importovaná část může pomocí těchto dat rozhodnout, které exporty se mají použít, nebo shromažďovat informace o exportu bez nutnosti jeho sestavení. Z tohoto důvodu musí být import opožděný, aby používal metadata.

Chcete-li použít metadata, obvykle deklarujete rozhraní známé jako *zobrazení metadat*, které deklaruje, jaká metadata budou k dispozici. Rozhraní zobrazení metadat musí mít pouze vlastnosti a tyto vlastnosti musí mít přistupující objekty `get`. Následující rozhraní je příkladem zobrazení metadat.

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

Je také možné použít obecnou kolekci, `IDictionary<string, object>`jako zobrazení metadat, ale to propadá na výhody kontroly typu a je třeba se jim vyhnout.

Obvykle jsou požadovány všechny vlastnosti pojmenované v zobrazení metadat a jakékoli exporty, které je neposkytují, nebudou považovány za shodu. Atribut `DefaultValue` určuje, že je vlastnost volitelná. Pokud není tato vlastnost zahrnutá, přiřadí se výchozí hodnota zadaná jako parametr `DefaultValue`. Níže jsou dvě různé třídy dekorované metadaty. Obě tyto třídy by odpovídaly předchozímu zobrazení metadat.

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

Metadata jsou vyjádřena za atributem `Export` pomocí atributu `ExportMetadata`. Každá část metadat se skládá z dvojice název/hodnota. Název v metadatech se musí shodovat s názvem příslušné vlastnosti v zobrazení metadat a hodnota bude přiřazena této vlastnosti.

Je to dovozce, který určuje, jaké zobrazení metadat se bude používat. Import s metadaty je deklarován jako opožděný import, s rozhraním metadat jako druhým parametrem typu pro `Lazy<T,T>`. Následující třída importuje předchozí část s metadaty.

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

V mnoha případech budete chtít kombinovat metadata s atributem `ImportMany`, aby bylo možné analyzovat v dostupných importech a vybírat a vytvářet instance pouze jeden, nebo filtrovat kolekci tak, aby odpovídala určité podmínce. Následující třída vytváří instance pouze `IPlugin` objekty, které mají `Name` hodnotu "protokolovací".

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a>Dědičnost importu a exportu

Pokud třída dědí z části, může se také stát, že se tato třída stane součástí. Importy jsou vždy děděny podtřídami. Proto bude podtřídou součásti vždy součástí, se stejnými importy jako její nadřazená třída.

Exporty deklarované pomocí atributu `Export` nejsou děděny podtřídami. Součást však může exportovat sebe sama pomocí atributu `InheritedExport`. Podtřídy této části zdědí a poskytnou stejný export, včetně názvu kontraktu a typu smlouvy. Na rozdíl od atributu `Export` lze `InheritedExport` použít pouze na úrovni třídy, nikoli na úrovni člena. Proto nelze export na úrovni členů dědění nikdy dědit.

Následující čtyři třídy demonstrují principy dědičnosti importu a exportu. `NumTwo` dědí z `NumOne`, takže `NumTwo` import `IMyData`. Běžné exporty nejsou děděny, takže `NumTwo` nebude něco exportovat. `NumFour` dědí z `NumThree`. Protože `NumThree` používá `InheritedExport`, `NumFour` má jeden export s typem kontraktu `NumThree`. Exporty na úrovni členů nejsou nikdy děděny, takže `IMyData` není exportován.

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

Pokud jsou k atributu `InheritedExport` přidružená metadata, budou tato metadata také zděděná. (Další informace najdete v části předchozí metadata a zobrazení metadat). Zděděná metadata nelze upravovat podtřídou. Když však znovu deklarujete atribut `InheritedExport` se stejným názvem kontraktu a typem kontraktu, ale s novými metadaty, podtřída může nahradit zděděná metadata novými metadaty. Následující třída demonstruje tento princip. `MegaLogger` část dědí z `Logger` a obsahuje atribut `InheritedExport`. Vzhledem k tomu, že `MegaLogger` znovu deklaruje nová metadata s názvem status, nedědí její název a metadata verze z `Logger`.

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

Při opětovné deklaraci atributu `InheritedExport` pro přepsání metadat se ujistěte, že typy kontraktu jsou stejné. (V předchozím příkladu je `IPlugin` typ kontraktu.) Pokud se liší, místo přepsání, druhý atribut vytvoří druhý nezávislý export z části. Obecně to znamená, že budete muset explicitně zadat typ kontraktu při přepsání atributu `InheritedExport`, jak je znázorněno v předchozím příkladu.

Vzhledem k tomu, že rozhraní nemohou být vytvořena přímo, nesmí být obecně upravena pomocí atributů `Export` nebo `Import`. Rozhraní lze však dekorovat pomocí atributu `InheritedExport` na úrovni rozhraní a tento export spolu s veškerými přidruženými metadaty bude děděn všemi implementací tříd. Samotné rozhraní nebude ale k dispozici jako součást.

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a>Vlastní atributy exportu

Základní atributy exportu `Export` a `InheritedExport`lze rozšířit tak, aby zahrnovaly metadata jako vlastnosti atributu. Tato technika je užitečná pro použití podobných metadat na mnoho částí nebo pro vytvoření stromu dědičnosti atributů metadat.

Vlastní atribut může určovat typ kontraktu, název kontraktu nebo jiná metadata. Aby bylo možné definovat vlastní atribut, musí být třída, která dědí z `ExportAttribute` (nebo `InheritedExportAttribute`), upravena atributem `MetadataAttribute`. Následující třída definuje vlastní atribut.

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

Tato třída definuje vlastní atribut s názvem `MyAttribute` s typem kontraktu `IMyAddin` a některá metadata s názvem `MyMetadata`. Všechny vlastnosti ve třídě označené atributem `MetadataAttribute` se považují za metadata definovaná ve vlastním atributu. Následující dvě deklarace jsou ekvivalentní.

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

V první deklaraci je typ kontraktu a metadata explicitně definovány. Ve druhé deklaraci je typ kontraktu a metadata implicitní v přizpůsobeném atributu. Zejména v případech, kdy je třeba použít velké množství identických metadat na mnoho částí (například informace o autorech nebo autorských právech), může použití vlastního atributu ušetřit spoustu času a duplikace. Kromě toho lze vytvořit stromy dědičnosti vlastních atributů, aby bylo možné variace.

Chcete-li vytvořit volitelná metadata ve vlastním atributu, můžete použít atribut `DefaultValue`. Pokud je tento atribut použit pro vlastnost ve vlastní třídě atributu, určuje, že dekorovaná vlastnost je volitelná a není nutné ji dodávat Exportér. Pokud hodnota vlastnosti není dodána, bude jí přiřazena výchozí hodnota pro svůj typ vlastnosti (obvykle `null`, `false`nebo 0).

<a name="creation_policies"></a>

## <a name="creation-policies"></a>Zásady vytváření

Pokud část určuje import a složení, kontejner kompozice se pokusí najít vyhovující export. Pokud odpovídá import s exportem úspěšně, je importovaný člen nastaven na instanci exportovaného objektu. Umístění, ze kterého pochází tato instance, je ovládáno pomocí *zásad vytváření*exportovaných částí.

Dvě možné zásady vytváření jsou *sdílené* a *nesdílené*. Součást s zásadou vytváření Shared bude sdílená mezi každým importem v kontejneru pro součást s touto smlouvou. Pokud modul kompozice najde shodu a musí nastavit vlastnost import, vytvoří instanci nové kopie součásti pouze v případě, že ještě neexistuje. v opačném případě poskytne existující kopii. To znamená, že mnoho objektů může mít odkazy na stejnou část. Tyto části by neměly spoléhat na vnitřní stav, který může být změněn z mnoha míst. Tyto zásady jsou vhodné pro statické části, součásti, které poskytují služby, a součásti, které využívají spoustu paměti nebo jiných prostředků.

Součást se zásadami vytváření nesdílených se vytvoří pokaždé, když se najde odpovídající import pro jeden z jeho exportů. Pro každý import v kontejneru, který odpovídá jedné z exportovaných smluv, bude vytvořena instance nového kopírování. Vnitřní stav těchto kopií nebude sdílen. Tyto zásady jsou vhodné pro části, kde každý import vyžaduje vlastní vnitřní stav.

Import i export mohou určovat zásadu vytváření součásti, a to z hodnot `Shared`, `NonShared`nebo `Any`. Výchozí hodnota je `Any` pro import i export. Export, který určuje `Shared` nebo `NonShared`, bude odpovídat pouze importu, který určuje stejný nebo který určuje `Any`. Podobně import, který určuje `Shared` nebo `NonShared`, bude odpovídat pouze exportu, které určuje stejné nebo které určuje `Any`. Importy a exporty s nekompatibilními zásadami vytváření nejsou považovány za shodu, a to stejným způsobem jako při importu a exportu, jejichž název kontraktu nebo typ kontraktu se neshodují. Pokud import i export specifikují `Any`nebo nezadáte zásadu vytváření a výchozí hodnotu `Any`, zásada vytváření se bude sdílet s výchozím nastavením.

Následující příklad ukazuje import i export, které určují zásady vytváření. `PartOne` neurčuje zásadu vytváření, takže výchozí hodnota je `Any`. `PartTwo` neurčuje zásadu vytváření, takže výchozí hodnota je `Any`. Vzhledem k tomu, že se naimportují i exportují výchozí hodnoty `Any`, `PartOne` sdílet. `PartThree` určuje zásadu vytváření `Shared`, takže `PartTwo` a `PartThree` budou sdílet stejnou kopii `PartOne`. `PartFour` určuje zásadu vytváření `NonShared`, takže `PartFour` nebudou sdíleny v `PartFive`. `PartSix` určuje zásadu vytváření `NonShared`. `PartFive` a `PartSix` získají samostatné kopie `PartFour`. `PartSeven` určuje zásadu vytváření `Shared`. Vzhledem k tomu, že není k dispozici žádná exportovaná `PartFour` se zásadami vytvoření `Shared`, `PartSeven` import se neshoduje s žádným a nebude vyplněn.

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a>Životní cyklus a odstraňování

Vzhledem k tomu, že části jsou hostovány v kontejneru složení, jejich životní cyklus může být složitější než běžné objekty. Části můžou implementovat dvě důležitá rozhraní související s životním cyklem: `IDisposable` a `IPartImportsSatisfiedNotification`.

Součásti, které vyžadují, aby se prováděla práce při vypnutí nebo potřebují uvolnit prostředky, by měly implementovat `IDisposable`, obvykle pro objekty .NET Framework. Vzhledem k tomu, že kontejner vytváří a udržuje odkazy na části, je nutné volat metodu `Dispose` pouze v kontejneru, který vlastní část. Kontejner sám implementuje `IDisposable`a jako část jeho vyčištění v `Dispose` bude volat `Dispose` na všech částech, které vlastní. Z tohoto důvodu byste měli kontejner kompozice vždy uvolnit, pokud je a jakékoliv součásti, které vlastní, již nepotřebujete.

V případě dlouhodobých kontejnerů kompozice se může stát, že spotřeba paměti podle částí se zásadou vytváření nesdíleného není sdílená. Tyto nesdílené části je možné vytvořit víckrát, takže nebudou uvolněny, dokud nedojde k uvolnění samotného kontejneru. V takovém případě kontejner poskytuje metodu `ReleaseExport`. Volání této metody u nesdíleného exportu odebere tento export z kontejneru složení a odstraní jej. Části, které se používají jenom odebraným exportem, a tak i na stromové struktuře, se taky odeberou a odstraňují. Tímto způsobem lze prostředky uvolnit bez likvidace kontejneru kompozice.

`IPartImportsSatisfiedNotification` obsahuje jednu metodu nazvanou `OnImportsSatisfied`. Tato metoda je volána kontejnerem kompozice na všech částech, které implementují rozhraní po dokončení složení, a importy části jsou připravené k použití. Části jsou vytvořeny modulem složení, aby bylo možné vyplnit importy dalších částí. Před nastavením importu části nelze provést žádnou inicializaci, která spoléhá na nebo zpracovává importované hodnoty v konstruktoru součásti, pokud tyto hodnoty nebyly zadány jako požadavky pomocí atributu `ImportingConstructor`. To je obvykle upřednostňovaná metoda, ale v některých případech nemusí být injektáže konstruktoru k dispozici. V těchto případech lze inicializaci provést v `OnImportsSatisfied`a část by měla implementovat `IPartImportsSatisfiedNotification`.

## <a name="see-also"></a>Viz také:

- [Video pro kanál 9: otevření aplikací pomocí Managed Extensibility Framework](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Video pro kanál 9: Managed Extensibility Framework (MEF) 2,0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
