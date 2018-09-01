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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323dfe7d68f5a6f6274ce23f82e25a337956b23c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386425"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
Toto téma obsahuje přehled služby Managed Extensibility Framework zavedena v rozhraní .NET Framework 4.  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a>Co je MEF?  
 Managed Extensibility Framework nebo MEF je knihovna pro vytváření jednoduchých, rozšiřitelných aplikací. Umožňuje aplikaci vývojářům poznávání a používání rozšíření bez nezbytné konfigurace. Také umožňuje rozšíření vývojáři snadno zapouzdření kód a vyhnout se křehké pevné závislosti. MEF nejen umožňuje rozšíření opětovné použití v aplikacích, ale napříč aplikacemi stejně.  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a>Problém rozšiřitelnosti  
 Představte si, že jste architekt velké aplikace, které musíte poskytovat podporu pro rozšíření. Vaše aplikace musí obsahovat potenciálně velký počet menších komponent a je zodpovědný za vytváření a spouštění je.  
  
 Nejjednodušším přístupem k problému se zahrnout součásti jako zdrojový kód ve vaší aplikaci, a je volat přímo z uživatelského kódu.  Tato akce nemá počet viditelných nevýhody.  Co je nejdůležitější nelze přidat nové komponenty bez změny zdrojového kódu, omezení, které může být přijatelný, například webové aplikace, ale je v nefunkčním v klientské aplikaci.  Rovnoměrně problematické, nemáte přístup ke zdrojovému kódu pro součásti, protože může být vyvinuté třetími stranami a ze stejného důvodu, že nemůže povolit jejich přístupu k té vaší.  
  
 Zadejte rozšiřovacího bodu nebo rozhraní, tak, aby povolovala oddělení mezi aplikací a jeho součástí je o něco sofistikovanější přístup.  V rámci tohoto modelu můžete zadat rozhraní, které můžete implementovat součásti a rozhraní API, který umožňuje interakci s vaší aplikací.  To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má svůj vlastní potíže.  
  
 Protože aplikace nemá žádné kapacity pro zjišťování součásti sama o sobě, se musí stále explicitně až k tomu dojde komponenty, které jsou k dispozici a musí být načten.  To je obvykle provedeno explicitně registrací dostupné součásti v konfiguračním souboru. To znamená, že součásti je ujištěním, která jsou správné stane problém údržby, zejména v případě, že je koncový uživatel a ne vývojář, který se má provést aktualizaci.  
  
 Kromě toho jsou součástí nepodporuje komunikaci mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotná aplikace.  Pokud architekt aplikací nebyl očekávané potřebu konkrétního komunikace je obvykle možné.  
  
 A konečně vývojáři komponent musí přijmout pevné závislost na sestavení, které obsahuje rozhraní, které implementují.  Je těžké pro komponentu, který se má použít ve více než jednu aplikaci a můžete také vytvářet problémy při vytváření testů pro komponenty.  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a>Co obsahuje rozhraní MEF  
 Místo této explicitní registraci dostupné součásti MEF poskytuje způsob, jak je implicitně, zjišťování prostřednictvím *složení*.  Komponenta MEF, volá se *část*, deklarativně určuje i jeho závislosti (označované jako *importuje*) a jaké možnosti (označované jako *exportuje*) jsou k dispozici. Když se části, Kompoziční modul rozhraní MEF splňuje jeho importů s tím, co je k dispozici z jiných částí.  
  
 Tento přístup řeší problémy popsané v předchozí části.  Protože částí MEF deklarativně specifikovat jejími funkcemi, jsou zjistitelné za běhu, což znamená, že aplikace může být použít částí bez pevně zakódované odkazy nebo křehké konfigurační soubory.  MEF umožňuje aplikacím zjistit a prozkoumejte části podle metadat, bez vytvoření instance je nebo dokonce načítání jejich sestavení. V důsledku toho není nutné pečlivě určit, kdy a jak se mají načíst rozšíření.  
  
 Kromě jeho zadaná exporty můžete zadat část jeho importů, které se sestavil jiné části.  Toto usnadňuje komunikaci mezi části není pouze je to možné, ale snadno a umožňuje dobré řešení kódu. Například služby, které jsou společné pro mnoho součástí můžete být promítnout do samostatných částí a snadno upravit nebo nahradit.  
  
 Protože MEF model vyžaduje žádné pevné závislost na sestavení konkrétní aplikace, umožňuje rozšíření znovu použít z aplikace.  To také usnadňuje vývoj testovací prostředí, nezávisle na aplikaci k testování rozšíření komponenty.  
  
 Rozšiřitelné aplikace vytvořené pomocí MEF deklaruje, že import, který může být naplněno komponent rozšíření a může také deklarovat exportuje, aby bylo možné zveřejnit aplikačními službami, abyste rozšíření.  Jednotlivé komponenty rozšíření deklaruje export a může také deklarovat importy.  Tímto způsobem jsou automaticky rozšiřitelné komponent rozšíření sami.  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a>Pokud je k dispozici rozhraní MEF  
 MEF je nedílnou součástí toho, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]a je k dispozici všude, kde se používá rozhraní .NET Framework.  MEF můžete použít v klientských aplikacích používají Windows Forms, WPF nebo jiné technologie, nebo v serverové aplikace, které pomocí technologie ASP.NET.  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a>MEF a MAF  
 Předchozí verze rozhraní .NET Framework zavedené spravované Add-in Framework (MAF), navržená tak, aby umožňovala izolaci a správu rozšíření.  Fokus MAF je mírně vyšší úrovni než MEF soustředíte na rozšíření izolace a sestavení, načítání a uvolňování, zatímco na MEF, zaměřuje se na možnosti rozpoznání, rozšíření a přenositelnost.  Dvě architektury hladce spolupracují, a jednu aplikaci můžete využít výhod obou.  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Ukázková aplikace  
 Nejjednodušší způsob, jak zobrazit, co můžete dělat MEF je vytvořit jednoduchou aplikaci MEF. V tomto příkladu vytvoříte s názvem SimpleCalculator velmi jednoduchou kalkulačku. Cílem SimpleCalculator je Vytvořte konzolovou aplikaci, která přijímá základní aritmetické příkazy ve tvaru "5 + 3" nebo "6-2" a vrátí správné odpovědi. Použití rozhraní MEF, budete moct přidat nové operátory beze změny kódu aplikace.  
  
 Stáhnout kompletní kód v tomto příkladu, najdete v článku [SimpleCalculator ukázka](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
> [!NOTE]
>  Účelem SimpleCalculator je k předvedení konceptů a syntaxe MEF, nikoli nutně poskytnout realistické scénáře jeho použití. Mnoho aplikací, které by měla mít prospěch maximálně využít sílu MEF jsou složitější než SimpleCalculator. Rozsáhlejší příklady najdete v článku [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) na Githubu.
  
 Pokud chcete začít, v [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], vytvořte nový projekt konzolové aplikace s názvem `SimpleCalculator`. Přidáte odkaz na sestavení System.ComponentModel.Composition, ve které se nachází MEF. Otevřete Module1.vb nebo soubor Program.cs a přidejte `Imports` nebo `using` příkazy pro System.ComponentModel.Composition a System.ComponentModel.Composition.Hosting. Tyto dva obory názvů obsahují typy MEF, které potřebujete pro vývoj rozšiřitelných aplikací. V jazyce Visual Basic přidejte `Public` – klíčové slovo na řádek, který deklaruje `Module1` modulu.  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a>Kontejner kompozic rozhraní MEF a katalogů  
 Základní model složení MEF je *kontejner kompozic rozhraní MEF*, který obsahuje všechny součásti, které jsou k dispozici a provede sestavení.  (To znamená, že odpovídající z importů pro export.)  Nejběžnějším typem kontejner kompozic rozhraní MEF je <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, a to pro SimpleCalculator použijete.  
  
 V jazyce Visual Basic v Module1.vb, přidejte veřejnou třídu s názvem `Program`. Pak přidejte následující řádek, který `Program` třídy v Module1.vb nebo Program.cs:  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 Chcete-li vyhledat částí, které jsou k dispozici, kompozice kontejnery využívá *katalogu*. Katalog je objekt, který je k dispozici částí zjištěných z nějakého zdroje.  MEF poskytuje katalogů a zjistit částí z poskytnutého typu, sestavení nebo adresáře. Vývojáři aplikací můžete snadno vytvořit nové katalogů a Objevte částí z jiných zdrojů, jako jsou webové služby.  
  
 Přidejte následující konstruktor k `Program` třídy:  
  
```vb  
Public Sub New()  
    'An aggregate catalog that combines multiple catalogs  
     Dim catalog = New AggregateCatalog()  
  
    'Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))  
  
    'Create the CompositionContainer with the parts in the catalog  
    _container = New CompositionContainer(catalog)  
  
    'Fill the imports of this object  
    Try  
        _container.ComposeParts(Me)  
    Catch ex As Exception  
        Console.WriteLine(ex.ToString)  
    End Try  
End Sub  
```  
  
```csharp  
private Program()  
{  
    //An aggregate catalog that combines multiple catalogs  
    var catalog = new AggregateCatalog();  
    //Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));  
  
    //Create the CompositionContainer with the parts in the catalog  
    _container = new CompositionContainer(catalog);  
  
    //Fill the imports of this object  
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
  
 Volání <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> říká kontejner kompozic sestavit konkrétní sadu části v tomto případě aktuální instancí třídy `Program`. V tomto okamžiku však není provedena žádná akce, protože `Program` nemá žádné importy tak, aby vyplnil.  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a>Importy a exporty s atributy  
 Nejdřív musíte `Program` importovat kalkulačku. To umožňuje oddělení uživatelského rozhraní aspekty, jako je konzola vstup a výstup, který přejde do `Program`, od logiky kalkulačky.  
  
 Přidejte následující kód, který `Program` třídy:  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 Všimněte si, že deklarace `calculator` objekt není, ale je doplněn <xref:System.ComponentModel.Composition.ImportAttribute> atribut.  Tento atribut deklaruje byste měli importu; To znamená ho bude vyplněno modul složení při objektu se skládá.  
  
 Má každý import *kontraktu*, který určuje, jaké exporty bude možné porovnat s. Kontrakt musí být řetězec s explicitně zadanými nebo ho automaticky generuje služba MEF ze zadaného typu, v tomto případě rozhraní `ICalculator`.  Každý export deklarována s odpovídající smlouvy bude splnění tohoto importu.  Všimněte si, že při typu `calculator` objekt je ve skutečnosti `ICalculator`, tento krok není povinný. Smlouva je nezávislý na typ importu objektu.  (V takovém případě může vynecháte `typeof(ICalculator)`.  MEF automaticky zaujme smlouvy založený na typ importu, pokud ho explicitně neurčíte.)  
  
 Přidat toto velmi jednoduché rozhraní modulu nebo `SimpleCalculator` obor názvů:  
  
```vb  
Public Interface ICalculator  
    Function Calculate(ByVal input As String) As String  
End Interface  
```  
  
```csharp  
public interface ICalculator  
{  
    String Calculate(String input);  
}  
```  
  
 Teď, když jste definovali `ICalculator`, je třeba třídu, která jej implementuje.  Přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:  
  
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
  
 Tady je export, která bude odpovídat import v `Program`. Pro export tak, aby odpovídaly importu, exportu musí mít stejný kontrakt.  Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` vyprodukuje neshodu a import by vyplněné; kontrakt musí přesně shodovat.  
  
 Vzhledem k tomu, že vyplní kontejner kompozic se všemi částmi, které jsou k dispozici v tomto sestavení `MySimpleCalculator` část bude k dispozici.  Při konstruktor pro `Program` provádí složení `Program` objektu, bude vyplněn jeho import `MySimpleCalculator` objekt, který se vytvoří pro tento účel.  
  
 Uživatelské rozhraní vrstvě (`Program`) nemusí vědět vše ostatní.  Můžete tedy přejít k vyplnění zbývající logiku uživatelského rozhraní v `Main` metody.  
  
 Přidejte následující kód, který `Main` metody:  
  
```vb  
Sub Main()  
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
    Program p = new Program(); //Composition is performed in the constructor  
    String s;  
    Console.WriteLine("Enter Command:");  
    while (true)  
    {  
        s = Console.ReadLine();  
        Console.WriteLine(p.calculator.Calculate(s));  
    }  
}  
```  
  
 Tento kód jednoduše načte řádek vstupu a volání `Calculate` funkce `ICalculator` na výsledek, který zapíše zpět do konzoly. Tedy kód potřebujete v `Program`.  Všechny zbývající práce proběhne v částech.  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a>Další importy a ImportMany  
 Aby SimpleCalculator mít rozšiřitelný je potřeba importovat seznam operací. Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut vyplní pouze jeden <xref:System.ComponentModel.Composition.ExportAttribute>.  Pokud je více než jeden dostupný, Kompoziční modul dojde k chybě.  K vytvoření, import, který můžete zadat libovolný počet exportů, můžete použít <xref:System.ComponentModel.Composition.ImportManyAttribute> atribut.  
  
 Přidejte následující vlastnosti operace, která má `MySimpleCalculator` třídy:  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <xref:System.Lazy%602> typem poskytované rozhraní MEF pro uložení nepřímé odkazy na exporty.  Tady, kromě samotného exportované objektu, budete mít také *export metadat*, nebo informace, které popisují exportované objektu. Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt představující aktuální operace a `IOperationData` objekt představující jeho metadata.  
  
 Přidejte následující jednoduché rozhraní modulu nebo `SimpleCalculator` obor názvů:  
  
```vb  
Public Interface IOperation  
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer  
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
  
 V tomto případě metadata pro každou operaci je symbol, který představuje tuto operaci, jako například +, -, *, a tak dále. Pokud chcete zpřístupnit operaci sčítání, přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "+"c)>  
Public Class Add  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
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
  
 <xref:System.ComponentModel.Composition.ExportAttribute> Atribut funkce stejně jako dříve.  <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atribut připojí k této exportu metadat ve formě dvojice název hodnota.  Zatímco `Add` implementuje třída `IOperation`, třídu, která implementuje `IOperationData` nejsou výslovně definované. Místo toho třídy implicitně vytvoří MEF s vlastnostmi na základě názvů metadata k dispozici.  (To je jedním z několika způsoby, jak získat přístup k metadatům v MEF.)  
  
 Složení v MEF *rekurzivní*. Můžete explicitně složený `Program` objekt, který importován `ICalculator` , ukázalo se typ `MySimpleCalculator`.  `MySimpleCalculator`, pak importuje kolekci `IOperation` objekty a, import se naplní při `MySimpleCalculator` se vytvoří ve stejnou dobu jako importů `Program`. Pokud `Add` třídy deklarované další importu, který by příliš měla být vyplněny a tak dále. Žádný import levé nevyplněným výsledků v chybě složení.  (To je ale možné, chcete-li deklarovat importy být volitelný nebo přiřadit výchozí hodnoty.)  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a>Kalkulačka logiky  
 Pomocí těchto částí v místě už jen zbývá vlastní logiky kalkulačku. Přidejte následující kód `MySimpleCalculator` třídu pro implementaci `Calculate` metody:  
  
```vb  
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate  
    Dim left, right As Integer  
    Dim operation As Char  
    Dim fn = FindFirstNonDigit(input) 'Finds the operator  
    If fn < 0 Then  
        Return "Could not parse command."  
    End If  
    operation = input(fn)  
    Try  
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
public String Calculate(String input)  
{  
    int left;  
    int right;  
    Char operation;  
    int fn = FindFirstNonDigit(input); //finds the operator  
    if (fn < 0) return "Could not parse command.";  
  
    try  
    {  
        //separate out the operands  
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
  
 Počáteční kroky parsovat vstupní řetězec do levé a pravé operandy a znak operátoru.  V `foreach` smyčky, každý člen `operations` kolekce je zkontrolován. Tyto objekty jsou typu <xref:System.Lazy%602>, a jejich hodnoty metadat a exportovaný objekt lze přistupovat pomocí <xref:System.Lazy%602.Metadata%2A> vlastnost a <xref:System.Lazy%601.Value%2A> vlastnost v uvedeném pořadí. V takovém případě pokud `Symbol` vlastnost `IOperationData` objekt zjištěn být shoda, volání Kalkulačka `Operate` metodu `IOperation` objekt a vrátí výsledek.  
  
 K dokončení kalkulačky, potřebujete také Pomocná metoda, která vrátí pozici první nečíslicovému znaku v řetězci.  Přidejte následující pomocnou metodu k `MySimpleCalculator` třídy:  
  
```vb  
Private Function FindFirstNonDigit(ByVal s As String) As Integer  
    For i = 0 To s.Length  
        If (Not (Char.IsDigit(s(i)))) Then Return i  
    Next  
    Return -1  
End Function  
```  
  
```csharp  
private int FindFirstNonDigit(String s)  
{  
    for (int i = 0; i < s.Length; i++)  
    {  
        if (!(Char.IsDigit(s[i]))) return i;  
    }  
    return -1;  
}  
```  
  
 Teď by měl být schopen kompilace a spuštění projektu. V jazyce Visual Basic, ujistěte se, že jste přidali `Public` – klíčové slovo do `Module1`. V okně konzoly zadejte další operace, jako je například "5 + 3", a vrátí výsledky kalkulačky.  Další operátor způsobí "operaci nebyl nalezen!" zpráva.  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a>Rozšíření SimpleCalculator pomocí nové třídy  
 Teď, když funguje kalkulačky, přidání nové operace je snadné. Přidejte následující třídu modulu nebo `SimpleCalculator` obor názvů:  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "-"c)>  
Public Class Subtract  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
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
  
 Kompilace a spuštění projektu. Typ operace odčítání, jako je například "5-3". Kalkulačce teď podporuje odčítání, stejně jako další.  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozšíření SimpleCalculator pomocí nové sestavení  
 Přidávání tříd ke zdroji je kód dostatečně jednoduchá, ale poskytuje možnost Hledat mimo zdroj aplikace vlastní části MEF. Abychom si předvedli to, budete muset upravit SimpleCalculator vyhledat adresář, stejně jako vlastní sestavení částí, tak, že přidáte <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.  
  
 Přidat nový adresář s názvem `Extensions` SimpleCalculator projektu.  Ujistěte se, že ho přidáte na úrovni projektu a ne na úrovni řešení. Pak přidejte nový projekt knihovny tříd k řešení s názvem `ExtendedOperations`. Nový projekt zkompiluje do samostatného sestavení.  
  
 Otevřete Návrhář vlastnosti projektu pro projekt ExtendedOperations a klikněte na tlačítko **kompilaci** nebo **sestavení** kartu. Změnit **výstupní cesta sestavení** nebo **výstupní cesta** tak, aby odkazoval do adresáře rozšíření v adresáři projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).  
  
 V souboru Program.cs nebo Module1.vb, přidejte následující řádek, který `Program` konstruktor:  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 Příklad cesty nahraďte cestou k adresáři rozšíření.  (Tato absolutní cesta je pouze pro účely ladění.  V produkční aplikace použijete relativní cestu.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teď přidá všechny části v všechna sestavení v adresáři rozšíření pro kontejner složení.  
  
 V projektu ExtendedOperations přidejte odkazy na SimpleCalculator a System.ComponentModel.Composition. V souboru ExtendedOperations třídy, přidejte `Imports` nebo `using` příkaz pro System.ComponentModel.Composition. V jazyce Visual Basic, také přidat `Imports` příkaz pro SimpleCalculator. Soubor třídy ExtendedOperations pak přidejte následující třídu:  
  
```vb  
<Export(GetType(SimpleCalculator.IOperation))>  
<ExportMetadata("Symbol", "%"c)>  
Public Class Modulo  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
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
  
 Všimněte si, že v pořadí pro kontrakt tak, aby odpovídaly, <xref:System.ComponentModel.Composition.ExportAttribute> atribut musí být stejného typu jako <xref:System.ComponentModel.Composition.ImportAttribute>.  
  
 Kompilace a spuštění projektu. Vyzkoušejte nový operátor Mod (%).  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 V tomto tématu se vztahují o základních konceptech služby MEF.  
  
-   Částí, katalogy a kontejner kompozic  
  
     Části a kontejner kompozic jsou základní stavební bloky aplikací rozhraní MEF. Součástí je libovolný objekt, který importuje nebo exportuje hodnotu, až po a včetně samotného. Katalog poskytuje kolekci částí z určitého zdroje.  Kontejner kompozic používá části poskytované katalog k sestavení, vazba importy pro export.  
  
-   Importy a exporty  
  
     Importy a exporty představují způsob, kterým součásti mohou komunikovat. Importu komponentu určuje potřebu konkrétní hodnotu nebo objekt a s export určuje dostupnosti hodnotu. Každý import je nalezena shoda se seznamem exporty prostřednictvím jejich smlouvy.  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a>Kam se mám obrátit nyní?  
 Stáhnout kompletní kód v tomto příkladu, najdete v článku [SimpleCalculator ukázka](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
 Další informace a příklady kódu naleznete v tématu [Managed Extensibility Framework](https://go.microsoft.com/fwlink/?LinkId=144282). Seznam typů rozhraní MEF, najdete v článku <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.
