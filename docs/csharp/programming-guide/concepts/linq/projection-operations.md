---
title: Projekční operace (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: f76eeeb779ab08a575e758a9d974573b700ae652
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168333"
---
# <a name="projection-operations-c"></a>Projekční operace (C#)
Projekce odkazuje na operaci transformace objektu do nové ho tvaru, který se často skládá pouze z těch vlastností, které budou následně použity. Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete promítat vlastnost a provádět na ní matematickou funkci. Původní objekt můžete také promítat bez změny.  
  
 Standardní metody operátoru dotazu, které provádějí projekci, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Vyberte|Projekty hodnoty, které jsou založeny na funkci transformace.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Selectmany|Projekty sekvence hodnot, které jsou založeny na funkci transformace a pak je sloučí do jedné sekvence.|Použití `from` více klauzulí|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="select"></a>Vyberte  
 Následující příklad používá `select` klauzuli k promítat první písmeno z každého řetězce v seznamu řetězců.  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a>Selectmany  
 Následující příklad používá `from` více klauzulí k promítat každé slovo z každého řetězce v seznamu řetězců.  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a>Vybrat versus SelectMany  
 Práce obou `Select()` a `SelectMany()` je vytvořit výslednou hodnotu (nebo hodnoty) ze zdrojových hodnot. `Select()`vytvoří jednu výslednou hodnotu pro každou zdrojové hodnoty. Celkový výsledek je proto kolekce, která má stejný počet prvků jako zdroj kolekce. Naopak vytvoří `SelectMany()` jeden celkový výsledek, který obsahuje zřetězené dílčí kolekce z každé zdrojové hodnoty. Funkce transformace, která je předána jako argument, `SelectMany()` musí vrátit výčet posloupnosti hodnot pro každou zdrojovou hodnotu. Tyto výčet sekvence jsou pak zřetězené vytvořit jednu `SelectMany()` velkou sekvenci.  
  
 Následující dva obrázky ukazují koncepční rozdíl mezi akcemi těchto dvou metod. V každém případě předpokládejme, že funkce selektoru (transformace) vybere pole květin z každé zdrojové hodnoty.  
  
 Tento obrázek `Select()` znázorňuje, jak vrátí kolekci, která má stejný počet prvků jako zdrojkolekce.  
  
 ![Obrázek znázorněný akcí možnosti Vybrat&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Tento obrázek `SelectMany()` znázorňuje, jak zřetězí mezilehlou sekvenci polí do jedné konečné výsledné hodnoty, která obsahuje každou hodnotu z každého zprostředkujícího pole.  
  
 ![Obrázek znázorňující akci selectmany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytváří "kytici" květin tím, že první dvě položky z každého seznamu názvů květin ve zdrojové sbírce. V tomto příkladu "single value", <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> který používá funkce transformace je sama o sobě kolekce hodnot. To vyžaduje `foreach` další smyčky, aby výčet každý řetězec v každé dílčí sekvence.  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [select – klauzule](../../../language-reference/keywords/select-clause.md)
- [Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Jak rozdělit soubor do mnoha souborů pomocí skupin (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
