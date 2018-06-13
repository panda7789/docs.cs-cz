---
title: Operace projekce (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a044982c21246fd4e8c1cbdbb9801ae7b29d05c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335387"
---
# <a name="projection-operations-c"></a>Operace projekce (C#)
Projekce odkazuje na operaci transformace objekt do nový formulář, který často se skládá jenom z těchto vlastností, které budou následně použity. Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu. Můžete projektu vlastnosti a na něm provádět matematické funkce. Můžete také promítnout původní objekt bez provedení změn.  
  
 Metody operátor standardní dotaz, které provádějí projekce jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Vyberte|Projekty hodnoty, které jsou založeny na funkce transformace.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Označit více|Projekty pořadí hodnot, které jsou založeny na funkce transformace a pak sloučí je do jedné sekvence.|Použití více `from` – klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="select"></a>Vyberte  
 Následující příklad používá `select` klauzule do projektu první písmeno z každé řetězec v seznamu řetězců.  
  
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
  
### <a name="selectmany"></a>Označit více  
 Následující příklad používá více `from` klauzule do projektu jednotlivých slov z každé řetězec v seznamu řetězců.  
  
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
  
## <a name="select-versus-selectmany"></a>Vyberte a označit více  
 Pracovní i `Select()` a `SelectMany()` z hodnot zdroj je vytvořit hodnotu výsledek (nebo hodnoty). `Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu. Kolekce, která má stejný počet elementů jako zdrojové kolekci je proto celkový výsledek. Naproti tomu `SelectMany()` vytváří jeden celkový výsledek, který obsahuje zřetězených podřízených kolekcí z každé zdrojové hodnotě. Funkce transformace, který je předán jako argument pro `SelectMany()` musí vrátit vyčíslitelná pořadí hodnot pro každou hodnotu zdroje. Tyto vyčíslitelná pořadí jsou pak zřetězených podle `SelectMany()` vytvoření jeden velký pořadí.  
  
 Následující dva obrázky ukazují koncepční rozdíl mezi tyto dvě metody akce. V každém případě předpokládá, že funkce selektor (transformace) vybere pole květy z každé zdrojové hodnoty.  
  
 Tento obrázek znázorňuje způsob `Select()` vrátí kolekce, která má stejný počet elementů jako zdrojové kolekci.  
  
 ![Koncepční obrázek akce vyberte&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Tento obrázek znázorňuje způsob `SelectMany()` zřetězí zprostředkující pořadí polí do jednu hodnotu konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.  
  
 ![Obrázek znázorňující akce označit více&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Označit více")  
  
### <a name="code-example"></a>Příklad kódu  
 Následující příklad porovnává chování `Select()` a `SelectMany()`. Kód vytvoří "bouquet" květy provedením první dvě položky z každé seznam názvů květina ve zdrojové kolekci. V tomto příkladu "jedna hodnota", transformační funkce <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je sám kolekci hodnot. To vyžaduje nadbytečné `foreach` smyčky, aby bylo možné vytvořit výčet každý řetězec v každé dílčí pořadí.  
  
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
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [select – klauzule](../../../../csharp/language-reference/keywords/select-clause.md)  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
