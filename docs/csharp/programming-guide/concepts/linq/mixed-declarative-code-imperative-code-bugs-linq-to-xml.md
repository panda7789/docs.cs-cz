---
title: Smíšené deklarativní chyby kódu imperativní kód (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 76a9bb5abf6ce2700a2a0698ebc109f65e2b7eb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168346"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Smíšené deklarativní chyby kódu/imperativního kódu (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsahuje různé metody, které umožňují přímo upravit strom XML. Můžete přidávat prvky, odstraňovat prvky, měnit obsah prvku, přidávat atributy a tak dále. Toto programovací rozhraní je popsáno [v úpravě stromů XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md). Pokud iterace prostřednictvím jedné z os, jako je například <xref:System.Xml.Linq.XContainer.Elements%2A>, a upravujete strom XML při iterace přes osu, můžete skončit s některé podivné chyby.  
  
 Tento problém je někdy známý jako "Halloween problém".  
  
## <a name="definition-of-the-problem"></a>Definice problému  
 Při psaní některého kódu pomocí LINQ, který iteruje prostřednictvím kolekce, píšete kód v deklarativním stylu. Je to více podobně jako popis toho, *co* chcete, spíše to, *jak* chcete, aby si to udělat. Pokud napíšete kód, který 1) získá první prvek, 2) testuje pro některé podmínky, 3) upraví jej a 4) vloží zpět do seznamu, pak by to bylo nutné kód. Říkáte počítači, *jak* dělat to, co chcete udělat.  
  
 Míchání těchto stylů kódu ve stejné operaci je to, co vede k problémům. Zvažte použití těchto zdrojů:  
  
 Předpokládejme, že máte propojený seznam se třemi položkami (a, b a c):  
  
 `a -> b -> c`  
  
 Nyní předpokládejme, že chcete procházet propojený seznam a přidat tři nové položky (a', b' a c'). Chcete, aby výsledný propojený seznam vypadal takto:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Takže napíšete kód, který itetuje prostřednictvím seznamu a pro každou položku přidá novou položku hned za ním. Co se stane, je, `a` že váš `a'` kód nejprve zobrazí prvek a vložit za něj. Nyní se váš kód přesune do dalšího uzlu v `a'`seznamu, což je nyní! To šťastně přidá novou položku `a''`do seznamu, .  
  
 Jak byste to vyřešili ve skutečném světě? No, můžete vytvořit kopii původního propojeného seznamu, a vytvořit zcela nový seznam. Nebo pokud píšete čistě imperativní kód, můžete najít první položku, přidat novou položku a potom dvakrát postoupit v propojeném seznamu a posunit se přes prvek, který jste právě přidali.  
  
## <a name="adding-while-iterating"></a>Přidání při iterace  
 Předpokládejme například, že chcete napsat nějaký kód, který pro každý prvek ve stromu chcete vytvořit duplicitní prvek:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Tento kód přejde do nekonečné smyčky. Příkaz `foreach` iterates přes `Elements()` osu, přidání `doc` nových prvků do prvku. To skončí iterace i prostřednictvím prvků, které právě přidal. A protože přiděluje nové objekty s každou iteraci smyčky, nakonec spotřebuje všechny dostupné paměti.  
  
 Tento problém můžete vyřešit vytažením <xref:System.Linq.Enumerable.ToList%2A> kolekce do paměti pomocí standardního operátoru dotazu, a to následujícím způsobem:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 Nyní kód funguje. Výsledný strom XML je následující:  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a>Odstranění při iterace  
 Pokud chcete odstranit všechny uzly na určité úrovni, můžete být v pokušení napsat kód, jako je následující:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 To však nedělá to, co chcete. V takovém případě po odebrání první prvek, A, je odebrán ze stromu XML obsažené v kořenovém adresáři a kód v Elements metoda, která dělá iterace nelze najít další prvek.  
  
 Předchozí kód vytváří následující výstup:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Řešením je opět <xref:System.Linq.Enumerable.ToList%2A> volat k zhmotnění kolekce, a to následovně:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Výsledkem je následující výstup:  
  
```xml  
<Root />  
```  
  
 Alternativně můžete eliminovat iterace úplně <xref:System.Xml.Linq.XElement.RemoveAll%2A> voláním na nadřazený prvek:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Proč to linq nemůže automaticky zpracovat?  
 Jedním z přístupů by bylo vždy přinést vše do paměti namísto toho, aby opožděné hodnocení. Nicméně, to by bylo velmi drahé, pokud jde o výkon a využití paměti. Ve skutečnosti, pokud LINQ a (LINQ na XML) byly tento přístup, by se nezdaří v reálných situacích.  
  
 Dalším možným přístupem by bylo vložit nějakou syntaxi transakce do LINQ a mít kompilátor pokus o analýzu kódu a zjistit, zda je třeba zhmotnit nějakou konkrétní kolekci. Však pokus o určení všech kód, který má vedlejší účinky je neuvěřitelně složité. Uvažujte následující kód:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Takový kód analýzy by bylo třeba analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volal, k určení, pokud nějaký kód měl vedlejší účinky. Ale kód analýzy nemohl jen hledat žádný kód, který měl vedlejší účinky. Bude muset vybrat pouze pro kód, který měl vedlejší `root` účinky na podřízené prvky v této situaci.  
  
 LINQ na XML se nepokouší provést žádnou takovou analýzu.  
  
 Je na vás, abyste se těmto problémům vyhnuli.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Za prvé, nemíchejte deklarativní a imperativní kód.  
  
 I v případě, že přesně znáte sémantiku vašich sbírek a sémantiku metod, které upravují strom XML, pokud napíšete nějaký chytrý kód, který se těmto kategoriím problémů vyhne, bude váš kód muset v budoucnu udržovat jiní vývojáři a nemusí být v otázkách tak jasné. Pokud smícháte deklarativní a imperativní styly kódování, váš kód bude křehčí.  
  
 Pokud napíšete kód, který zhmotní kolekci tak, aby se tyto problémy vyhnout, poznamenejte si s komentáři podle potřeby ve vašem kódu, takže programátoři údržby bude rozumět problému.  
  
 Za druhé, pokud výkon a další aspekty umožňují, použijte pouze deklarativní kód. Neupravujte existující strom XML. Vygenerujte nový.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
