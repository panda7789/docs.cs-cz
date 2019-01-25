---
title: Operace projekce (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: fa9b1d2a0dc63be89e8a93fd5d234f131a2943e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723950"
---
# <a name="projection-operations-c"></a>Operace projekce (C#)
Projekce odkazuje na operace transformace objektu na nový formulář, který často se skládá pouze z těchto vlastností, které se následně použijí. S použitím projekce, můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete vlastnosti projektu a provádění matematických funkcí na něj. Můžete také promítnout na původní objekt bez provedení změn.  
  
 V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí projekce.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Vyberte|Projekty hodnoty, které jsou založeny na funkce transformace.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projekty pořadí hodnot, které jsou založeny na funkce transformace a sloučí je do jedné sekvence.|Použití více `from` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="select"></a>Vyberte  
 V následujícím příkladu `select` klauzuli do projektu první písmeno každého řetězce v seznamu řetězců.  
  
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
  
### <a name="selectmany"></a>SelectMany  
 Následující příklad používá více `from` klauzule do projektu všechna slova ze každý řetězec v seznamu řetězců.  
  
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
  
## <a name="select-versus-selectmany"></a>Vyberte a operátor SelectMany  
 Práce z obou `Select()` a `SelectMany()` je výsledná hodnota (nebo hodnoty) ze zdrojové hodnoty. `Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu. Celkový výsledek je proto kolekci, která má stejný počet prvků jako zdrojové kolekce. Naproti tomu `SelectMany()` jeden celkový výsledek, který obsahuje zřetězených podřízené kolekce od všech hodnot zdroje. Funkce transformace, která je předána jako argument `SelectMany()` musí vracet vyčíslitelné posloupnost hodnot pro každou zdrojovou hodnotu. Tyto vyčíslitelné sekvence jsou pak zřetězeny podle `SelectMany()` vytvořte jedno velké pořadí.  
  
 Následující dva obrázky ukazují konceptuální rozdíl mezi akcemi z těchto dvou metod. V obou případech se předpokládá, že funkce selektor (transformace) vybere z každé zdrojové hodnoty pole květin.  
  
 Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojové kolekce.  
  
 ![Ilustrace akci vyberte&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Tento obrázek znázorňuje, jak `SelectMany()` zřetězí zprostředkující pořadí polí do jedné hodnoty konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.  
  
 ![Obrázek znázorňující akce operátor SelectMany&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operátor SelectMany")  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "kytice" květin díky první dvě položky z každého seznam názvů květinu ve zdrojové kolekce. V tomto příkladu "jedna hodnota", který funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je samotný kolekci hodnot. To vyžaduje, aby nadbytečné `foreach` smyčky, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.  
  
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
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [select – klauzule](../../../../csharp/language-reference/keywords/select-clause.md)
- [Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
