---
title: Výrazy lambda - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 77701653abacbe6d876c0890a11586f0840bad5d
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200894"
---
# <a name="lambda-expressions-c-programming-guide"></a>Výrazy lambda (C# Programming Guide)

Výraz lambda je [anonymní funkce](anonymous-methods.md) , můžete použít k vytvoření [delegáti](../delegates/using-delegates.md) nebo [stromu výrazů](../concepts/expression-trees/index.md) typy. Pomocí výrazů lambda můžete psát místní funkce, které mohou být předány jako argumenty nebo vráceny jako hodnota volání funkce. Výrazy lambda jsou zvláště užitečné pro psaní výrazů dotazů LINQ.
  
Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda [ => ](../../../csharp/language-reference/operators/lambda-operator.md), a umístěte blok výrazu nebo příkazu na druhé straně. Například výraz lambda `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci. Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Postup vytvoření typu stromu výrazu:  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 `=>` Operátor má stejnou prioritu jako přiřazení (`=`) a je [asociativní zprava](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (viz oddíl "Asociativita" operátory článku).  
  
 Výrazy lambda se používají v založených na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů jako argumenty pro standardní metody operátoru dotazu, jako například <xref:System.Linq.Enumerable.Where%2A>.  
  
 Při použití syntaxe založených na volání metody na volání <xref:System.Linq.Enumerable.Where%2A> metoda ve <xref:System.Linq.Enumerable> třídy (stejně jako v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k objektům a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) je parametr typu delegáta <xref:System.Func%602?displayProperty=nameWithType>. Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu. Při volání stejné metody, například <xref:System.Linq.Queryable?displayProperty=nameWithType> třídy (stejně jako v [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) je typ parametru <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> kde Func je libovolný delegát Func s až šestnácti vstupními parametry. Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu. Výrazy lambda umožňují `Where` volání vypadalo podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda jiný.  
  
 V předchozím příkladu, Všimněte si, že podpis delegáta má jeden implicitně zadaný vstupní parametr typu `int`a vrátí `int`. Výraz lambda může být převeden na delegáta daného typu, protože má také jeden vstupní parametr (`x`) a návratovou hodnotu, může kompilátor implicitně převést na typ `int`. (Odvození typu je popsáno podrobněji v následujících částech). Pokud je delegát vyvolán pomocí vstupního parametru 5, vrátí výsledek 25.  
  
 Výrazy lambda nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) nebo [jako](../../../csharp/language-reference/keywords/as.md) operátor.  
  
 Všechna omezení, která platí pro anonymní metody, platí také pro výrazy lambda. Další informace najdete v tématu [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Výrazové lambdy

 Výraz lambda s výrazem na pravé straně = > – operátor je volána *výrazu lambda*. Výrazové lambdy se často používají v konstrukci [stromů výrazů](../concepts/expression-trees/index.md). Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:
  
```csharp
(input-parameters) => expression
```

 Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány. Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:  
  
```csharp
(x, y) => x == y
```

 Někdy je pro kompilátor obtížné či nemožné odvodit vstupní typy. V takovém případě můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:  
  
```csharp
(int x, string s) => s.Length > x
```
 Vstupní parametr typy musí být všechny explicitní, nebo všechny implicitní; v opačném případě jazyka C# vygeneruje [CS0748](../../misc/cs0748.md) chybu kompilátoru.

 Zadejte nulové vstupní parametry s prázdnými závorkami:  
  
```csharp
() => SomeMethod()
```

 V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody. Pokud však vytváříte stromy výrazu, které jsou vyhodnocovány mimo rozhraní .NET Framework, například na SQL Server, neměli byste používat volání metody ve výrazech lambda. Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.  
  
## <a name="statement-lambdas"></a>Příkazové lambdy

 Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:  
  
(vstupní parametry) = > {příkaz;}

 Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.  
  
[!code-csharp[StatementLambda#1](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLambda#2](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#2)]

 Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.  
  
## <a name="async-lambdas"></a>Asynchronní lambdy

 Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) a [await](../../../csharp/language-reference/keywords/await.md) klíčová slova. Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy. Chcete-li přidat tuto obslužnou rutinu, přidejte `async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Výrazy lambda s operátory standardního dotazu

 Mnoho standardních operátorů dotazu má vstupní parametr, jehož typ je jednou z <xref:System.Func%602> řady obecných delegátů. Tyto delegáty používají parametry typu pro definování počtu a typů vstupních parametrů a návratový typ delegátu. `Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat. Zvažte například následující typ delegátu:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Delegát může být vytvořen jako `Func<int,bool> myFunc` kde `int` je vstupní parametr a `bool` je návratová hodnota. Vrácená hodnota je vždy určena v posledním parametru typu. `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`. Následující `Func` delegáta, při vyvolání, vrátí hodnotu true nebo false označuje, zda je vstupní parametr roven hodnotě 5:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Výraz lambda lze také zadat, pokud je typ argumentu `Expression<Func>`, například ve standardních operátorech dotazu, které jsou definovány v System.Linq.Queryable. Pokud zadáte `Expression<Func>` argument, bude lambda kompilována na strom výrazu.  
  
 Standardní operátor dotazu, <xref:System.Linq.Enumerable.Count%2A> metoda, je znázorněna zde:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda vrátí ta celá čísla (`n`) která po vydělení dvěma mají zbytek 1.  
  
 Následující řádek kódu vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které jsou nalevo od hodnoty 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Tento příklad znázorňuje způsob zadávání většího počtu vstupních parametrů uzavřením do závorek. Metoda vrátí všechny prvky v poli čísel, dokud není zjištěno číslo, jehož hodnota je nižší než jeho pozice. Nezaměňujte operátor lambda (`=>`) s operátorem větší než nebo rovno (`>=`).  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Odvození typu proměnné ve výrazech lambda

 Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní části výrazu lambda, typu delegátu parametru a dalších faktorů, jak je popsáno ve specifikaci jazyka C#. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 Obecná pravidla pro výrazy lambda jsou následující:  
  
-   Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.  
  
-   Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.  
  
-   Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.  
  
 Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“. Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda. V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Rozsah proměnné ve výrazech lambda

 Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metodě, která definuje funkci lambda, nebo v rozsahu typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla:  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:  
  
-   Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.  
  
-   Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.  
  
-   Výraz lambda nemůže přímo zachytit `in`, `ref`, nebo `out` parametr z ohraničující metody.  
  
-   Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.  
  
-   Výraz lambda nemůže obsahovat `goto` příkazu `break` příkazu, nebo `continue` příkaz, který se nachází uvnitř funkce lambda, pokud cíl příkazu skoku je mimo blok. Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Doporučená kapitola knihy

 [Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [LINQ (Language-Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [Stromy výrazů](../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 2008 C# – ukázky (viz ukázkové soubory dotazů LINQ a XQuery program)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekurzivní výrazy lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
