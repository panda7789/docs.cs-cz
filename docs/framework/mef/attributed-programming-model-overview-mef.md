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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09eb37fd2c1bf77e981a2eb7952b1fff5110e977
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872375"
---
# <a name="attributed-programming-model-overview-mef"></a>Přehled modelu programování s přidělenými atributy (MEF)

V Managed Extensibility Framework (MEF), *programovací model* je konkrétní metoda definuje sadu rámcové objekty, na kterých pracuje MEF. Mezi tyto rámcové objekty patří částí, importy a exporty. MEF používá tyto objekty, ale není zadán, jak by měly být zastoupeny. Proto jsou celou řadu programovacích modelů je to možné, včetně přizpůsobit programovacích modelů.

Výchozí hodnota je programovací model používaný v MEF *model programování s atributy*. V části s atributy programovací model jsou definovány importy, exporty a dalších objektů s atributy, které uspořádání běžné třídy rozhraní .NET Framework. Toto téma vysvětluje, jak používat atributy poskytované modelu programování s atributy k vytvoření aplikace MEF.

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a>Import a Export základy

*Exportovat* je hodnota, která obsahuje část s ostatními částmi v kontejneru, a *importovat* je požadavek, který vyjadřuje část do kontejneru, vyplní se z dostupných exportů. V modelu programování s atributy importy a exporty jsou deklarovány přidáním upravení třídy nebo členy s `Import` a `Export` atributy. `Export` Atribut můžete uspořádání třída, pole, vlastnost nebo metoda, zatímco `Import` atribut můžete uspořádání parametr pole, vlastnost nebo konstruktor.

Pro import lze porovnat s export, import a export musí mít stejné *kontraktu*. Smlouva se skládá z řetězce, volá se *název kontraktu*a typ objektu importovaná nebo exportovaná, volá se *typ kontraktu*. Pouze v případě, že název kontraktu i smlouva zadejte shoda se export považuje za splnit konkrétní importu.

Jeden nebo oba parametry smlouvy může být implicitní nebo explicitní. Následující kód ukazuje třídu, která deklaruje základní import.

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

V tomto importu `Import` atribut nemá typ kontraktu ani parametr název kontraktu připojen. Proto i se odvodit z upravené vlastnosti. V takovém případě budou mít typ kontraktu `IMyAddin`, a název smlouvy bude jedinečný řetězec vytvořený z typ kontraktu. (Jinými slovy, název smlouvy budou odpovídat jenom exporty, jejichž názvy jsou také odvodit z typu `IMyAddin`.)

Následuje ukázka export, který odpovídá předchozí import.

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

V tomto export, zajišťujeme typ kontraktu je `IMyAddin` vzhledem k tomu, že je zadán jako parametr `Export` atribut. Exportovaný typ musí být buď stejná jako typ kontraktu, odvozen od typu kontraktu nebo implementovat typ kontraktu, pokud se jedná o rozhraní. V tomto exportu, skutečný typ `MyLogger` implementuje rozhraní `IMyAddin`. Název smlouvy je odvozen z typu smlouvy, což znamená, že tento export bude odpovídat předchozí import.

> [!NOTE]
> Exportuje a importuje by měl obvykle deklarované v veřejné třídy nebo členy. Další deklarace jsou podporované, ale export nebo import privátní, chráněné nebo interní člen přeruší modelu izolace pro část a není proto doporučuje.

Typ kontraktu musí odpovídat přesně pro export a import být považovány za shodné. Vezměte v úvahu následující exportu.

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

V tomto export, zajišťujeme typ kontraktu je `MyLogger` místo `IMyAddin`. I když `MyLogger` implementuje `IMyAddin`a proto může být přetypovat na `IMyAddin` objektu, export nebudou odpovídat předchozí importovat, protože typy kontraktů nejsou stejné.

Obecně platí není potřeba zadávat název kontraktu a většina kontrakty by měl definovány jako typ kontraktu a metadata. Za určitých okolností, je potřeba zadat název kontraktu přímo. Nejběžnější případ je, když třída exportuje několik hodnot, které sdílejí společný typ, jako je například primitiv. Název smlouvy lze zadat jako první parametr `Import` nebo `Export` atribut. Následující kód ukazuje, import a export s názvem zadaného smlouvy `MajorRevision`.

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

Pokud není zadán typ kontraktu, bude stále odvozen z typu importu nebo exportu. Ale i v případě, že je explicitně zadán název kontraktu, typ kontraktu musí také odpovídat přesně pro import a export být považovány za shodné. Například pokud `MajorRevision` bylo pole řetězce, typy kontraktů odvozený shodě a export shodě import, přes který má stejný název kontraktu.

### <a name="importing-and-exporting-a-method"></a>Import a export metodu

`Export` Atribut může také uspořádání metody, stejně jako třída, vlastnost nebo funkce. Metoda exporty musíte zadat název kontraktu a typ kontraktu jako typ nelze odvodit. Zadaný typ může být vlastního delegáta nebo obecného typu, například `Func`. Následující třídy exportuje metodu s názvem `DoSomething`.

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

V této třídě `DoSomething` metoda přebírá jediný `int` parametr a vrátí `string`. Tak, aby odpovídaly export, import část musí deklarovat příslušného člena. Následující třídy importy `DoSomething` metody.

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

Další informace o tom, jak používat nástroje `Func<T, T>` objektu, najdete v článku <xref:System.Func%602>.

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a>Typy importy

Několik import MEF podporují typy, včetně dynamických, opožděné požadované a volitelné.

### <a name="dynamic-imports"></a>Dynamické importy

V některých případech může být vhodné importu třídy tak, aby odpovídaly exporty libovolného typu, které mají název konkrétní kontraktu. V tomto scénáři můžete deklarovat třídy *dynamického importu*. Následující import odpovídá jakékoli export s názvem kontraktu "TheString".

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

Kdy typu kontraktu je odvozen z `dynamic` – klíčové slovo, budou se shodovat s libovolný typ kontraktu. V takovém případě by měl importu **vždy** zadejte název smlouvy tak, aby odpovídaly na. (Pokud není zadán žádný název smlouvy, import bude považovat za tak, aby odpovídaly žádné exporty.) Obě tyto exporty odpovídá předchozí import.

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

Samozřejmě musí být připravené třídu importu se objekt libovolného typu.

### <a name="lazy-imports"></a>Opožděné importy

V některých případech importu třídy vyžadují nepřímý odkaz na importovaný objekt tak, aby se okamžitě vytvořena instance objektu. V tomto scénáři můžete deklarovat třídy *opožděné import* pomocí typu kontraktu `Lazy<T>`. Následující vlastnost importu deklaruje opožděné importu.

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

Z hlediska složení modulu, typu kontraktu `Lazy<T>` se považuje za stejný jako typ kontraktu `T`. Proto se předchozí import odpovídají následujícího exportu.

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

Název kontraktu a typ smlouvy lze zadat v `Import` atributu opožděné import, jak je popsáno výše v části "Základní importy a exporty".

### <a name="prerequisite-imports"></a>Požadované importy

Kompoziční modul v reakci na žádost o přímé nebo nutnosti tak, aby vyplnil odpovídající import obvykle vytváří exportované částmi MEF. Ve výchozím nastavení se při vytvoření části Kompoziční modul používá konstruktor bez parametrů. Chcete-li modul, použijte jiný konstruktor, můžete označit ji `ImportingConstructor` atribut.

Každá část může mít pouze jeden konstruktor pro použití u Kompoziční modul. Žádný výchozí konstruktor a ne `ImportingConstructor` atribut nebo poskytuje více než jeden `ImportingConstructor` atribut, dojde k chybě.

Vyplnit parametry konstruktoru označeného klíčovým `ImportingConstructor` atribut, všechny tyto parametry jsou automaticky deklarován jako importy. Je to pohodlný způsob, jak deklarovat importy, které se používají při inicializaci části. Následující třídy používá `ImportingConstructor` pro deklaraci importu.

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Default constructor will NOT be used
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

    //Default constructor will NOT be
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

Ve výchozím nastavení `ImportingConstructor` atribut odvodit používá typy kontraktů a kontraktů pro všechny importy parametru. Je možné přepsat pomocí upravení parametrů pomocí `Import` atributy, které můžete pak určit typ kontraktu a název kontraktu explicitně. Následující kód ukazuje konstruktor, který používá tuto syntaxi pro import odvozenou třídu namísto nadřazené třídy.

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

Konkrétně byste měli být opatrní při práci s parametry kolekce. Pokud zadáte například `ImportingConstructor` na konstruktor s parametrem typu `IEnumerable<int>`, import bude odpovídat jeden export typu `IEnumerable<int>`, místo sady exporty typu `int`. Tak, aby odpovídaly sadu exporty typu `int`, máte k vyplnění parametr s `ImportMany` atribut.

Parametry deklarovány jako importy podle `ImportingConstructor` atribut jsou také označené jako *předpoklad importuje*. Obvykle umožňuje exporty MEF a naimportuje do formuláře *cyklu*. Cyklus je třeba where-object objekt A importů B, který zase importuje objekt A. Za běžných okolností cyklus nepředstavuje žádný problém a kontejner kompozic obvykle vytvoří oba objekty.

Když importované hodnoty je potřeba pomocí konstruktoru část, tento objekt se nemůže podílet na cyklus. Pokud objekt A vyžaduje zkonstruovat tento objekt B předtím, než lze sestavit samostatně a objekt B importuje objektu A pak cyklu nejde přeložit a dojde k chybě složení. Importy deklarované parametry konstruktoru jsou proto požadované importy, které musí všechny být vyplněno před žádné exporty z objektu, který vyžaduje, je použít.

### <a name="optional-imports"></a>Volitelné importy

`Import` Atribut určuje požadavek pro část funkce. Pokud nelze splnit, import, složení této části se nezdaří a části nebude k dispozici.

Můžete určit, že je import *volitelné* pomocí `AllowDefault` vlastnost. V takovém případě bude složení úspěšné i v případě, že import neodpovídá žádné dostupné exporty a importu vlastnost bude nastavena na výchozí hodnoty pro jeho vlastnost typ (`null` na vlastnosti objektu `false` pro logické hodnoty nebo nula pro číselné Vlastnosti.) Následující třídy používá volitelný import.

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

### <a name="importing-multiple-objects"></a>Import více objektů

`Import` Atribut bude být úspěšně tvořen pouze případě, že odpovídá pouze jeden export. Jindy ohlásí chybu kompozice. Chcete-li importovat víc než jeden export odpovídající stejný kontrakt, použijte `ImportMany` atribut. Importy označené pomocí tohoto atributu jsou vždy volitelné. Například složení nebude nezdaří, pokud jsou k dispozici žádné exporty odpovídající. Následující třídy importuje libovolný počet exportů typu `IMyAddin`.

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

Importované pole je přístupná pomocí běžných `IEnumerable<T>` syntaxi a metody. Je také možné použít běžné pole (`IMyAddin[]`) místo toho.

Tento model může být velmi důležité, když ho použijete v kombinaci s `Lazy<T>` syntaxe. Například s použitím `ImportMany`, `IEnumerable<T>`, a `Lazy<T>`, můžete importovat nepřímé odkazy na libovolný počet objektů a pouze ty, které budou potřebné instance. Následující třídy ukazuje tento model.

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

## <a name="avoiding-discovery"></a>Obcházení zjišťování

V některých případech můžete chtít zabránit zjišťování katalogu v rámci části. Části může být například základní třídu, má Zdědit z však nepoužívá. Existují dva způsoby, jak toho dosáhnout. Nejprve, můžete použít `abstract` – klíčové slovo ve třídě část. Abstraktní třídy nikdy poskytují exporty, i když mohou poskytovat zděděné exporty do třídy, které jsou odvozeny z nich.

Pokud nelze nastavit jako abstraktní třídu, můžete ji uspořádání `PartNotDiscoverable` atribut. Část upravené pomocí tohoto atributu se nezahrnuly do jakékoli katalogů. Následující příklad ukazuje tyto vzory. `DataOne` nebudou nalezeni funkcí katalogu. Protože `DataTwo` je abstraktní, zjišťování selže. Protože `DataThree` použít `PartNotDiscoverable` atributu, nebudou zjištěna.

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

Exporty můžou poskytnout další informace o samotné označované jako *metadat*. Metadata můžete použít k předání vlastnosti objektu exportované do části importu. Části importu můžete pomocí těchto dat se rozhodnout, který exportuje použití nebo shromažďovat informace o export bez nutnosti jeho vytvoření. Z tohoto důvodu musí být importu opožděné použití metadat.

Použití metadat, deklarujete obvykle označuje jako rozhraní *zobrazení metadat*, který deklaruje metadat jaký bude k dispozici. Rozhraní zobrazení metadat musí mít pouze vlastnosti, a tyto vlastnosti musí mít `get` přistupující objekty. Rozhraní následující je příklad zobrazení metadat.

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

Je také možné použít obecné kolekce `IDictionary<string, object>`, jako zobrazení metadat, ale to přichází výhody kontrolu typu a mělo by se vyhnout.

Obvykle jsou požadovány všechny vlastnosti v zobrazení metadat s názvem a žádné exporty, které se nevztahuje Smlouva je nesmí být považovány za shodné. `DefaultValue` Atribut určuje, že vlastnost je volitelná. Pokud je vlastnost neuvedete, se přiřadí výchozí hodnota zadaná jako parametr `DefaultValue`. Tady jsou dvě různé třídy upravené pomocí metadat. Obě tyto třídy by odpovídala na předchozí zobrazení metadat.

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

Metadata je vyjádřena po `Export` atribut s použitím `ExportMetadata` atribut. Každá část metadata se skládá z dvojice název/hodnota. Část názvu metadat musí odpovídat názvu příslušné vlastnosti v zobrazení metadat a hodnota se přiřadí dané vlastnosti.

Pokud existuje, bude používán je programu pro import, který určuje, jaké zobrazení metadat. Import metadat je deklarován jako opožděné import metadat rozhraní jako druhý parametr typu tím `Lazy<T,T>`. Následující třídy importuje předchozí části s metadaty.

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

V mnoha případech budete chtít kombinovat metadat se `ImportMany` atribut, aby bylo možné analyzovat prostřednictvím dostupné importy a zvolte a vytvořit pouze jednu instanci nebo filtrovat kolekce tak, aby odpovídaly určité podmínky. Tyto třídy vytvoří pouze instanci `IPlugin` objekty, které mají `Name` hodnotu "Logger".

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

## <a name="import-and-export-inheritance"></a>Import a Export dědičnosti

Pokud třída dědí z části, této třídy může být také součástí. Importy jsou vždy děděné podtřídy. Proto podtřídou třídy součástí bude vždy součástí, pomocí stejné importy jako své nadřazené třídy.

Exporty deklarovaná příkazem using `Export` nedědí atribut podtřídy. Ale součástí mohou exportovat samotného pomocí `InheritedExport` atribut. Podtřídy třídy části bude dědit a poskytovat stejné exportu, včetně názvu kontraktu a typ kontraktu. Na rozdíl od `Export` atribut `InheritedExport` lze použít pouze na úrovni třídy a ne na úrovni člena. Proto je možné zdědit nikdy exporty úrovně členu.

Následující čtyři třídy ukazují zásady import a export dědičnosti. `NumTwo` dědí z `NumOne`, takže `NumTwo` naimportuje `IMyData`. Běžné exporty nedědí, takže `NumTwo` nic nebude export. `NumFour` dědí z `NumThree`. Protože `NumThree` použít `InheritedExport`, `NumFour` má jeden export typu kontraktu `NumThree`. Nikdy dědí exporty úrovni člena, takže `IMyData` neexportoval.

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

Dojde-li metadata přidružené `InheritedExport` atribut, tato metadata se budou také dědit. (Další informace najdete v předchozí části "Metadata a zobrazení metadat".) Podtřídy nemůže upravit zděděné metadat. Ale deklarováním znovu `InheritedExport` atribut se stejným názvem kontraktu a typ smlouvy, ale s novými metadaty, podtřídy můžete nahradit zděděné metadat s novými metadaty. Následující třídy znázorňuje tento princip. `MegaLogger` Části dědí z `Logger` a zahrnuje `InheritedExport` atribut. Protože `MegaLogger` novými metadaty znovu deklaruje pojmenované stav, nedědí názvu a verze metadat z `Logger`.

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

Při opětovné deklarování `InheritedExport` atribut přetížení metadat, ujistěte se, že typy kontraktů jsou stejné. (V předchozím příkladu `IPlugin` je typ kontraktu.) Pokud se liší místo přepsání, druhý atribut se vytvoří druhé, nezávislé export z části. Obecně platí, to znamená, že je nutné explicitně zadat typ kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.

Protože rozhraní nelze přímo vytvořit instanci, jsou obecně nedá dekorovat `Export` nebo `Import` atributy. Rozhraní ale mohou být doplněny pomocí `InheritedExport` atribut na úrovni rozhraní, a že export spolu s související metadata zdědí všechny implementace třídy. Ale nebudou k dispozici v rámci samotným rozhraním.

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a>Export vlastních atributů

Atributy základní export `Export` a `InheritedExport`, je možné rozšířit na zahrnují metadata jako atribut vlastnosti. Tato technika je užitečná pro použití podobné metadat pro mnoho částí nebo vytváření strom dědičnosti atributů metadat.

Vlastní atribut můžete zadat typ smlouvy, název kontraktu nebo další metadata. Aby bylo možné definovat vlastní atribut třídu, která dědí z `ExportAttribute` (nebo `InheritedExportAttribute`) musí být doplněny pomocí `MetadataAttribute` atribut. Následující třídy definuje vlastní atribut.

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

Tato třída definuje vlastní atribut s názvem `MyAttribute` s typem kontraktu `IMyData` a některé metadat s názvem `MyMetadata`. Všechny vlastnosti v třídě označené `MetadataAttribute` atribut jsou považovány za definovaný ve vlastním atributu metadat. Jsou následující dvě deklarace ekvivalentní.

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

V první deklaraci typu kontraktu a metadata jsou explicitně definovány. V deklaraci druhý typ kontraktu a metadata jsou implicitní ve vlastní atribut. Zejména v případech, kde je nutné použít velké množství identické metadat na mnoho částí (například autora nebo informace o autorských právech) můžete pomocí vlastního atributu uložit spoustu času a replikace. Stromové struktury dědičnosti vlastních atributů lze dále umožňovat plánování.

Chcete-li vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut. Když tento atribut aplikován na vlastnost ve třídě vlastních atributů, určuje to, že dekorované vlastnost je volitelná a nebude muset zadávat Exportér. Pokud není zadána hodnota pro vlastnost, budou přiřazeny výchozí hodnotě pro jeho vlastnost typ (obvykle `null`, `false`, nebo 0.)

<a name="creation_policies"></a>

## <a name="creation-policies"></a>Vytvoření zásad

Když část určuje importu a skládání se provádí, kontejner kompozic se pokusí najít odpovídající exportu. Pokud úspěšně odpovídá importu se export, import člen je nastavený na instanci objektu exportované. Odkud pochází tato instance je řízen exportující část *vytváření zásad*.

Jsou dvě možné vytvoření zásady *sdílené* a *nesdílené*. Část zásadám vytváření sdílených se sdílí mezi každému importu v kontejneru pro část s touto smlouvou. Když Kompoziční modul najde shodu, musíme nastavit vlastnost importu ji jenom v případě, že již neexistuje, vytvoří instanci novou kopii části v opačném případě dodá stávající kopie. To znamená, že mnoho objektů může mít odkazy na stejné části. Tyto části neměli byste tedy spoléhat na vnitřní stav, který může být změněn z mnoha místech. Tyto zásady jsou vhodné pro statické části, náhradní díly, které poskytují služby a částí, které využívají velké množství paměti nebo jiných prostředků.

Část zásadám vytváření nesdílenými vytvoří pokaždé, když je nalezen odpovídající import pro jeden z jeho exporty. Nová kopie bude vytvořena instance proto ke každému importu v kontejneru, který odpovídá jednomu z části exportovaných kontraktů. Vnitřní stav tyto kopie nesmí sdílet. Tato zásada je vhodné pro části, kde každý import vyžaduje svou vlastní vnitřní stav.

Import a export můžete zadat zásady vytváření části, z hodnoty `Shared`, `NonShared`, nebo `Any`. Výchozí hodnota je `Any` pro obě importy a exporty. Export, který určuje `Shared` nebo `NonShared` bude porovnávat pouze importu, který určuje stejný nebo, který určuje `Any`. Podobně, import, který určuje `Shared` nebo `NonShared` bude porovnávat pouze export, který určuje stejný nebo, který určuje `Any`. Importy a exporty pomocí nekompatibilní vytváření zásad nejsou považovány za shodné, stejně jako import a export, jejíž název nebo smlouvy typ kontraktu nejsou odpovídající. Import a export zadání `Any`, nebo nezadávejte vytvoření zásad a ve výchozím nastavení `Any`, vytvoření zásady budou ve výchozím nastavení sdílené.

Následující příklad ukazuje importy a exporty určení zásad pro vytváření. `PartOne` neurčuje vytváření zásad, aby výchozí hodnota je `Any`. `PartTwo` neurčuje vytváření zásad, aby výchozí hodnota je `Any`. Vzhledem k tomu, jak importovat a exportovat výchozí `Any`, `PartOne` se bude sdílet. `PartThree` Určuje `Shared` vytváření zásad, takže `PartTwo` a `PartThree` budou sdílet stejnou kopii `PartOne`. `PartFour` Určuje `NonShared` vytváření zásad, takže `PartFour` bude nesdílené v `PartFive`. `PartSix` Určuje `NonShared` vytváření zásad. `PartFive` a `PartSix` obdrží každou samostatnou kopii `PartFour`. `PartSeven` Určuje `Shared` vytváření zásad. Protože neexistuje žádné exportované `PartFour` s zásady vytváření `Shared`, `PartSeven` import ničemu neodpovídá a není vyplněné.

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

## <a name="life-cycle-and-disposing"></a>Životní cyklus a připravuje se

Protože součásti jsou hostované v kontejner kompozic, může být složitější než běžné objekty svůj životní cyklus. Části mohou implementovat rozhraní dvě důležité týkající se životního cyklu: `IDisposable` a `IPartImportsSatisfiedNotification`.

Částí, které vyžadují práce, která musí provést vypnutí, dolů nebo které je třeba uvolnit prostředky by měly implementovat `IDisposable`, jako obvykle pro objekty rozhraní .NET Framework. Ale protože kontejneru vytvoří a spravuje odkazy na části, pouze kontejneru, který vlastní součástí by měly volat `Dispose` metoda na něj. Implementuje kontejner sám o sobě `IDisposable`a jako část jeho vyčištění v `Dispose` bude volat `Dispose` na všechny části, které vlastní. Z tohoto důvodu by měl vždy dispose kontejner kompozic, pokud už nepotřebujete a některé části, které vlastní.

Pro kontejnery s dlouhým poločasem rozpadu složení využití paměti podle části zásadám vytváření nesdílenými stát problémem. Tyto nesdílenými součástmi je možné vytvořit více než jednou a nebude odstraněn, dokud se kontejner sám o sobě je uvolněn. Nelze zpracovat takové, poskytuje kontejneru `ReleaseExport` metody. Voláním této metody na k exportu nesdílenými odstraní tento export z kontejner kompozic a zruší ho. Části, které jsou používány pouze odebrané exportu, a tak dále dolů stromu, se taky odeberou a odstraněn. Tímto způsobem můžou uvolnit prostředky bez uvolnění samotný kontejner složení.

`IPartImportsSatisfiedNotification` obsahuje jednu metodu s názvem `OnImportsSatisfied`. Tato metoda je volána kontejner kompozic v některé části, které implementují rozhraní, když dokončil složení a části importy jsou připravené k použití. Kompoziční modul tak, aby vyplnil importy z dalších částí vytvářejí částí. Importy z část jste nastavili, je nelze provést všechny inicializace, které spoléhá na nebo tyto hodnoty jste byla určena jako požadavky pomocí provádí úpravy importované hodnoty v konstruktoru část `ImportingConstructor` atribut. Toto je obvykle upřednostňovanou metodou, ale v některých případech nemusí být k dispozici prostřednictvím injektáže konstruktoru. V těchto případech je možné provádět inicializace `OnImportsSatisfied`, a měla by implementovat části `IPartImportsSatisfiedNotification`.

## <a name="see-also"></a>Viz také:

- [Video pro kanál 9: Otevřete aplikací pomocí Managed Extensibility Framework](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Video pro kanál 9: Rozhraní Managed Extensibility Framework (MEF) 2.0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
