---
title: 'Postupy: Přidání vlastních metod pro dotazů LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: cd282b4b8ee4add759070317d9dbc3f78c07abf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326895"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Postupy: Přidání vlastních metod pro dotazů LINQ (C#)
Můžete rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní metoda aggregate vypočítat jednu hodnotu z pořadí hodnot. Můžete také vytvořit metodu, která funguje jako vlastní nebo konkrétní data transformace pro pořadí hodnot a vrátí nové pořadí. Příkladem takové metody jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Pokud rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít pro jakékoli vyčíslitelná kolekce vlastních metod. Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Přidání agregační metoda  
 Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik metod agregační, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Přidáním metodu rozšíření k můžete vytvořit vlastní metoda aggregate <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 Následující příklad kódu ukazuje, jak vytvořit volat metody rozšíření `Median` vypočítat medián pro pořadí čísel typu `double`.  
  
```csharp  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 Volání této metody rozšíření pro jakoukoli kolekci, výčtové stejným způsobem volání z jiné agregační metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 Následující příklad kódu ukazuje, jak používat `Median` metodu pro pole typu `double`.  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  

```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
*/  
```  
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení metody agregační tak, aby přijímal různých typů  
 Může dojít k přetížení agregační metodu tak, aby přijímá pořadí různých typů. Standardní přístupu je vytvoření přetížení pro každý typ. Další možností je vytvořit přetížení, které bude trvat obecného typu a převést jej do konkrétního typu pomocí delegáta. Můžete také kombinovat obou přístupů.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Chcete-li vytvořit přetížení pro každý typ  
 Můžete vytvořit na konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení `Median` metodu `integer` typu.  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 Nyní můžete volat `Median` přetížení pro obě `integer` a `double` typů, jak je znázorněno v následujícím kódu:  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  
  
```csharp  
int[] numbers2 = { 1, 2, 3, 4, 5 };  
  
var query2 = numbers2.Median();  
  
Console.WriteLine("int: Median = " + query2);  
```  
  
```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
 Integer: Median = 3  
*/  
```  

#### <a name="to-create-a-generic-overload"></a>Chcete-li vytvořit obecné přetížení  
 Můžete také vytvořit přetížení, které přijímá pořadí obecné objektů. Toto přetížení trvá delegáta jako parametr a používá ho převést na určitý typ pořadí objektů obecného typu.  
  
 Následující kód ukazuje přetížení `Median` metody, která přijímá <xref:System.Func%602> delegovat jako parametr. Tento delegát přebírá objekt obecného typu T a vrátí objekt typu `double`.  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Nyní můžete volat `Median` metoda sekvenci objekty libovolného typu. Pokud není typ vlastního přetížení metody, budete muset předání parametru delegáta. V jazyce C# můžete pro tento účel výrazu lambda. Také v jazyce Visual Basic, pouze pokud použijete `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.  
  
 Následující příklad kódu ukazuje způsob volání `Median` metodu pro pole celých čísel a pole řetězců. Pro řetězce je vypočítána Medián pro délky v poli řetězců. Příklad ukazuje, jak předat <xref:System.Func%602> delegovat parametru `Median` metoda pro každý případ.  
  
```csharp  
int[] numbers3 = { 1, 2, 3, 4, 5 };  
  
/*   
  You can use the num=>num lambda expression as a parameter for the Median method   
  so that the compiler will implicitly convert its value to double.  
  If there is no implicit conversion, the compiler will display an error message.            
*/  
  
var query3 = numbers3.Median(num => num);  
  
Console.WriteLine("int: Median = " + query3);  
  
string[] numbers4 = { "one", "two", "three", "four", "five" };  
  
// With the generic overload, you can also use numeric properties of objects.  
  
var query4 = numbers4.Median(str => str.Length);  
  
Console.WriteLine("String: Median = " + query4);  
  
/*  
 This code produces the following output:  
  
 Integer: Median = 3  
 String: Median = 4  
*/  
```   
## <a name="adding-a-method-that-returns-a-collection"></a>Přidání metody, která vrátí kolekci  
 Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s vlastního dotazu metodu, která vrátí pořadí hodnot. V takovém případě metodu musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody lze použít filtry nebo data transformací pořadí hodnot.  
  
 Následující příklad ukazuje, jak vytvořit metody rozšíření s názvem `AlternateElements` , vrátí každý další element v kolekci, od první prvek.  
  
```csharp  
// Extension method for the IEnumerable<T> interface.   
// The method returns every other element of a sequence.  
  
public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)  
{  
    List<T> list = new List<T>();  
  
    int i = 0;  
  
    foreach (var element in source)  
    {  
        if (i % 2 == 0)  
        {  
            list.Add(element);  
        }  
  
        i++;  
    }  
  
    return list;  
}  
```  
 Můžete tuto metodu lze volat rozšíření pro jakoukoli kolekci, výčtové stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:  
  
```csharp  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
