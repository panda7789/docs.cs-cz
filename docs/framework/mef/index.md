---
title: Managed Extensibility Framework (MEF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
caps.latest.revision: 31
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 524fa0f2d654c812189ff6863f84db81144fb48f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
Toto téma obsahuje přehled spravované rozhraní rozšiřitelnosti byla zavedená v rozhraní .NET Framework 4.  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a>Co je MEF?  
 Spravovaná rozhraní rozšiřitelnosti nebo MEF je knihovna pro vytváření aplikací pro jednoduché a rozšiřitelné. To umožňuje vývojáři aplikace k zjišťovat a používat rozšíření s nutná žádná konfigurace. Také umožňuje rozšíření vývojáři snadno zapouzdření kódu a vyhnout se křehké pevný závislosti. MEF nejen umožňuje rozšíření znovu použije v rámci aplikace, ale napříč i aplikace.  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a>Problém rozšiřitelnosti  
 Představte si, že jste architekt velké aplikace, které musí poskytovat podporu pro rozšíření. Aplikace musí obsahovat potenciálně velkého počtu menší součásti a je odpovědná za vytváření a spustil je.  
  
 Nejjednodušším přístupem při problém je zahrnout komponenty jako zdrojového kódu v aplikaci, a je volat přímo z vašeho kódu.  To má počet zřejmé nevýhody.  Co je nejdůležitější – nelze přidat nové komponenty beze změny zdrojový kód, který může být přijatelné in, například webovou aplikaci, ale je v aplikaci klienta nefunkčním omezení.  Stejně problematické, nemáte přístup ke zdrojovému kódu pro součásti, protože může být vyvinutá třetích stran a ze stejného důvodu, že nelze povolit, aby váš přístup.  
  
 Mírně propracovanější postup by poskytnout rozšíření bodu nebo rozhraní, tak, aby povolovala oddělení mezi aplikací a jeho komponenty.  V tomto modelu můžete zadat rozhraní, které můžete implementovat součásti a rozhraní API pro interakci s vaší aplikací.  To řeší problém vyžadující přístup ke zdrojovému kódu, ale stále má svou vlastní problémy.  
  
 Protože aplikace nemá žádné kapacity pro zjišťování součásti sama o sobě, se musí stále explicitně říct, součástí, které jsou k dispozici a mělo by být načíst.  Obvykle to provádí explicitně registrace dostupné součásti v konfiguračním souboru. To znamená, že zabezpečit, aby komponenty jsou správné stane údržby problém, zvlášť pokud je koncové uživatele a není vývojář, který se očekává proveďte aktualizaci.  
  
 Kromě toho jsou komponenty nepodporující komunikaci mezi sebou, s výjimkou prostřednictvím pevně definovaných kanálů samotné aplikace.  Pokud architekt aplikace nebyla očekává nutné pro konkrétní komunikaci, je obvykle možné.  
  
 Nakonec vývojáři komponent musí přijmout pevný závislost na jaké sestavení obsahuje rozhraní, která implementují.  To ztěžuje součást použije ve více než jednu aplikaci a může také způsobit problémy při vytváření test framework pro součásti.  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a>Co nabízí MEF  
 Místo tato explicitní registrace k dispozici součástí MEF poskytuje způsob, jak je implicitně, zjišťovat prostřednictvím *složení*.  Komponenty MEF, s názvem *část*, deklarativně určuje jeho závislé součásti (označované jako *importuje*) a funkcích (označované jako *exportuje*) jsou k dispozici. Když je vytvořen součástí, modul složení MEF splňuje jeho importy s co je dostupné z dalších částí.  
  
 Tento přístup řeší problémy, které jsou popsané v předchozí části.  Protože částí rozhraní MEF deklarativně zadat jejich schopnosti, jsou zjistitelný za běhu, což znamená, že aplikace provádět použít částí bez pevně odkazy nebo křehké konfigurační soubory.  MEF umožňuje aplikacím pro zjišťování a kontrolu částí podle jejich metadat bez vytváření instancí je nebo i načtení jejich sestavení. V důsledku toho není třeba pečlivě určit, kdy a jak se mají načíst rozšíření.  
  
 Kromě jeho zadaný exportuje můžete zadat část jeho importy, které budou plnit podle dalších částí.  Tato díky komunikace mezi částí není pouze možná, ale snadno a umožňuje dobré řešení kódu. Například služby, které jsou společné pro celou řadu součástí můžete být promítnou do samostatné části a snadno upravit nebo nahradit.  
  
 Protože MEF modelu vyžaduje žádné pevné závislost na konkrétní aplikaci sestavení, umožňuje rozšíření znovu použije z aplikace do aplikace.  To také umožňuje snadno vyvíjet test harness, nezávisle na aplikaci, otestovat rozšíření součásti.  
  
 Rozšiřitelné aplikace napsané pomocí MEF deklaruje, že importu, který může být vyplněna součástmi rozšíření a může také deklarovat exportuje tak, aby získal aplikačních služeb pro rozšíření.  Jednotlivé komponenty rozšíření deklaruje exportu a může také deklarovat importy.  Tímto způsobem jsou automaticky extensible rozšíření komponenty, sami.  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a>Kde je k dispozici MEF?  
 MEF je nedílnou součástí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]a je k dispozici, kdekoli se používá rozhraní .NET Framework.  Můžete vytvořit MEF v klientských aplikacích, ať už používají Windows Forms, WPF nebo jiné technologie, nebo v serverových aplikací, které pomocí technologie ASP.NET.  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a>MEF a MAF  
 Předchozí verze rozhraní .NET Framework zavedl spravované Add-in Framework (MAF), navržená tak, aby aplikacím umožňují izolovat a správě rozšíření.  Cílem tohoto MAF je něco vyšší úrovni než MEF, který je zaměřený na rozšíření izolace a sestavení načítání a uvolňování, pokud je fokus na MEF na možnosti rozpoznání, rozšíření a přenositelnost.  Dvě rozhraní spolupracovat plynule a jedné aplikace můžete využít i.  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Ukázková aplikace  
 Nejjednodušší způsob, jak zobrazit, co můžete dělat MEF je vytvořit jednoduchou aplikaci MEF. V tomto příkladu vytvoříte velmi jednoduché kalkulačky s názvem SimpleCalculator. Cílem SimpleCalculator je k vytvoření konzolové aplikace, který přijímá základní aritmetické příkazy ve tvaru "5 + 3" nebo "6-2" a vrátí správné odpovědi. Pomocí rozhraní MEF, nebudete moct přidat nové operátory beze změny kódu aplikace.  
  
 Si můžete stáhnout kompletní kód v tomto příkladu [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
> [!NOTE]
>  Účelem SimpleCalculator je k předvedení konceptů a syntaxe MEF, nikoli nutně zajistit realistické scénář pro jeho použití. Mnoho aplikací, které by měla mít prospěch většinu od výkonu MEF je mnohem složitější než SimpleCalculator. Rozsáhlejší příklady najdete v tématu [spravované rozhraní rozšiřitelnosti](https://github.com/MicrosoftArchive/mef) na Githubu.
  
 Chcete-li spustit v [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], vytvořte nový projekt konzolové aplikace s názvem `SimpleCalculator`. Přidáte odkaz na sestavení System.ComponentModel.Composition, kde se nachází MEF. Otevřete Module1.vb nebo Program.cs a přidejte `Imports` nebo `using` příkazy pro System.ComponentModel.Composition a System.ComponentModel.Composition.Hosting. Tyto dva obory názvů obsahovat typy MEF budete muset vyvíjet rozšiřitelné aplikace. V jazyce Visual Basic, přidejte `Public` – klíčové slovo na řádek, který deklaruje `Module1` modulu.  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a>Složení kontejneru a katalogy  
 Je základní modelu složení MEF *složení kontejneru*, který obsahuje všechny části k dispozici a provede složení.  (To znamená, shody s importy pro export.)  Nejběžnějším typem složení kontejneru je <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, a to bude používat pro SimpleCalculator.  
  
 V jazyce Visual Basic v Module1.vb přidejte veřejnou třídu s názvem `Program`. Pak přidejte následující řádek na `Program` třídy v Module1.vb nebo Program.cs:  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 Chcete-li vyhledat dostupné, kontejnery složení částí využívá *katalogu*. Katalog je objekt, který je k dispozici částí zjištěných z některé zdroje.  MEF poskytuje katalogy pro zjišťování částí ze zadaného typu, sestavení nebo v adresáři. Vývojáři aplikací můžete snadno vytvořit nový katalogy pro zjišťování částí z jiných zdrojů, například webovou službu.  
  
 Přidejte následující konstruktor `Program` třídy:  
  
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
  
 Volání <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontejner složení, aby tvoří konkrétní sadu části v tomto případě aktuální instancí třídy `Program`. V tuto chvíli však není provedena žádná akce, protože `Program` nemá žádné importy k vyplnění.  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a>Import a export s atributy  
 Nejdřív musíte `Program` importovat kalkulačky. To umožňuje oddělení uživatelské rozhraní otázky, jako je například konzola vstup a výstup, který bude odeslán do `Program`, z logiky kalkulačky.  
  
 Přidejte následující kód, který `Program` třídy:  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 Všimněte si, že deklaraci `calculator` objekt není, ale je upravena pomocí <xref:System.ComponentModel.Composition.ImportAttribute> atribut.  Tento atribut deklaruje něco jako importu; To znamená, že ho bude vyplněno modul složení při objekt se skládá.  
  
 Má každý importu *kontrakt*, která určuje, jaké exporty budou přiřazeny. Kontrakt může být explicitně zadaný řetězec, nebo ji automaticky generuje služba MEF z daného typu, v tomto případě rozhraní `ICalculator`.  Každý export deklarovat s kontraktu odpovídající bude splnění tohoto importu.  Všimněte si, že se při typ `calculator` objekt je ve skutečnosti `ICalculator`, není to povinné. Kontrakt je nezávislé na typ objektu import.  (V takovém případě může nechat `typeof(ICalculator)`.  MEF automaticky převezme kontrakt byl založen na typ importu, pokud ji zadáte explicitně.)  
  
 Přidejte tento velmi jednoduché rozhraní, modul nebo `SimpleCalculator` obor názvů:  
  
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
  
 Teď, když jste definovali `ICalculator`, musíte třídu, která implementuje ho.  Přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:  
  
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
  
 Tady je export, který se bude shodovat s import do `Program`. V pořadí pro export tak, aby odpovídaly import export musí mít stejné smlouvy.  Export v rámci smlouvy na základě `typeof(MySimpleCalculator)` byste mohli vytvořit neshody a import by být vyplněna; kontrakt musí přesně shodovat.  
  
 Vzhledem k tomu, že kontejner složení vyplní se všechny součásti, které jsou k dispozici v tomto sestavení `MySimpleCalculator` část bude k dispozici.  Když v konstruktoru pro `Program` složení provádí `Program` objektu, bude vyplněn jeho import `MySimpleCalculator` objekt, který se vytvoří pro tento účel.  
  
 Uživatelské rozhraní vrstvě (`Program`) nemusí vědět nic jiného.  Proto můžete vyplnit ve zbývající části logiku uživatelského rozhraní v `Main` metoda.  
  
 Přidejte následující kód, který `Main` metoda:  
  
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
  
 Tento kód jednoduše přečte řádek vstupu a volání `Calculate` funkce `ICalculator` na výsledek, který zapíše zpět do konzoly. To znamená všechny kód, který potřebujete v `Program`.  Všechny zbývající práce proběhne v části.  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a>Další importy a ImportMany  
 Aby SimpleCalculator na rozšiřitelnost je nutné importovat seznam operací. Běžný <xref:System.ComponentModel.Composition.ImportAttribute> atribut vyplní pouze jeden <xref:System.ComponentModel.Composition.ExportAttribute>.  Pokud je více než jeden dostupný, modul složení vyvolá chybu.  Pokud chcete vytvořit tak může být vyplněna podle libovolný počet exportuje importu, můžete použít <xref:System.ComponentModel.Composition.ImportManyAttribute> atribut.  
  
 Přidejte následující vlastnosti operací `MySimpleCalculator` třídy:  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <xref:System.Lazy%602>Typ poskytovaný MEF pro uložení nepřímé odkazy na export.  Zde, kromě exportovaný samotného objektu získáte *export metadat*, nebo informace, které popisují exportovaný objekt. Každý <xref:System.Lazy%602> obsahuje `IOperation` objekt, představující aktuální operace a `IOperationData` objekt, představující jeho metadata.  
  
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
  
 V takovém případě metadata pro každou operaci je symbol, který představuje tuto operaci, jako například +, -, *, a tak dále. Operace přidání zpřístupnit, přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:  
  
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
  
 <xref:System.ComponentModel.Composition.ExportAttribute> Atribut funkce jako předtím.  <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atribut připojí metadata, a to ve formě pár název hodnota pro tento export.  Když `Add` třída implementuje `IOperation`, třídu, která implementuje `IOperationData` nejsou výslovně definované. Místo toho třída je implicitně vytvořen MEF s na základě názvů metadata zadané vlastnosti.  (To je jedním z několika způsoby, jak získat přístup k metadatům v MEF.)  
  
 Složení v MEF je *rekurzivní*. Můžete explicitně skládá `Program` objekt, který importován `ICalculator` , je typu `MySimpleCalculator`.  `MySimpleCalculator`, pak importuje kolekce `IOperation` objekty a že import bude vyplněno při `MySimpleCalculator` se vytvoří ve stejnou dobu jako importy z `Program`. Pokud `Add` třída deklarována další import, který příliš musel být vyplněna a tak dále. Importovat všechny levé nevyplněný výsledkem chyba složení.  (Je možné, ale deklarovat importy jako volitelnou nebo jim ho přiřadit výchozí hodnoty.)  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a>Kalkulačky logiky  
 Pomocí těchto částí v místě zbývá vlastní logiky kalkulačky. Přidejte následující kód v `MySimpleCalculator` třídu pro implementaci `Calculate` metoda:  
  
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
  
 Počáteční kroky analyzovat vstupní řetězec do levé a pravé operandy a znakem operátor.  V `foreach` cykly, každý člen `operations` je zkontrolován kolekce. Tyto objekty jsou typu <xref:System.Lazy%602>, a jejich hodnoty metadat a exportovaný objekt lze přistupovat pomocí <xref:System.Lazy%602.Metadata%2A> vlastnost a <xref:System.Lazy%601.Value%2A> vlastnost v uvedeném pořadí. V takovém případě pokud `Symbol` vlastnost `IOperationData` objektu byla vyhodnocena jako odpovídající, volání kalkulačky `Operate` metodu `IOperation` objektu a vrátí výsledek.  
  
 K dokončení kalkulačky, musíte taky Pomocná metoda, která vrátí pozici prvního nečíselným znaku v řetězci.  Přidejte následující metodu helper do `MySimpleCalculator` třídy:  
  
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
  
 Teď by měla být moct zkompilování a spuštění projektu. V jazyce Visual Basic, ujistěte se, zda jste přidali `Public` – klíčové slovo k `Module1`. V okně konzoly zadejte operace přidání, například "5 + 3", a kalkulačky vrátí výsledky.  Další operátor bude výsledkem "operaci nebyl nalezen!" Zpráva.  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a>Rozšíření SimpleCalculator pomocí nové třídy  
 Teď, když kalkulačky funguje, přidání nové operaci je snadné. Přidejte následující třídy modulu nebo `SimpleCalculator` obor názvů:  
  
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
  
 Zkompilování a spuštění projektu. Zadejte odčítání operace, jako je například "5-3". Rozhraní kalkulačky teď podporuje odčítání a také přidání.  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Rozšíření SimpleCalculator pomocí nové sestavení  
 Přidávání tříd ke zdroji kód je dostatečně jednoduchá, ale MEF umožňuje hledat částí mimo na aplikace vlastní zdroj. Ukazuje to, budete muset upravit SimpleCalculator k vyhledání adresáře, jakož i vlastní sestavení pro části přidáním <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.  
  
 Přidat nový adresář s názvem `Extensions` do projektu SimpleCalculator.  Ujistěte se, že ho přidat na úrovni projektu a nikoli na úrovni řešení. Pak přidejte nový projekt knihovny tříd do řešení, s názvem `ExtendedOperations`. Nový projekt zkompiluje do samostatné sestavení.  
  
 Otevřete vlastnosti Návrhář projektu ExtendedOperations projektu a klikněte **zkompilovat** nebo **sestavení** kartě. Změna **sestavení výstupní cesta** nebo **výstupní cesta** tak, aby odkazoval na adresář rozšíření v adresáři projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).  
  
 V Module1.vb nebo Program.cs přidejte následující řádek na `Program` konstruktor:  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 Příklad cesty nahraďte cestu k adresáři rozšíření.  (Tato absolutní cesta je pouze pro účely ladění.  V případě produkční aplikace použijete relativní cesta.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teď přidá všechny části v jakékoli sestavení v adresáři rozšíření ke kontejneru složení nalezen.  
  
 V projektu ExtendedOperations přidáte odkazy na SimpleCalculator a System.ComponentModel.Composition. V souboru ExtendedOperations třídy, přidejte `Imports` nebo `using` příkaz pro System.ComponentModel.Composition. V jazyce Visual Basic také přidat `Imports` příkaz pro SimpleCalculator. Do souboru třídy ExtendedOperations přidáte následující třídy:  
  
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
  
 Všimněte si, že v pořadí pro daný kontrakt tak, aby odpovídaly, <xref:System.ComponentModel.Composition.ExportAttribute> atributu musí mít stejný typ jako <xref:System.ComponentModel.Composition.ImportAttribute>.  
  
 Zkompilování a spuštění projektu. Otestujte novou operátor Mod (%).  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Toto téma je zahrnuté se základními koncepty MEF.  
  
-   Části, katalogů a kontejneru složení  
  
     Části a kontejneru složení jsou základní stavební bloky MEF aplikace. Součástí je libovolný objekt, který importuje nebo exportuje hodnotu, do a včetně sám sebe. Katalog poskytuje kolekci částí z určitého zdroje.  Kontejneru složení částí poskytované katalog používá k sestavení, vazba importy pro export.  
  
-   Import a export  
  
     Import a export představují způsob, kterým součásti komunikovat. Importu komponentu určuje potřebu konkrétní hodnota nebo objekt a s exportu určuje dostupnost hodnotu. Každý import je nalezena shoda se seznamem exportuje prostřednictvím její smlouvy.  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a>Kde přejít teď?  
 Si můžete stáhnout kompletní kód v tomto příkladu [SimpleCalculator ukázka](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
 Další informace a příklady kódu najdete v tématu [spravované rozhraní rozšiřitelnosti](http://go.microsoft.com/fwlink/?LinkId=144282). Seznam typů MEF, najdete v článku <xref:System.ComponentModel.Composition?displayProperty=nameWithType> oboru názvů.
