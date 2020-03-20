---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181290"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Toto téma obsahuje přehled spravovaného rozhraní rozšiřitelnosti, který byl zaveden v rozhraní .NET Framework 4.

## <a name="what-is-mef"></a>Co je MEF?

Spravované rozhraní rozšiřitelnosti nebo MEF je knihovna pro vytváření lehkých a rozšiřitelných aplikací. Umožňuje vývojářům aplikací zjišťovat a používat rozšíření bez nutnosti konfigurace. Umožňuje také vývojářům rozšíření snadno zapouzdřit kód a vyhnout se křehkým pevným závislostem. MEF umožňuje nejen rozšíření, které mají být znovu použity v rámci aplikací, ale napříč aplikacemi stejně.

## <a name="the-problem-of-extensibility"></a>Problém rozšiřitelnosti

Představte si, že jste architekt emitované velké aplikace, která musí poskytovat podporu pro rozšiřitelnost. Aplikace musí obsahovat potenciálně velký počet menších součástí a je zodpovědný za jejich vytváření a spouštění.

Nejjednodušší přístup k problému je zahrnout součásti jako zdrojový kód ve vaší aplikaci a volat je přímo z vašeho kódu. To má řadu zjevných nevýhod. A co je nejdůležitější, nelze přidat nové součásti bez úpravy zdrojového kódu, omezení, které může být přijatelné, například webové aplikace, ale je nefunkční v klientské aplikaci. Stejně problematické je, že pravděpodobně nemáte přístup ke zdrojovému kódu komponent, protože mohou být vyvinuty třetími stranami a ze stejného důvodu jim nemůžete povolit přístup k vašim.

O něco sofistikovanější přístup by bylo poskytnout rozšíření bodu nebo rozhraní, aby oddělení mezi aplikací a jeho součástí. V rámci tohoto modelu můžete poskytnout rozhraní, které může implementovat součást a rozhraní API, které jí umožní interakci s vaší aplikací. To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má své vlastní potíže.

Vzhledem k tomu, že aplikace postrádá žádnou kapacitu pro zjišťování součástí samostatně, musí být stále explicitně sděleny, které součásti jsou k dispozici a měly by být načteny. To se obvykle provádí explicitní registrací dostupných součástí v konfiguračním souboru. To znamená, že zajištění správné součásti se stane problém údržby, zejména v případě, že je koncový uživatel a nikoli vývojář, který se očekává, že aktualizace.

Kromě toho součásti nejsou schopny komunikovat mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotné aplikace. Pokud architekt aplikace nepředpokládá potřebu konkrétní komunikace, je to obvykle nemožné.

Nakonec vývojáři komponent musí přijmout tvrdou závislost na tom, jaké sestavení obsahuje rozhraní, které implementují. To ztěžuje součást, která má být použita ve více než jedné aplikaci a může také způsobit problémy při vytváření testovacího rámce pro součásti.

## <a name="what-mef-provides"></a>Co MEF poskytuje

Namísto této explicitní registrace dostupných komponent, MEF poskytuje způsob, jak objevit implicitně, prostřednictvím *složení*. Komponenta MEF, nazývaná *část*, deklarativně určuje jak své závislosti (označované jako *importy),* tak jaké možnosti (označované jako *exporty)* zpřístupňuje. Při vytvoření součásti kompoziční motor MEF splňuje své importy s tím, co je k dispozici z jiných částí.

Tento přístup řeší problémy popsané v předchozí části. Vzhledem k tomu, že součásti MEF deklarativně určují své možnosti, jsou zjistitelné za běhu, což znamená, že aplikace může využívat součásti bez pevně zakódovaných odkazů nebo křehkých konfiguračních souborů. MEF umožňuje aplikacím zjišťovat a zkoumat součásti podle jejich metadat, aniž by byly konkretizovat nebo dokonce načítat jejich sestavení. V důsledku toho není nutné pečlivě určit, kdy a jak by měla být načtena rozšíření.

Kromě poskytnutých vývozů může část specifikovat své dovozy, které budou vyplněny jinými částmi. Díky komunikaci mezi částmi je nejen možná, ale i snadná a umožňuje dobré faktoring kódu. Například služby společné pro mnoho součástí mohou být započítány do samostatného dílu a snadno upraveny nebo nahrazeny.

Vzhledem k tomu, že model MEF nevyžaduje žádnou tvrdou závislost na konkrétním sestavení aplikace, umožňuje rozšíření opakovaně z aplikace do aplikace. To také usnadňuje vývoj testovacího svazku, nezávisle na aplikaci, na testování rozšiřujících komponent.

Rozšiřitelná aplikace napsaná pomocí MEF deklaruje import, který lze vyplnit komponenty rozšíření a může také deklarovat exporty za účelem vystavení aplikačních služeb rozšířením. Každá komponenta rozšíření deklaruje export a může také deklarovat importy. Tímto způsobem jsou komponenty rozšíření automaticky rozšiřitelné.

## <a name="where-mef-is-available"></a>Kde je MEF k dispozici

MEF je nedílnou součástí rozhraní .NET Framework 4 a je k dispozici všude, kde se používá rozhraní .NET Framework. Mef můžete použít v klientských aplikacích, ať už používají Windows Forms, WPF nebo jakoukoli jinou technologii nebo v serverových aplikacích, které používají ASP.NET.

## <a name="mef-and-maf"></a>MEF a MAF

Předchozí verze rozhraní .NET Framework zavedly rozhraní Managed Add-in Framework (MAF), které umožňuje aplikacím izolovat a spravovat rozšíření. Zaměření MAF je o něco vyšší úroveň než MEF, se zaměřením na rozšíření izolace a montáž zatížení a vykládky, zatímco MEF se zaměřuje na zjistitelnost, rozšiřitelnost a přenositelnost. Tyto dva rámce hladce spolupracují a jedna aplikace může využít obojí.

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Ukázková aplikace

Nejjednodušší způsob, jak zjistit, co MEF může udělat, je vytvořit jednoduchou aplikaci MEF. V tomto příkladu vytvoříte velmi jednoduchou kalkulačku s názvem SimpleCalculator. Cílem SimpleCalculator je vytvořit konzolovou aplikaci, která přijímá základní aritmetické příkazy ve tvaru "5+3" nebo "6-2" a vrací správné odpovědi. Pomocí MEF budete moci přidat nové operátory beze změny kódu aplikace.

Chcete-li stáhnout úplný kód pro tento příklad, naleznete [simplecalculator ukázka (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

> [!NOTE]
> Účelem SimpleCalculator je demonstrovat koncepty a syntaxe MEF, spíše než nutně poskytnout realistický scénář pro jeho použití. Mnoho aplikací, které by nejvíce těžit z výkonu MEF jsou složitější než SimpleCalculator. Podrobnější příklady najdete v tématu [spravované rozšiřitelnost i framework](https://github.com/MicrosoftArchive/mef) na GitHubu.

- Chcete-li začít, vytvořte v sadě Visual `SimpleCalculator`Studio nový projekt konzolové aplikace a pojmenujte jej .

- Přidejte odkaz `System.ComponentModel.Composition` na sestavení, kde mef sídlí.

- Otevřete *modul1.vb* nebo `Imports` `using` *Program.cs* `System.ComponentModel.Composition` a `System.ComponentModel.Composition.Hosting`přidejte nebo příkazy pro a . Tyto dva obory názvů obsahují typy MEF, které budete potřebovat k vývoji rozšiřitelné aplikace.

- Pokud používáte Visual Basic, `Public` přidejte klíčové slovo na `Module1` řádek, který deklaruje modul.

## <a name="composition-container-and-catalogs"></a>Kontejner složení a katalogy

Jádrem modelu složení MEF je *kompozice kontejneru*, který obsahuje všechny díly k dispozici a provádí složení. Složení je sladění dovozu s vývozem. Nejběžnější typ kontejneru složení <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>je a budete používat pro SimpleCalculator.

Pokud používáte Visual Basic, přidejte `Program` veřejnou třídu s názvem v *Module1.vb*.

Přidejte následující řádek `Program` do třídy v *Module1.vb* nebo *Program.cs*:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Aby bylo možné zjistit části, které má k dispozici, kontejnery složení využívá *katalogu*. Katalog je objekt, který zpřístupňuje součásti zjištěné z některého zdroje. MEF poskytuje katalogy ke zjišťování částí z poskytnutého typu, sestavení nebo adresáře. Vývojáři aplikací mohou snadno vytvářet nové katalogy a zjišťovat součásti z jiných zdrojů, například z webové služby.

Přidejte do třídy `Program` následující konstruktor:

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

Volání říká <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> kompozice kontejneru sestavit určitou sadu částí, v tomto `Program`případě aktuální instance . V tomto okamžiku se však `Program` nic nestane, protože nemá žádný dovoz k vyplnění.

## <a name="imports-and-exports-with-attributes"></a>Importy a exporty s atributy

Nejprve máte `Program` import kalkulačku. To umožňuje oddělení uživatelského rozhraní obavy, jako je například vstup konzoly a výstup, který bude přecházet do `Program`, z logiky kalkulačky.

Do `Program` třídy přidejte následující kód:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

Všimněte si, `calculator` že deklarace objektu není neobvyklé, <xref:System.ComponentModel.Composition.ImportAttribute> ale že je zdoben atributem. Tento atribut deklaruje něco jako import; to znamená, že bude vyplněna modul složení při skládání objektu.

Každý import má *smlouvu*, která určuje, s jakým exportem bude spárován. Kontrakt může být explicitně zadaný řetězec, nebo může být automaticky generován MEF z `ICalculator`daného typu, v tomto případě rozhraní . Každý export deklarovaný s odpovídající smlouvou splní tento import. Všimněte si, že `calculator` zatímco typ `ICalculator`objektu je ve skutečnosti , to není nutné. Smlouva je nezávislá na typu importujícího objektu. (V tomto případě můžete vynechat `typeof(ICalculator)`. MEF automaticky předpokládá, že smlouva bude založena na typu importu, pokud ji výslovně nezadáte.)

Přidejte toto velmi jednoduché `SimpleCalculator` rozhraní do modulu nebo oboru názvů:

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

Nyní, když `ICalculator`jste definovali , budete potřebovat třídu, která ji implementuje. Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:

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

Zde je export, který bude `Program`odpovídat importu v . Aby export odpovídal importu, musí mít export stejnou smlouvu. Vývoz na základě smlouvy `typeof(MySimpleCalculator)` založené na by vytvořil nesoulad a dovoz by nebyl vyplněn; smlouva musí přesně odpovídat.

Vzhledem k tomu, že kontejner složení bude naplněn `MySimpleCalculator` všemi díly dostupnými v této sestavě, bude díl k dispozici. Když konstruktor `Program` pro provádí `Program` složení na objekt, jeho `MySimpleCalculator` import bude vyplněn objektem, který bude vytvořen pro tento účel.

Vrstva uživatelského`Program`rozhraní ( ) nemusí vědět nic jiného. Proto můžete vyplnit zbytek logiky uživatelského `Main` rozhraní v metodě.

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

 Tento kód jednoduše přečte řádek `Calculate` vstupu `ICalculator` a volá funkci na výsledek, který zapíše zpět do konzoly. To je veškerý kód, `Program`který potřebujete v . Všechny ostatní práce se budou odehrávat v částech.

## <a name="further-imports-and-importmany"></a>Další dovozy a importMnoho

Aby SimpleCalculator být rozšiřitelný, je třeba importovat seznam operací. Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut je vyplněn jedním <xref:System.ComponentModel.Composition.ExportAttribute>a pouze jedním . Pokud je k dispozici více než jeden, modul složení vytvoří chybu. Chcete-li vytvořit import, který lze vyplnit libovolným <xref:System.ComponentModel.Composition.ImportManyAttribute> počtem exportů, můžete použít atribut.

Přidejte do `MySimpleCalculator` třídy následující vlastnost operations:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<xref:System.Lazy%602>je druh poskytnutý MEF pro uložení nepřímých odkazů na vývoz. Zde kromě samotného exportovaného objektu získáte také *metadata exportu*nebo informace popisující exportovaný objekt. Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt představující skutečnou operaci `IOperationData` a objekt představující jeho metadata.

Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující jednoduchá rozhraní:

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

 V tomto případě metadata pro každou operaci je symbol, který představuje \*tuto operaci, například +, -, , a tak dále. Chcete-li zpřístupnit operaci sčítání, přidejte do `SimpleCalculator` modulu nebo oboru názvů následující třídu:

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

Atribut <xref:System.ComponentModel.Composition.ExportAttribute> funguje stejně jako dříve. Atribut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> připojí metadata ve formě dvojice název-hodnota k tomuto exportu. Zatímco `Add` třída implementuje `IOperation`, třída, která implementuje `IOperationData` není explicitně definována. Místo toho je třída implicitně vytvořena MEF s vlastnostmi založenými na názvech poskytnutých metadat. (Toto je jeden z několika způsobů, jak získat přístup k metadatům v MEF.)

Složení v MEF je *rekurzivní*. Explicitně jste `Program` složili objekt, `ICalculator` který importoval, `MySimpleCalculator`který se ukázal jako typ . `MySimpleCalculator`, na druhé straně importuje kolekci `IOperation` objektů a `MySimpleCalculator` tento import bude vyplněn při vytvoření, ve stejnou dobu jako importy . `Program` Pokud `Add` třída deklarovala další import, muselo by být také vyplněno a tak dále. Jakýkoli import, který zůstal nevyplněný, má za následek chybu složení. (Je však možné deklarovat importy jako volitelné nebo jim přiřadit výchozí hodnoty.)

## <a name="calculator-logic"></a>Kalkulačka Logika

S těmito částmi na místě, vše, co zbývá, je kalkulačka logiku sám. Přidejte následující kód `MySimpleCalculator` do třídy k implementaci `Calculate` metody:

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

Počáteční kroky analyzovat vstupní řetězec do levé a pravé operandy a znak operátoru. Ve `foreach` smyčce je zkoumán každý člen `operations` kolekce. Tyto objekty <xref:System.Lazy%602>jsou typu a jejich hodnoty metadat a exportovaný <xref:System.Lazy%602.Metadata%2A> objekt <xref:System.Lazy%601.Value%2A> lze přistupovat s vlastností a vlastností. V tomto případě `Symbol` pokud je `IOperationData` vlastnost objektu zjištěno, že se `Operate` shoduje, `IOperation` kalkulačka volá metodu objektu a vrátí výsledek.

K dokončení kalkulačky potřebujete také pomocnou metodu, která vrátí pozici prvního nečíselného znaku v řetězci. Do třídy přidejte `MySimpleCalculator` následující pomocnou metodu:

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

Nyní byste měli být schopni zkompilovat a spustit projekt. V jazyce Visual Basic zkontrolujte, zda jste přidali `Public` klíčové slovo do aplikace `Module1`. V okně konzoly zadejte operaci sčítání, například "5+3", a kalkulačka vrátí výsledky. Jakýkoli jiný operátor má za následek "Operace nebyla nalezena!" zpráva.

## <a name="extending-simplecalculator-using-a-new-class"></a>Rozšíření SimpleCalculator pomocí nové třídy

Nyní, když kalkulačka funguje, přidání nové operace je snadné. Do modulu nebo `SimpleCalculator` oboru názvů přidejte následující třídu:

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

Zkompilujte a spusťte projekt. Zadejte operaci odčítání, například "5-3". Kalkulačka nyní podporuje odčítání, stejně jako sčítání.

## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozšíření SimpleCalculator pomocí nového sestavení

Přidání tříd do zdrojového kódu je dost jednoduché, ale MEF poskytuje možnost podívat se mimo vlastní zdroj aplikace pro součásti. Chcete-li to demonstrovat, budete muset upravit SimpleCalculator pro vyhledávání v adresáři, <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>stejně jako jeho vlastní sestavení, pro díly, přidáním .

Přidejte nový `Extensions` adresář s názvem SimpleCalculator projektu. Nezapomeňte jej přidat na úrovni projektu a ne na úrovni řešení. Potom přidejte do řešení nový projekt `ExtendedOperations`knihovny tříd s názvem . Nový projekt se zkompiluje do samostatného sestavení.

Otevřete Návrhář vlastností projektu pro projekt ExtendedOperations a klepněte na **Output path** kartu **Kompilace** nebo **Sestavení.** **Build output path** * \SimpleCalculator\Extensions\\*).

 V *modulu 1.vb* nebo *Program.cs*přidejte do konstruktoru `Program` následující řádek:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

Nahraďte ukázkovou cestu cestou do adresáře Rozšíření. (Tato absolutní cesta je pouze pro účely ladění. V produkční aplikaci byste použili relativní cestu.) Nyní <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> přidá všechny součásti nalezené v všech sestaveních v adresáři Rozšíření do kontejneru kompozice.

V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System.ComponentModel.Composition. V souboru třídy ExtendedOperations přidejte příkaz nebo `Imports` `using` příkaz pro System.ComponentModel.Composition. V jazyce Visual `Imports` Basic také přidejte příkaz pro SimpleCalculator. Potom přidejte do souboru třídy ExtendedOperations následující třídu:

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

Všimněte si, že aby se <xref:System.ComponentModel.Composition.ExportAttribute> smlouva shodovala, musí <xref:System.ComponentModel.Composition.ImportAttribute>mít atribut stejný typ jako .

Zkompilujte a spusťte projekt. Otestujte nový mod (%) Operátor.

## <a name="conclusion"></a>Závěr

Toto téma se týkalo základních pojmů MEF.

- Části, katalogy a kontejner složení

     Díly a kontejner složení jsou základními stavebními kameny aplikace MEF. Součást je libovolný objekt, který importuje nebo exportuje hodnotu až do sebe sama včetně. Katalog poskytuje kolekci částí z určitého zdroje. Kontejner složení používá části poskytované katalogu k provedení složení, vazba importu k vývozu.

- Dovoz a vývoz

     Importy a exporty jsou způsob, jakým komponenty komunikují. Při importu komponenta určuje potřebu určité hodnoty nebo objektu a při exportu určuje dostupnost hodnoty. Každý import je spárován se seznamem exportů prostřednictvím své smlouvy.

## <a name="next-steps"></a>Další kroky

Chcete-li stáhnout úplný kód pro tento příklad, naleznete [simplecalculator ukázka (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

 Další informace a příklady kódu naleznete [v tématu Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Seznam typů MEF naleznete v <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.
