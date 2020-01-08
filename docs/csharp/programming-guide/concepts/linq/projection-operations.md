---
title: Operace projekce (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a2a2ae762d63d5ff26c7018caef1a83558042fb5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346525"
---
# <a name="projection-operations-c"></a>Operace projekce (C#)
Projekce odkazuje na operaci transformace objektu do nového formuláře, který se často skládá pouze z těchto vlastností, které budou následně použity. Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete promítnout vlastnost a na ní provést matematickou funkci. Původní objekt můžete také promítnout beze změny.  
  
 Standardní metody operátoru dotazu, které provádějí projekci, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|, verze Select|Projekty hodnoty, které jsou založeny na transformační funkci.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Operátor SelectMany|Projektuje sekvence hodnot, které jsou založeny na transformační funkci a poté jsou shrnuty do jedné sekvence.|Použít více klauzulí `from`|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="select"></a>, verze Select  
 V následujícím příkladu je použita klauzule `select` pro projekt prvního písmene z každého řetězce v seznamu řetězců.  
  
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
  
### <a name="selectmany"></a>Operátor SelectMany  
 Následující příklad používá více klauzulí `from` pro každé slovo z každého řetězce v seznamu řetězců.  
  
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
  
## <a name="select-versus-selectmany"></a>Vybrat versus operátor SelectMany  
 Jak `Select()`, tak `SelectMany()` je vytvořit výslednou hodnotu (nebo hodnoty) ze zdrojových hodnot. `Select()` vytvoří jednu hodnotu výsledku pro každou zdrojovou hodnotu. Celkový výsledek je tedy kolekce, která má stejný počet prvků jako zdrojová kolekce. Naproti tomu `SelectMany()` vytváří jeden celkový výsledek, který obsahuje zřetězené dílčí kolekce z každé zdrojové hodnoty. Funkce transformace, která je předána jako argument pro `SelectMany()` musí vracet vyčíslitelné sekvence hodnot pro každou zdrojovou hodnotu. Tyto vyčíslitelné sekvence jsou poté zřetězeny `SelectMany()`, aby vytvořily jednu velkou sekvenci.  
  
 Následující dva ilustrace znázorňují koncepční rozdíl mezi akcemi těchto dvou metod. V každém případě Předpokládejme, že funkce Selector (transformace) vybere pole květů z každé zdrojové hodnoty.  
  
 Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojová kolekce.  
  
 ![Obrázek, který zobrazuje akci výběru&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Tento obrázek znázorňuje, jak `SelectMany()` zřetězí mezilehlé pořadí polí do jedné konečné výsledné hodnoty, která obsahuje všechny hodnoty z každého mezilehlého pole.  
  
 ![Obrázek znázorňující akci operátor SelectMany&#40;&#41;](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "kytici" květů z každého seznamu názvů květin ve zdrojové kolekci. V tomto příkladu "jednoduchá hodnota", kterou funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je sám kolekcí hodnot. K tomu je potřeba smyčka extra `foreach`, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [select – klauzule](../../../language-reference/keywords/select-clause.md)
- [Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
