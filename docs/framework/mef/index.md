---
title: Managed Extensibility Framework (MEF)
description: Prozkoumejte Managed Extensibility Framework (MEF), která vývojářům aplikací umožňuje zjišťovat a používat rozšíření bez konfigurace v rozhraní .NET 4 nebo vyšší.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 00ed48f2202d4c04039ac264b1fe71474a02432e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281248"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

V tomto tématu najdete přehled Managed Extensibility Framework představených v .NET Framework 4.

## <a name="what-is-mef"></a>Co je MEF?

Managed Extensibility Framework nebo MEF je knihovna pro vytváření lehkých a rozšiřitelných aplikací. Umožňuje vývojářům aplikací zjišťovat a používat rozšíření bez nutnosti konfigurace. Také umožňuje vývojářům rozšíření snadno zapouzdřit kód a vyhnout se nekřehkým pevným závislostem. MEF neumožňuje znovu použít rozšíření v aplikacích, ale i napříč aplikacemi.

## <a name="the-problem-of-extensibility"></a>Problém rozšiřitelnosti

Představte si, že jste architekt velké aplikace, která musí poskytovat podporu pro rozšiřitelnost. Vaše aplikace musí zahrnovat potenciálně velký počet menších součástí a zodpovídá za jejich vytvoření a spuštění.

Nejjednodušším přístupem k problému je zahrnout komponenty jako zdrojový kód do vaší aplikace a volat je přímo z vašeho kódu. To má řadu zjevných nevýhod. Nejdůležitější je, že nemůžete přidávat nové komponenty bez změny zdrojového kódu, což je omezení, které může být přijatelné například pro webovou aplikaci, ale nefunguje v klientské aplikaci. Stejně problematický, možná nebudete mít přístup ke zdrojovému kódu pro součásti, protože můžou být vyvinuty třetími stranami a ze stejného důvodu je nemůžete jim dovolit přístup.

Mírně propracovanější přístup by byl poskytnutím rozšiřujícího bodu nebo rozhraní, aby bylo možné odsouhlasení mezi aplikací a jejími součástmi. V rámci tohoto modelu můžete zadat rozhraní, které může komponenta implementovat, a rozhraní API, které bude umožňovat interakci s vaší aplikací. Tím se vyřeší problém vyžadující přístup ke zdrojovému kódu, ale stále se jedná o vlastní problémy.

Vzhledem k tomu, že aplikace nemá žádnou kapacitu pro zjišťování komponent na vlastní, musí být stále výslovně jasné, které součásti jsou k dispozici a měly by být načteny. To se obvykle provádí explicitním registrací dostupných komponent do konfiguračního souboru. To znamená, že ujištění, že tyto součásti jsou správné a že se jedná o problém s údržbou, zejména pokud se jedná o koncového uživatele, nikoli vývojáře, který by se měl aktualizovat.

Kromě toho součásti nejsou schopny vzájemně komunikovat, s výjimkou pevně definovaných kanálů samotné aplikace. Pokud architekt aplikace nepředpokládal nutnost konkrétní komunikace, je obvykle nemožné.

Nakonec musí vývojáři komponent přijmout pevně závislou závislost na tom, jaké sestavení obsahuje rozhraní, které implementuje. Proto je obtížné použít komponentu ve více než jedné aplikaci a může také vytvořit problémy při vytváření testovacího rozhraní pro komponenty.

## <a name="what-mef-provides"></a>Jaké rozhraní MEF poskytuje

Namísto této explicitní registrace dostupných komponent poskytuje rozhraní MEF způsob, jak je zjistit implicitně, prostřednictvím *složení*. Komponenta MEF, která se označuje jako *součást*, deklarativně určuje jejich závislosti (známé jako *importy*) a jaké funkce (označované jako *Export*) zpřístupňují. Když je vytvořena část, modul kompozice MEF splní svůj import s tím, co je k dispozici z jiných částí.

Tento přístup řeší problémy popsané v předchozí části. Vzhledem k tomu, že součásti MEF deklarativně specifikují své možnosti, jsou zjistitelné za běhu, což znamená, že aplikace může využít části bez pevně zakódovaných odkazů nebo křehkých konfiguračních souborů. MEF umožňuje aplikacím vyhledat a prozkoumat části podle jejich metadat, aniž by bylo nutné je vytvořit nebo dokonce načíst jejich sestavení. V důsledku toho není nutné pečlivě určovat, kdy a jak se mají rozšíření načíst.

Kromě poskytnutých exportů může součást určit její importy, které budou vyplněny jinými částmi. To umožňuje komunikaci mezi součástmi, které nejsou pouze možné, ale jednoduché, a umožňuje dobrý faktoring kódu. Například služby společné na mnoho komponent lze rozdělit do samostatné části a snadno upravit nebo nahradit.

Vzhledem k tomu, že model MEF nepožaduje žádné pevné závislosti na konkrétním sestavení aplikace, umožňuje rozšíření znovu použít z aplikace do aplikace. To také usnadňuje vývoj testovacího vodiče nezávisle na aplikaci pro testování komponent rozšíření.

Rozšiřitelná aplikace napsaná pomocí rozhraní MEF deklaruje import, který může být vyplněn součástmi rozšíření, a může také deklarovat exporty, aby bylo možné vystavit aplikační služby pro rozšíření. Každá součást rozšíření deklaruje export a může také deklarovat import. Tímto způsobem jsou samotné součásti rozšíření automaticky rozšiřitelné.

## <a name="where-mef-is-available"></a>Kde je k dispozici MEF

MEF je nedílnou součástí .NET Framework 4 a je k dispozici všude, kde se používá .NET Framework. V klientských aplikacích můžete použít MEF, ať už používají model Windows Forms, WPF nebo jakoukoli jinou technologii, nebo v serverových aplikacích, které používají ASP.NET.

## <a name="mef-and-maf"></a>MEF a MAF

Předchozí verze .NET Framework představily spravované rozhraní doplňku (MAF), navržené tak, aby aplikacím umožnily izolaci a správu rozšíření. Zaměření na MAF je mírně vyšší než MEF, zaměřuje se na izolaci rozšíření a načítání a uvolňování sestavení, zatímco se rozhraní MEF zaměřuje na zjistitelnost, rozšiřitelnost a přenositelnost. Obě architektury fungují hladce a jedna aplikace může využít obojí.

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Ukázková aplikace

Nejjednodušší způsob, jak zjistit, co může MEF udělat, je sestavení jednoduché aplikace MEF. V tomto příkladu vytvoříte velmi jednoduchou kalkulačku s názvem SimpleCalculator. Cílem SimpleCalculator je vytvořit konzolovou aplikaci, která přijímá základní aritmetické příkazy ve formátu "5 + 3" nebo "6-2" a vrací správné odpovědi. Pomocí MEF budete moci přidat nové operátory beze změny kódu aplikace.

Úplný kód pro tento příklad si můžete stáhnout v [ukázce SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

> [!NOTE]
> Účelem SimpleCalculator je předvedení konceptů a syntaxe MEF, místo aby nutně poskytovala reálný scénář pro použití. Mnohé z aplikací, které by mohly těžit z mocniny MEF, jsou složitější než SimpleCalculator. Další podrobné příklady najdete v [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) na GitHubu.

- Chcete-li začít, v aplikaci Visual Studio vytvořte nový projekt konzolové aplikace a pojmenujte jej `SimpleCalculator` .

- Přidejte odkaz na `System.ComponentModel.Composition` sestavení, kde se nachází MEF.

- Otevřete *Module1. vb* nebo *program.cs* a přidejte `Imports` nebo `using` příkazy pro `System.ComponentModel.Composition` a `System.ComponentModel.Composition.Hosting` . Tyto dva obory názvů obsahují typy MEF, které budete potřebovat pro vývoj rozšiřitelné aplikace.

- Pokud používáte Visual Basic, přidejte `Public` klíčové slovo na řádek, který deklaruje `Module1` modul.

## <a name="composition-container-and-catalogs"></a>Kontejner a katalog kompozic

Základem modelu složení MEF je *kontejner kompozice*, který obsahuje všechny dostupné součásti a provádí složení. Složení je porovnáním s importy a exporty. Nejběžnější typ kontejneru kompozice je a použijete ho <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> pro SimpleCalculator.

Pokud používáte Visual Basic, přidejte veřejnou třídu s názvem `Program` v *Module1. vb*.

Přidejte následující řádek do `Program` třídy v *Module1. vb* nebo *program.cs*:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Aby bylo možné zjistit, jaké součásti jsou k dispozici, kontejnery kompozice využívají *katalog*. Catalog je objekt, který zpřístupňuje dostupné části z nějakého zdroje. MEF poskytuje katalogy pro zjišťování částí ze zadaného typu, sestavení nebo adresáře. Vývojáři aplikací můžou snadno vytvářet nové katalogy a zjišťovat části z jiných zdrojů, například webové služby.

Do třídy přidejte následující konstruktor `Program` :

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

Volání, které <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> oznamuje kontejneru kompozice pro sestavení konkrétní sady částí, v tomto případě aktuální instance `Program` . V tuto chvíli se ale nic nestane, protože `Program` nemá žádné importy k vyplnění.

## <a name="imports-and-exports-with-attributes"></a>Import a export s atributy

Nejdřív jste `Program` importovali kalkulačku. To umožňuje oddělení kalkulačky, jako je vstup z konzoly a výstup, který se bude týkat `Program` , z logiky kalkulačky.

Do třídy přidejte následující kód `Program` :

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

Všimněte si, že deklarace `calculator` objektu není neobvyklé, ale je upravena <xref:System.ComponentModel.Composition.ImportAttribute> atributem. Tento atribut deklaruje něco pro import; To znamená, že bude modul sestavování vyplněn modulem složení, pokud je objekt sestaven.

Každý import má *kontrakt*, který určuje, s jakými exporty bude odpovídat. Kontrakt může být explicitně zadaný řetězec nebo může být automaticky vygenerován pomocí MEF z daného typu, v tomto případě rozhraní `ICalculator` . Tento import bude plnit jakýkoli export deklarovaný s vyhovující smlouvou. Všimněte si, že zatímco typ `calculator` objektu je ve skutečnosti `ICalculator` , není to vyžadováno. Kontrakt je nezávislý na typu importovaného objektu. (V tomto případě můžete opustit `typeof(ICalculator)` . MEF bude automaticky předpokládat, že kontrakt bude založen na typu importu, pokud ho explicitně neurčíte.)

Přidejte toto velmi jednoduché rozhraní do modulu nebo `SimpleCalculator` oboru názvů:

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

Teď, když jste definovali `ICalculator` , potřebujete třídu, která ji implementuje. Přidejte následující třídu do modulu nebo `SimpleCalculator` oboru názvů:

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

Tady je export, který bude odpovídat importu v `Program` . Aby export odpovídal importu, musí mít export stejný kontrakt. Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` by způsobil neshodu a import nebude vyplněn. kontrakt musí přesně odpovídat.

Vzhledem k tomu, že kontejner kompozice bude naplněn všemi částmi dostupnými v tomto sestavení, bude `MySimpleCalculator` část k dispozici. Když konstruktor pro `Program` provede složení `Program` objektu, jeho import se vyplní `MySimpleCalculator` objektem, který se vytvoří pro tento účel.

Vrstva uživatelského rozhraní ( `Program` ) nemusí znát žádné jiné. Z tohoto důvodu můžete v metodě vyplnit zbývající část logiky uživatelského rozhraní `Main` .

Do metody `Main` přidejte následující kód:

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Tento kód jednoduše přečte řádek vstupu a zavolá `Calculate` funkci `ICalculator` na výsledek, která se zapisuje zpátky do konzoly. To je veškerý kód, který potřebujete v `Program` . Veškerá zbývající část práce nastane v částech.

## <a name="further-imports-and-importmany"></a>Další import a ImportMany

Aby SimpleCalculator bylo rozšiřitelné, musí importovat seznam operací. Obyčejný <xref:System.ComponentModel.Composition.ImportAttribute> atribut je vyplněn jedním a pouze jedním <xref:System.ComponentModel.Composition.ExportAttribute> . Pokud je k dispozici více než jeden, modul kompozice vytvoří chybu. Chcete-li vytvořit import, který může být vyplněn libovolným počtem exportů, můžete použít <xref:System.ComponentModel.Composition.ImportManyAttribute> atribut.

Do třídy přidejte následující vlastnost Operations `MySimpleCalculator` :

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<xref:System.Lazy%602>je typ poskytnutý MEF pro uchování nepřímých odkazů na export. Zde, kromě exportovaných objektů, také získáte *metadata exportu*nebo informace, které popisují exportovaný objekt. Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt představující skutečnou operaci a `IOperationData` objekt, který představuje jeho metadata.

Do modulu nebo oboru názvů přidejte následující jednoduchá rozhraní `SimpleCalculator` :

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 V tomto případě je metadata pro každou operaci symbol, který představuje tuto operaci, například +,-, \* a tak dále. K zpřístupnění operace sčítání přidejte do modulu nebo `SimpleCalculator` oboru názvů následující třídu:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<xref:System.ComponentModel.Composition.ExportAttribute>Atribut funguje jako dříve. <xref:System.ComponentModel.Composition.ExportMetadataAttribute>Atribut připojí metadata v podobě páru název-hodnota k tomuto exportu. I když `Add` Třída implementuje `IOperation` , třída, která implementuje, není `IOperationData` explicitně definována. Místo toho je třída implicitně vytvořena pomocí MEF s vlastnostmi na základě názvů poskytnutých metadat. (Toto je jeden z několika způsobů, jak získat přístup k metadatům v MEF.)

Složení v rozhraní MEF je *rekurzivní*. Explicitně jste seřadíte `Program` objekt, který importoval `ICalculator` typ, který je vypnulý, aby byl typu `MySimpleCalculator` . `MySimpleCalculator`, následně importuje kolekci `IOperation` objektů a tento import bude vyplněn při `MySimpleCalculator` Vytvoření, ve stejnou dobu jako při importu `Program` . Pokud `Add` Třída deklarovala další import, je nutné ji vyplnit a tak dále. Všechny naimportované nevyplnit výsledky v důsledku chyby složení. (Je však možné deklarovat importy jako volitelné nebo přiřadit výchozí hodnoty.)

## <a name="calculator-logic"></a>Logika kalkulačky

Spolu s těmito částmi jsou všechny tyto součásti stále logikou kalkulačky. Do třídy přidejte následující kód `MySimpleCalculator` , který implementuje `Calculate` metodu:

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

Počáteční kroky analyzují vstupní řetězec na levý a pravý operand a znak operátoru. Ve `foreach` smyčce `operations` je zkontrolován každý člen kolekce. Tyto objekty jsou typu <xref:System.Lazy%602> a jejich hodnoty metadat a exportovaný objekt jsou k dispozici s <xref:System.Lazy%602.Metadata%2A> vlastností a <xref:System.Lazy%601.Value%2A> vlastností v uvedeném pořadí. V tomto případě, pokud `Symbol` `IOperationData` je zjištěna shoda vlastnosti objektu, kalkulačka volá `Operate` metodu `IOperation` objektu a vrátí výsledek.

K dokončení kalkulačky je také potřeba pomocná metoda, která vrací pozici prvního nenumerického znaku v řetězci. Do třídy přidejte následující pomocnou metodu `MySimpleCalculator` :

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

Nyní byste měli být schopni zkompilovat a spustit projekt. V Visual Basic nezapomeňte přidat `Public` klíčové slovo do `Module1` . V okně konzoly zadejte operaci sčítání, například "5 + 3", a kalkulačka vrátí výsledky. Jakýkoli jiný operátor má za následek, že operace nebyla nalezena! .

## <a name="extending-simplecalculator-using-a-new-class"></a>Rozšíření SimpleCalculator pomocí nové třídy

Teď, když Kalkulačka funguje, je přidání nové operace snadné. Přidejte následující třídu do modulu nebo `SimpleCalculator` oboru názvů:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

Zkompilujte a spusťte projekt. Zadejte operaci odčítání, například "5-3". Kalkulačka teď podporuje odčítání a navíc.

## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozšíření SimpleCalculator pomocí nového sestavení

Přidávání tříd do zdrojového kódu je dostatečně snadné, ale rozhraní MEF poskytuje možnost podívat se mimo vlastní zdroj aplikace pro části. K tomu je nutné upravit SimpleCalculator pro hledání adresáře a také jeho vlastní sestavení, pro součásti přidáním <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> .

Přidejte nový adresář s názvem `Extensions` do projektu SimpleCalculator. Nezapomeňte ho přidat na úrovni projektu, a ne na úrovni řešení. Pak přidejte nový projekt knihovny tříd do řešení s názvem `ExtendedOperations` . Nový projekt se zkompiluje do samostatného sestavení.

Otevřete Návrhář vlastností projektu pro projekt ExtendedOperations a klikněte na kartu **kompilovat** nebo **sestavit** . Změňte **výstupní cestu sestavení** nebo **výstupní cestu** tak, aby odkazovaly na adresář rozšíření v adresáři projektu SimpleCalculator (*.. \SimpleCalculator\Extensions \\ *).

 V *Module1. vb* nebo *program.cs*přidejte do konstruktoru následující řádek `Program` :

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

Nahraďte příklad cesty cestou k adresáři rozšíření. (Tato absolutní cesta je určena pouze pro účely ladění. V produkční aplikaci byste použili relativní cestu.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>Teď přidá všechny části, které se nacházejí v jakýchkoli sestaveních v adresáři rozšíření, do kontejneru kompozice.

V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System. ComponentModel. kompozici. V souboru třídy ExtendedOperations přidejte `Imports` `using` příkaz nebo pro System. ComponentModel. kompozici. V Visual Basic také přidejte `Imports` příkaz pro SimpleCalculator. Pak přidejte následující třídu do souboru třídy ExtendedOperations:

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

Všimněte si, že aby se kontrakt shodoval, <xref:System.ComponentModel.Composition.ExportAttribute> atribut musí mít stejný typ jako <xref:System.ComponentModel.Composition.ImportAttribute> .

Zkompilujte a spusťte projekt. Otestujte nové rozhraní mod (%) podnikatel.

## <a name="conclusion"></a>Závěr

Toto téma se zabývá základními koncepty rozhraní MEF.

- Části, katalogy a kontejner kompozice

     Části a kontejner skládání jsou základní stavební kameny aplikace MEF. Součást je libovolný objekt, který importuje nebo exportuje hodnotu, a to až do a včetně samotného. Katalog poskytuje kolekci částí z konkrétního zdroje. Kontejner kompozice používá části poskytované katalogem k provedení složení, vazby importů do exportů.

- Importy a exporty

     Importy a exporty představují způsob, jakým komponenty komunikují. V případě importu Tato součást Určuje potřebu konkrétní hodnoty nebo objektu a s exportem určuje dostupnost hodnoty. Každý import se shoduje se seznamem exportů podle jejich smlouvy.

## <a name="next-steps"></a>Další kroky

Úplný kód pro tento příklad si můžete stáhnout v [ukázce SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

 Další informace a příklady kódu naleznete v tématu [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Seznam typů MEF naleznete v <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.
