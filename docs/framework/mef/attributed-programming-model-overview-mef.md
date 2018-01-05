---
title: "Přehled modelu programování s přidělenými atributy (MEF)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 565cd9384e150f707b2e5e72342579d95c3a096e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="attributed-programming-model-overview-mef"></a>Přehled modelu programování s přidělenými atributy (MEF)
V Managed Extensibility Framework (MEF), *programovací model* je konkrétní metoda definování sady koncepční objektů, na kterých pracuje MEF. Tyto rámcové objekty zahrnují části, import a export. MEF používá tyto objekty, ale neurčuje, jak by měly být zastoupeny. Proto je možné, včetně přizpůsobit programovací modely celou řadu programovacích modelů.  
  
 Výchozí hodnota je programovací model použitý v MEF *model programování s atributy*. V části s atributy programovací model import, export a jiné objekty jsou definovány s atributy, které uspořádání běžné třídy rozhraní .NET Framework. Toto téma vysvětluje, jak použít atributy poskytované model programování s atributy pro vytvoření aplikace MEF.  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>Import a Export základy  
 *Exportovat* je hodnota, která poskytuje součástí do dalších částí v kontejneru, a *importovat* je požadavek, který je součástí vyjadřoval do kontejneru, aby byla vyplněna z dostupných exporty. Ve model programování s atributy, import a export je deklarovaná architekturu třídy nebo členy s `Import` a `Export` atributy. `Export` Atributu můžete uspořádání třídu, pole, vlastnost nebo metoda, při `Import` atributu můžete uspořádání parametr pole, vlastnost nebo konstruktor.  
  
 Aby importu lze porovnat s exportu, import a export musí mít stejnou *kontrakt*. Smlouva se skládá z řetězec s názvem *název kontraktu*a typ objektu exportovanou nebo importované, volá se *typ kontraktu*. Pouze v případě, že název kontraktu i smlouva zadejte shodu považuje exportu splnit konkrétní importu.  
  
 Implicitním nebo explicitním, může být buď nebo oba parametry kontrakt. Následující kód ukazuje třídu, který deklaruje základní import.  
  
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
  
 V tomto importu `Import` atribut má typ smlouvy ani parametr název kontraktu připojen. Proto i bude odvodit z dekorované vlastnosti. V takovém případě bude typ smlouvy `IMyAddin`, a název kontraktu bude jedinečný řetězec vytvořený z typu kontraktu. (Jinými slovy, název kontraktu bude odpovídat jenom exportuje, jejichž názvy jsou také odvodit z typu `IMyAddin`.)  
  
 Následující obrázek znázorňuje exportu, který odpovídá předchozí importu.  
  
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
  
 V tento export je typ kontraktu `IMyAddin` vzhledem k tomu, že je zadán jako parametr `Export` atribut. Exportovaný typ musí být buď stejný jako typ smlouvy, jsou odvozeny od typu kontraktu nebo implementovat typ smlouvy, pokud je rozhraní. V této exportu, skutečný typ `MyLogger` implementuje rozhraní `IMyAddin`. Název smlouvy je odvozeno z typu kontraktu, což znamená, že tento export bude shodovat s předchozí importu.  
  
> [!NOTE]
>  Export a import by měl obvykle deklarovat na veřejné třídy nebo členy. Další deklarace jsou podporovány, ale exportu nebo importu privátního, chráněný, nebo vnitřní člen dělí model izolace pro část a proto se nedoporučuje.  
  
 Typ smlouvy musí odpovídat přesně exportu a importu do být považovány za shodné. Vezměte v úvahu následující exportu.  
  
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
  
 V tento export je typ kontraktu `MyLogger` místo `IMyAddin`. I když `MyLogger` implementuje `IMyAddin`a proto může být přetypovat `IMyAddin` objektu, tento export nebude odpovídat předchozí importovat, protože kontrakt typy nejsou stejné.  
  
 Obecně platí není nutné zadat název kontraktu a většina kontrakty by měl být definován jako typ smlouvy a metadata. Za určitých okolností, je potřeba zadat název kontraktu přímo. Nejběžnější případ je, když třída exportuje několik hodnot, které sdílejí společný typ, třeba primitiv. Název smlouvy lze zadat jako první parametr `Import` nebo `Export` atribut. Následující kód ukazuje importu a exportu s názvem zadaného kontrakt `MajorRevision`.  
  
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
  
 Pokud není zadán typ smlouvy, bude stále odvodit z typu import nebo export. Ale i v případě, že název smlouvy je explicitně zadané, typ kontraktu se taky musí shodovat přesně pro import a export do být považovány za shodné. Například pokud `MajorRevision` pole byl to řetězec, nebude odpovídající typy odvozené kontraktu a export nebude odpovídat import, přes který má stejný název kontraktu.  
  
### <a name="importing-and-exporting-a-method"></a>Import a export metody  
 `Export` Atributu můžete také uspořádání metodu, stejným způsobem jako třídu, vlastnost nebo funkce. Metoda Export třeba zadat typ smlouvy nebo název kontraktu jako typ nemůže být odvozený. Zadaný typ může být vlastní delegáta nebo obecného typu, například `Func`. Následující třídy exportuje metodu s názvem `DoSomething`.  
  
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
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 V této třídě `DoSomething` metoda přebírá jediný `int` parametr a vrátí `string`. Pro tento export shodu, je třeba deklarovat import část příslušného člena. Následující třídy importy `DoSomething` metoda.  
  
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
  
 Další informace o tom, jak použít `Func<T, T>` objektu, najdete v části <xref:System.Func%602>.  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>Typy importy  
 Podpory MEF několik importovat typy včetně dynamické opožděné, požadované a volitelné.  
  
### <a name="dynamic-imports"></a>Dynamické importy  
 V některých případech může chtít import třídy tak, aby odpovídaly exportuje libovolného typu, které mají název konkrétní kontraktu. V tomto scénáři můžou deklarovat třídy *dynamické import*. Následující importu odpovídá žádné exportu s název kontraktu "TheString".  
  
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
  
 Když je typ smlouvy odvodit z `dynamic` – klíčové slovo, se bude shodovat s jakýmikoli kontrakt. V takovém případě by měl importu **vždy** zadejte název kontraktu tak, aby odpovídala na. (Pokud není zadán žádný název kontraktu, import bude považovat za tak, aby odpovídaly žádným exportům.) Obě tyto exporty odpovídá předchozí importu.  
  
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
  
 Samozřejmě musí být import třída připraveno jak nakládat s objekt libovolného typu.  
  
### <a name="lazy-imports"></a>Opožděné importy  
 V některých případech může import – třída vyžadovat nepřímý odkaz na importovaný objekt tak, aby objekt není instanci okamžitě. V tomto scénáři můžou deklarovat třídy *opožděné import* pomocí typu kontraktu `Lazy<T>`. Následující import vlastnost deklaruje opožděné importu.  
  
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
  
 Z hlediska modulu složení, kontrakt typ `Lazy<T>` se považuje za identické smlouvy typ `T`. Proto předchozí importu odpovídá následující exportu.  
  
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
  
 V lze zadat název kontraktu a typ smlouvy `Import` atribut pro opožděné import, jak je popsáno výše v části "Základní import a export".  
  
### <a name="prerequisite-imports"></a>Požadovaný importy  
 Exportovaný částí rozhraní MEF se obvykle vytvářejí modul složení, v reakci na žádost o přímý nebo nutnosti zadejte odpovídající importu. Ve výchozím nastavení se při vytváření součástí používá modul složení konstruktor bez parametrů. Chcete-li modul použijte jiný konstruktor, můžete označit její `ImportingConstructor` atribut.  
  
 Jednotlivé části může mít pouze jeden konstruktor pro použití modul složení. Poskytnutí neexistoval výchozí konstruktor a ne `ImportingConstructor` atribut, nebo zadáním více než jeden `ImportingConstructor` atribut, vygeneruje chybu.  
  
 K vyplnění parametry konstruktor označené jako `ImportingConstructor` atribut všechny tyto parametry jsou automaticky deklarované jako importy. Toto je pohodlný způsob, jak deklarovat importy, které se používají během inicializace část. Následující třídy používá `ImportingConstructor` deklarovat importu.  
  
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
  
 Ve výchozím nastavení `ImportingConstructor` atribut používá odvozené typy kontraktů a smlouvy názvy pro všechny importy parametr. Je možné přepsat to tak, že architekturu parametry s `Import` atributy, které lze poté zadejte typ smlouvy a název kontraktu explicitně. Následující kód ukazuje konstruktor, který používá tuto syntaxi k importu do odvozené třídy místo nadřazené třídy.  
  
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
  
 Konkrétně byste měli být opatrní při práci s parametry kolekce. Pokud zadáte například `ImportingConstructor` na konstruktor s parametrem typu `IEnumerable<int>`, import bude odpovídat jedné export typu `IEnumerable<int>`, místo sadu exportuje typu `int`. Tak, aby odpovídaly sadu exportuje typu `int`, budete muset uspořádání parametr pomocí `ImportMany` atribut.  
  
 Parametry deklarován jako importy pomocí `ImportingConstructor` atribut jsou také označen jako *importuje požadovaných součástí*. MEF normálně umožňuje exportuje a naimportuje do formuláře *cyklus*. Cyklus. je třeba kde importy objektu A objekt B, který naopak importuje objekt A. Za běžných okolností cyklus se nejedná o problém a kontejneru složení vytvoří oba objekty normálně.  
  
 Když importované hodnotu vyžaduje konstruktoru součástí, tento objekt nemůže být součástí cyklický odkaz. Pokud objekt A vyžaduje, aby tento objekt B zkonstruovat před jde konstruovat samostatně a objekt B importuje objekt A potom na cyklus nelze vyřešit a dojde k chybě složení. Importy deklarovaná u konstruktor parametry jsou proto požadovaných importů, které musí všechny plnit před každý exporty z objektu, který vyžaduje je můžete použít.  
  
### <a name="optional-imports"></a>Volitelné importy  
 `Import` Atribut určuje požadavek pro část funkce. Pokud nelze splnit importu, složení této části se nezdaří a části nebudete mít k dispozici.  
  
 Můžete určit, že bude importu *volitelné* pomocí `AllowDefault` vlastnost. V takovém případě bude složení úspěšné i v případě, že import neodpovídá žádné dostupné export a import vlastnost bude nastavena na výchozí hodnoty pro typ vlastnosti (`null` pro vlastnosti objektu `false` pro logických výrazů nebo nula pro číselné Vlastnosti.) Následující třídy používá volitelné importu.  
  
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
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a>Import více objektů  
 `Import` Atribut bude pouze úspěšně skládat při odpovídá pouze jeden export. Ostatních případech vygeneruje chyba složení. Chcete-li importovat více než jeden export, který odpovídá stejné smlouvy, použijte `ImportMany` atribut. Importy označené jako tento atribut se vždycky volitelné. Pokud jsou k dispozici žádné odpovídající exportuje se například nebudou složení. Následující třídy importuje libovolný počet exportuje typu `IMyAddin`.  
  
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
  
 Importované pole je přístupná pomocí obyčejnou `IEnumerable<T>` syntaxe a metody. Je také možné použít obyčejnou pole (`IMyAddin[]`) místo.  
  
 Tento vzor může být velmi důležité, pokud ji použít v kombinaci s `Lazy<T>` syntaxe. Například pomocí `ImportMany`, `IEnumerable<T>`, a `Lazy<T>`, můžete importovat nepřímé odkazy na libovolný počet objektů a pouze ty, které se stanou nezbytnými doložit. Následující třídy ukazuje tento vzor.  
  
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
 V některých případech můžete chtít zabránit části zjišťovat v rámci katalogu. Část může být například základní třída má od doby, ale nepoužívá se. Existují dva způsoby, jak dosáhnout. První, můžete použít `abstract` – klíčové slovo k třídě část. Abstraktní třídy nikdy zadejte exportuje, i když poskytují zděděné export do tříd, které vycházejí z nich.  
  
 Pokud nemůže být provedena abstraktní třídu, můžete ho s uspořádání `PartNotDiscoverable` atribut. Součástí označených pomocí tento atribut nebude součástí žádné katalogů. Následující příklad ukazuje tyto vzory. `DataOne`Najde katalogu. Protože `DataTwo` je abstraktní, se nebudou vyhledány. Vzhledem k tomu `DataThree` použít `PartNotDiscoverable` atribut, nebudou vyhledány.  
  
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
 Export může poskytovat další informace o samotné známé jako *metadata*. Metadata slouží k předání informací o tom vlastnosti objektu exportovaný import část. Tyto údaje můžete použít pro import část rozhodnout, který exportuje používat nebo shromažďovat informace o exportu bez nutnosti jej vytvořit. Z tohoto důvodu musí být importu opožděné používat metadata.  
  
 Použít metadata, je obvykle deklarovat rozhraní nazývá *zobrazení metadat*, který deklaruje, jaká metadata bude k dispozici. Rozhraní metadat zobrazení musí mít pouze vlastnosti, a musí mít tyto vlastnosti `get` přistupující objekty. Následující rozhraní je zobrazení příkladu metadat.  
  
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
  
 Je také možné použít kolekci Obecné `IDictionary<string, object>`, jako zobrazení metadat, ale tím o výhody kontrola typu a je nutno.  
  
 Normálně všechny vlastnosti s názvem v zobrazení metadata jsou povinné a žádné export, které je neposkytují nebude být považovány za shodné. `DefaultValue` Atribut určuje, že vlastnost je volitelná. Pokud vlastnost není součástí, bude jí přiřazeno výchozí hodnota zadaná jako parametr funkce `DefaultValue`. Níže jsou uvedeny dva různé třídy dekorované s metadaty. Obě tyto třídy odpovídá předchozí zobrazení metadat.  
  
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
  
 Metadata se vyjadřuje po `Export` atribut pomocí `ExportMetadata` atribut. Každá část metadat se skládá z dvojice název/hodnota. Část názvu metadat musí odpovídat názvu příslušné vlastnosti v zobrazení metadat a hodnota se přiřadí této vlastnosti.  
  
 Pokud existuje, bude používán je – Importér, která určuje, jaké zobrazení metadat. Importu s metadaty je deklarován jako opožděné importu rozhraní metadat jako druhý parametr typu `Lazy<T,T>`. Následující třídy importuje předchozí část s metadaty.  
  
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
  
 V řadě případů budete chtít kombinovat metadat pomocí `ImportMany` atribut, aby bylo možné analyzovat prostřednictvím dostupné importy a vyberte a vytvořit pouze jednu instanci nebo filtrování kolekce splňují určité podmínky. Následující třídy vytvoří pouze `IPlugin` objekty, které mají `Name` hodnotu "Protokolovač".  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
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
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a>Import a Export dědičnosti  
 Pokud třídy dědí z části, této třídy může také stát součástí. Importy jsou vždy zděděny podtřídy. Proto podtřídou třídy součástí budou vždy částí, s stejné importy jako své nadřazené třídy.  
  
 Exportuje deklarovat pomocí `Export` atribut nejsou zdědí podtřídy. Však součástí můžete exportovat samotné pomocí `InheritedExport` atribut. Podtřídy části bude dědit a zadejte stejné exportu, včetně názvu kontraktu a typ smlouvy. Na rozdíl od `Export` atribut `InheritedExport` lze použít pouze na úrovni třídy a nikoli na úrovni člena. Proto může být zděděna nikdy exportuje úrovni člena.  
  
 Následující čtyři třídy předvedení zásady importu a exportu dědičnosti. `NumTwo`dědí z `NumOne`, takže `NumTwo` naimportuje `IMyData`. Obyčejnou exportuje nedědí, takže `NumTwo` nebude nic exportovat. `NumFour`dědí z `NumThree`. Protože `NumThree` používá `InheritedExport`, `NumFour` má jeden exportu s typ smlouvy `NumThree`. Nikdy dědí exportuje úrovni člena, takže `IMyData` neexportoval.  
  
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
  
 Pokud je metadata přidružená `InheritedExport` atribut, aby metadata také zděděná. (Další informace najdete v části "Metadata a zobrazení metadat" starší.) Zděděné metadata nelze změnit pomocí podtřídy. Ale deklarováním znovu `InheritedExport` atribut se stejným názvem kontraktu a typ smlouvy, ale s novými metadaty podtřídy můžete nahradit zděděné metadata novými metadaty. Následující třídy ukazuje této zásady. `MegaLogger` Část dědí z `Logger` i `InheritedExport` atribut. Vzhledem k tomu `MegaLogger` novými metadaty znovu deklaruje s názvem stav, nedědí název a verze metadata z `Logger`.  
  
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
  
 Když znovu deklarace `InheritedExport` atribut přepsat metadata, ujistěte se, že typy kontraktů jsou stejné. (V předchozím příkladu `IPlugin` je typ kontraktu.) Pokud se liší, místo přepsání, druhý atribut vytvoří druhý, nezávislé export z části. Obecně platí, to znamená, že budete mít k explicitnímu zadání typu kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.  
  
 Vzhledem k tomu, že rozhraní nemůže být přímo vytvořeny instance, se obecně nemůže být doplněny pomocí `Export` nebo `Import` atributy. Ale rozhraní může být doplněny pomocí `InheritedExport` atribut na úrovni rozhraní, a že export společně s žádné přidružená metadata zdědí všechny implementující třídy. Ale nebudete mít k dispozici v rámci rozhraní sám sebe.  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>Export vlastních atributů  
 Atributy základní export `Export` a `InheritedExport`, je možné rozšířit na obsahovat metadata jako atribut vlastnosti. Tato metoda je užitečná pro použití podobné metadata pro mnoho částí nebo vytváření ve stromu dědičnosti metadata atributů.  
  
 Vlastní atribut můžete určit typ smlouvy, název kontraktu nebo další metadata. Aby bylo možné definovat vlastní atribut, která dědí z třídy `ExportAttribute` (nebo `InheritedExportAttribute`) musí být doplněny pomocí `MetadataAttribute` atribut. Následující třídy definuje vlastní atribut.  
  
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
  
 Tato třída definuje vlastní atribut s názvem `MyAttribute` s typem kontraktu `IMyData` a některé metadat s názvem `MyMetadata`. Všechny vlastnosti v třídě označené jako `MetadataAttribute` atribut se považují za metadata definované ve vlastním atributu. Následující dva deklarace jsou ekvivalentní.  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 V první deklaraci typu kontraktu a metadata jsou explicitně definovány. V druhé deklaraci typu kontraktu a metadata jsou implicitní ve vlastní atribut. Zvláště v případech, kdy musí být velké množství identické metadata používá pro mnoho částí (například autora nebo informace o autorských právech) můžete pomocí vlastní atribut uložit spoustu času a duplicita. Navíc dědičnosti stromy vlastních atributů vytvořením umožňující variace.  
  
 Pokud chcete vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut. Když tento atribut se použije k vlastnosti ve třídě vlastních atributů, určuje to, že dekorované vlastnost je volitelná a nemá být poskytl exportu. Pokud není zadána hodnota pro vlastnost, bude jí přiřazeno výchozí hodnota pro typ vlastnosti (obvykle `null`, `false`, nebo 0.)  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>Vytvoření zásad  
 Když součást určuje importu a složení se provádí, kontejneru složení se pokusí najít odpovídající export. Pokud ho importovat s exportu odpovídá úspěšně, import člen je nastavena na instanci exportovaný objektu. Kde se tato instance pochází z řídí export části *vytvoření zásad*.  
  
 Jsou dvě možné vytvoření zásady, které *sdílené* a *nesdílené*. Součástí zásadám vytváření sdílených bude možné sdílet mezi každých importu v kontejneru pro část s tohoto kontraktu. Pokud modul složení najde shoda a má nastavit vlastnost import, ji pouze v případě, že již neexistuje, vytvoří instanci novou kopii části jinak poskytne existující kopie. To znamená, že mnoho objektů, může mít odkazy na stejnou část. Tyto části neměli spoléhat na vnitřní stav, který může být změněn z mnoha místech. Tato zásada je vhodné pro statické části, částí, které poskytují služby a částí, které využívají velké množství paměti nebo jiných prostředků.  
  
 Část zásadám vytváření nesdílené vytvoří pokaždé, když je nalezen odpovídající import jednoho z jeho export. Nové kopie bude vytvořena instance proto pro každý import v kontejneru, který odpovídá jednomu z exportovaný kontrakty pro část. Vnitřní stav tyto kopie se sdílet nebude. Tato zásada je vhodná pro části, kde každý importu vyžaduje vlastní vnitřní stav.  
  
 Import a export můžete zadat zásady vytváření druhé, některé z těchto hodnot `Shared`, `NonShared`, nebo `Any`. Výchozí hodnota je `Any` pro obě importuje a exportuje. Exportu, která určuje `Shared` nebo `NonShared` bude odpovídá pouze importu stejné, nebo určuje určující `Any`. Podobně, která určuje importu `Shared` nebo `NonShared` bude odpovídá pouze exportu stejné, nebo určuje určující `Any`. Import a export zásadám nekompatibilní vytvoření nejsou považovány za shodné, stejným způsobem jako import a export, jejíž název nebo kontrakt typ smlouvy nejsou shody. Pokud import a export zadat `Any`, nebo nezadávejte vytvoření zásad a výchozí `Any`, vytvoření zásady, bude použita výchozí sdílet.  
  
 Následující příklad ukazuje, import a export zadání vytvoření zásady. `PartOne`neurčuje vytvoření zásady, takže výchozí hodnota je `Any`. `PartTwo`neurčuje vytvoření zásady, takže výchozí hodnota je `Any`. Vzhledem k tomu, jak importovat a exportovat výchozí nastavení `Any`, `PartOne` budou sdílet. `PartThree`Určuje `Shared` vytvoření zásady, takže `PartTwo` a `PartThree` budou sdílet stejnou kopii `PartOne`. `PartFour`Určuje `NonShared` vytvoření zásady, takže `PartFour` bude nesdílené v `PartFive`. `PartSix`Určuje `NonShared` vytváření zásad. `PartFive`a `PartSix` obdrží každou samostatnou kopii `PartFour`. `PartSeven`Určuje `Shared` vytváření zásad. Protože je ne exportovat `PartFour` s vytvoření zásady `Shared`, `PartSeven` import neodpovídá nic a nesmí být vyplněna.  
  
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
    'Since the export's creation policy was explictly  
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
    //Since the export's creation policy was explictly  
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
## <a name="life-cycle-and-disposing"></a>Životní cyklus a uvolnění  
 Vzhledem k součásti jsou hostované v kontejneru složení, může být složitější než obyčejnou objekty jejich životního cyklu. Části můžete implementovat dvě důležité rozhraní související s životní cyklus: `IDisposable` a `IPartImportsSatisfiedNotification`.  
  
 Částí, které vyžadují, aby se provést na vypnutí dolů nebo které potřebujete k uvolnění prostředků by měla implementovat `IDisposable`, pro objekty rozhraní .NET Framework jako obvykle. Ale vzhledem k tomu, že kontejner vytvoří a udržuje odkazy na části, pouze kontejneru, který vlastní část by měly volat `Dispose` metoda na něm. Implementuje kontejneru samotné `IDisposable`a jako část jeho vyčištění v `Dispose` bude volat `Dispose` na všechny části, které je vlastní. Z tohoto důvodu by měl vždycky dispose kontejneru složení, když ho a částí, které vlastní už nejsou potřeba.  
  
 Pro kontejnery dlohotrvající složení částí zásadám vytváření nesdílené spotřeba paměti se může stát problém. Tyto části nesdílené lze vytvořit více než jednou a nebude uvolněno, dokud je zveřejněn kontejneru sám sebe. Zpracovat takové, poskytuje kontejner `ReleaseExport` metoda. Voláním této metody na export nesdíleného odebere tento export z kontejneru složení a zruší ho. Částí, které jsou používány pouze odebrané exportu, a tak dále hlouběji ve stromové struktuře, se taky odeberou a zlikvidován. Tímto způsobem se nedá uvolnit prostředky bez uvolnění kontejneru složení sám sebe.  
  
 `IPartImportsSatisfiedNotification`obsahuje jednu metodu s názvem `OnImportsSatisfied`. Tato metoda je volána kontejneru složení na všechny části, které implementují rozhraní při dokončení složení a rámci importy jsou připravené k použití. Části jsou vytvořené pomocí modulu složení k vyplnění importy dalších částí. Před importy části byly nastaveny, nelze provést všechny inicializace, který využívá nebo manipuluje importované hodnoty v rámci konstruktoru, pokud tyto hodnoty mají byl zadán jako požadavky pomocí `ImportingConstructor` atribut. To je obvykle upřednostňovanou metodou, ale v některých případech vkládání konstruktor nemusí být k dispozici. V takových případech lze provést inicializaci v `OnImportsSatisfied`, a měly by implementovat části `IPartImportsSatisfiedNotification`.  
  
## <a name="see-also"></a>Viz také  
 [Video Channel 9: Otevře aplikace s použitím spravovaných rozšíření Framework](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [Video Channel 9: Spravovaných rozšíření Framework (MEF) 2.0](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
