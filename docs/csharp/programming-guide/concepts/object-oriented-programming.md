---
title: Objektově orientované programování (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6da28e97a33e962d4926a3b65d0fdf388c252d9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="object-oriented-programming-c"></a>Objektově orientované programování (C#)
C# poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnost a polymorfismus.  
  
 *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.  
  
 *Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídy.  
  
 *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zcela zaměnitelným významem, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.  
  
 Tato část popisuje následující koncepty:  
  
-   [Třídy a objekty](#Classes)  
  
    -   [Členy třídy](#Members)  
  
         [Vlastnosti a pole](#Properties)  
  
         [Metody](#Methods)  
  
         [Konstruktory](#Constructors)  
  
         [Finalizační metody](#Finalizers)  
  
         [Události](#Events)  
  
         [Vnořené třídy](#NestedClasses)  
  
    -   [Modifikátory přístupu a úrovně přístupu](#AccessModifiers)  
  
    -   [Vytváření instancí třídy](#InstantiatingClasses)  
  
    -   [Statické třídy a členové](#Static)  
  
    -   [Anonymní typy](#AnonymousTypes)  
  
-   [Dědičnost](#Inheritance)  
  
    -   [Přepis členů](#Overriding)  
  
-   [Rozhraní](#Interfaces)  
  
-   [Obecné typy](#Generics)  
  
-   [Delegáti](#Delegates)  
  
##  <a name="Classes"></a> Třídy a objekty  
 Podmínky *třída* a *objekt* se někdy používají zcela zaměnitelným významem, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd. Ano, je volána v rámci vytvoření objektu *vytváření instancí*. Pomocí analogie plán, podle kterého, třída je plán, podle kterého a v budově z tento plán, podle kterého je objekt.  
  
 Chcete-li definovat třídu:  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 C# také poskytuje světla verzi třídy názvem *struktury* , jsou užitečné, když potřebujete vytvořit velké pole objektů a proveďte využívat příliš mnoho paměti, pro který chcete.  
  
 Chcete-li definovat strukturu:  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 Další informace naleznete v tématu:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> Členy třídy  
 Každá třída může mít různé *třídy členy* , zahrnout vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které zajišťují komunikaci mezi různými třídami a objekty.  
  
####  <a name="Properties"></a> Vlastnosti a pole  
 Pole a vlastnosti představují informací, které obsahuje objekt. Pole jsou jako proměnné, protože můžou být číst nebo nastavovat přímo.  
  
 Chcete-li definovat pole:  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 Vlastnosti mají get a nastavte postupů, které poskytuje větší kontrolu na tom, jak nastavit nebo vrátil hodnoty.  
  
 C# můžete buď vytvořit soukromé pole pro ukládání hodnota vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí, které poskytují základní logiku pro vlastnost postupy.  
  
 Chcete-li definovat ve automaticky implementované vlastnosti:  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Pokud potřebujete provést některé další operace pro čtení a zápis hodnota vlastnosti definice pole pro ukládání hodnota vlastnosti a poskytují základní logiku pro ukládání a načítání ho:  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 Většina vlastnosti mají metody nebo postupy, jak nastavit a získat hodnotu vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení, nebo jen pro zápis je omezit změnit nebo načíst. V jazyce C#, můžete vynechat `get` nebo `set` metoda property. Automaticky implementované vlastnosti však nemůže být jen pro čtení nebo jen pro zápis.  
  
 Další informace naleznete v tématu:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> Metody  
 A *metoda* je akce, která může provádět objekt.  
  
 Definovat metodu třídy:  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se budou lišit v počtu parametry nebo typy parametrů.  
  
 Chcete-li přetížení metody:  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 Ve většině případů deklarujte metodu v definici třídy. Však C# také podporuje *rozšiřující metody* které umožňují přidání metody do existující třídy mimo skutečné definice třídy.  
  
 Další informace naleznete v tématu:  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> Konstruktory  
 Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializovat datových členů nového objektu. Konstruktor lze spustit pouze po vytvoření třídy. Kromě toho kód v konstruktoru vždy spouští před jakýkoli jiný kód v třídě. Můžete však vytvořit více přetížení konstruktor stejným způsobem jako u jakékoliv jiné metody.  
  
 Chcete-li definovat konstruktor pro třídu:  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 Další informace naleznete v tématu:  
  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).  
  
####  <a name="Finalizers"></a> Finalizační metody  
 Finalizační metody se používají k destruct instance tříd. V rozhraní .NET Framework bude systém uvolňování automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci. Mohou však stále zapotřebí finalizační metody vyčistit všechny nespravovaných prostředků, které vytváří vaše aplikace. Může existovat pouze jedna finalizační metody pro třídu.  
  
 Další informace o finalizační metody a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
####  <a name="Events"></a> Události  
 Události povolit třídu nebo objekt, který chcete upozornit ostatní třídy nebo objekty, když něco zájmu dojde. Třída, která odešle (nebo vyvolá) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *Odběratelé, kteří*. Další informace o událostech, způsob jejich jsou vyvolány a zpracovávají, najdete v části [události](../../../standard/events/index.md).  
  
-   Chcete-li deklarovat událost v třídě, použijte [událostí](../../../csharp/language-reference/keywords/event.md) – klíčové slovo.  
  
-   Vyvolat událost, vyvolání delegáta události.  
  
-   K odběru události, použijte `+=` operátor; k odhlášení odběru událostí, použijte `-=` operátor.  
  
####  <a name="NestedClasses"></a> Vnořené třídy  
 Třídy definované v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení je vnořené třídy soukromé.  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 K vytvoření instance třídy vnořené, použijte název třídy kontejneru, za nímž následuje tečky a po ní následuje název vnořené třídy:  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> Modifikátory přístupu a úrovně přístupu  
 Všechny třídy a jejich členové můžete určit, jakou úroveň přístupu poskytují další třídy pomocí *přístup modifikátory*.  
  
 K dispozici jsou následující modifikátory přístupu:  
  
|C# – modifikátor|Definice|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|Typ nebo člen je přístupná jiným kódem ve stejném sestavení nebo jiné sestavení, které na ni odkazuje.|  
|[private](../../../csharp/language-reference/keywords/private.md)|Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě nebo v odvozené třídě.|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|Typ nebo člen je přístupný kód ve stejném sestavení, ale nikoli z jiné sestavení.|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Typ nebo člen je přístupná žádný kód ve stejném sestavení, nebo všechny odvozené třídy v jiném sestavení.|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Typ nebo člen je přístupný kód ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.|  
  
 Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
###  <a name="InstantiatingClasses"></a> Vytváření instancí třídy  
 Pro vytvoření objektu, musíte vytvořit instanci třídy, nebo vytvořit instanci třídy.  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a vyvolání metody třídy.  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Chcete-li přiřadit hodnoty k vlastnosti během procesu vytváření instancí třídy, použijte inicializátory objektů:  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Další informace naleznete v tématu:  
  
-   [new – operátor](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> Statické třídy a členové  
 Statický člen třídy je vlastnost, postup nebo pole, které platí pro všechny instance třídy.  
  
 Chcete-li definovat je statický člen:  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Pro přístup k statický člen, použijte název třídy bez vytvoření objektu této třídy:  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 Statické třídy v jazyce C# mají jenom statické členy a nelze vytvořit instanci. Statické členy také přístup k vlastnosti nestatické, pole a metody  
  
 Další informace najdete v tématu: [statické](../../../csharp/language-reference/keywords/static.md).  
  
###  <a name="AnonymousTypes"></a> Anonymní typy  
 Anonymní typy umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ. Kompilátor místo, vygeneruje třídu pro vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklarace objektu.  
  
 Chcete-li vytvořit instanci anonymního typu:  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Další informace najdete v tématu: [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
##  <a name="Inheritance"></a> dědičnost  
 Dědičnost umožňuje vytvořit novou třídu, která opětovně používá rozšiřuje a mění chování, která je definována v jiné třídy. Je volána třídu, jejíž členové jsou děděné *základní třída*, a třídu, která dědí členů, se nazývá *odvozené třídy*. Ale všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchie tříd rozhraní .NET a poskytuje nižší úroveň služby pro všechny třídy.  
  
> [!NOTE]
>  C# nepodporuje vícenásobná dědičnost. To znamená můžete zadat pouze jeden základní třídu pro odvozené třídy.  
  
 Chcete-li zdědit ze základní třídy:  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 Ve výchozím nastavení může být dědí všechny třídy. Však můžete určit, zda nesmí používat jako základní třída třídy, nebo vytvořte třídu, která lze použít jako základní třídy.  
  
 Chcete-li určit, že třídy nelze použít jako základní třída:  
  
```csharp  
public sealed class A { }  
```  
  
 K určení, že třídy lze použít jako základní třída a nelze vytvořit instanci:  
  
```csharp  
public abstract class B { }  
```  
  
 Další informace naleznete v tématu:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> Přepis členů  
 Ve výchozím nastavení odvozené třídy dědí všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného členu, budete muset přepsat. To znamená můžete definovat nové implementace metoda, vlastnost nebo události v odvozené třídě.  
  
 Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:  
  
|C# – modifikátor|Definice|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umožňuje člena třídy k přepsání v odvozené třídě.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Přepsání člena virtuální (přepisovatelné) definované v základní třídě.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Vyžaduje, aby člena třídy k přepsání v odvozené třídě.|  
|[new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md)|Skryje členem zděděn ze základní třídy|  
  
##  <a name="Interfaces"></a> Rozhraní  
 Rozhraní, jako jsou třídy, definovat sadu vlastností, metod a události. Ale na rozdíl od třídy, rozhraní neposkytují implementace. Jsou implementované třídy a definován jako samostatné entity z tříd. Rozhraní představuje kontraktu, v tomto třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.  
  
 Definice rozhraní:  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 K implementaci rozhraní v třídě:  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 Další informace naleznete v tématu:  
  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> Obecné typy  
 Třídy, struktury, rozhraní a metody v rozhraní .NET Framework může zahrnovat *parametry typu* , definování typů objektů, které lze uložit nebo použít. Nejčastější obecných typů je kolekce, kde můžete určit typ objektů, které chcete uložit v kolekci.  
  
 Zadat obecné třídy:  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Chcete-li vytvořit instanci obecné třídy:  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Další informace naleznete v tématu:  
  
-   [Obecné typy](~/docs/standard/generics/index.md)  
  
-   [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> Delegáti  
 A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu kompatibilní podpisem. Můžete vyvolat (nebo volání) metoda prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.  
  
> [!NOTE]
>  Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).  
  
 Pokud chcete vytvořit delegáta:  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 Pokud chcete vytvořit odkaz na metodu, která odpovídá podpis určeného delegát:  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 Další informace naleznete v tématu:  
  
-   [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
