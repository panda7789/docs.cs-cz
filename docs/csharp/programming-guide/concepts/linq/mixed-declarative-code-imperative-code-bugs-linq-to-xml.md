---
title: Smíšeného deklarativního a imperativního kódu chyby (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 56d8140613f3dae7f99c1374634dbd8bdf094a7c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799772"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Smíšený kód deklarativní nebo imperativní kód chyby (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje různé metody, které umožňují upravit stromu XML přímo. Můžete přidat prvky, odstranění prvků, změňte obsah elementu, přidejte atributy a tak dále. Toto programovací rozhraní je popsán v [změna stromů XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Pokud jste se provede iterace přes jeden z OS, jako <xref:System.Xml.Linq.XContainer.Elements%2A>a jak iterovat na ose upravujete stromu XML, můžete skončit s některé chyby neobvyklé.  
  
 Tento problém se někdy označuje jako "The Halloweenem problém".  
  
## <a name="definition-of-the-problem"></a>Definice problému  
 Při psaní kódu s využitím LINQ, který Iteruje přes kolekci jsou deklarativní stylem psaní kódu. Se více podobají popisující *co* chcete, místo toho, který *jak* chcete pracovat efektivněji. Pokud píšete kód, který 1) získá první prvek, 2) testy se některé podmínky, 3) upraví jeho a 4) vloží jej zpět do seznamu, pak by to imperativního kódu. Oznamujete tím počítače *jak* udělat, co chcete Hotovo.  
  
 Kombinování tyto styly kódu v rámci jedné operace je co vede k problémům. Vezměte v úvahu následující:  
  
 Předpokládejme, že v něm máte odkazovaného seznamu se tři položky (a, b a c):  
  
 `a -> b -> c`  
  
 Nyní předpokládejme, že chcete přesunout prostřednictvím propojeného seznamu přidáte tři nové položky (", b" a jazyka c "). Chcete, aby výsledný odkazovaného seznamu vypadat nějak takto:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Proto můžete napsat kód, který Iteruje přes seznam a pro každou položku, přidá nové právo položku za ním. Co se stane, je, že váš kód se nejprve zobrazí `a` elementu a vložit `a'` po něm. Nyní, váš kód se přesune na další uzel v seznamu, který je teď `a'`! Využívá elastic přidá novou položku do seznamu, `a''`.  
  
 Jak by vás tento problém vyřešit v reálném světě? Dobře můžete vytvořit kopii původní propojeného seznamu a vytvořit zcela nový seznam. Nebo pokud vytváříte čistě imperativního kódu, můžete se setkat na první položku Přidat novou položku a pak přejděte dvakrát v propojeném seznamu posunutí je nad prvkem, který jste právě přidali.  
  
## <a name="adding-while-iterating"></a>Přidání během iterace  
 Předpokládejme například, že chcete napsat kód pro každý element ve stromové struktuře chcete vytvořit duplicitní element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Tento kód přejde do nekonečné smyčky. `foreach` Příkaz prochází `Elements()` osy, přidávání nových elementů do `doc` elementu. To končí také iterace prvků, které právě přidali. A vzhledem k tomu, že ji přidělí nové objekty při každé iteraci smyčky, budou nakonec spotřebovávat veškerou dostupnou paměť.  
  
 Tento problém můžete vyřešit přidáním kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> standardní operátor dotazu, následujícím způsobem:  
  
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
  
## <a name="deleting-while-iterating"></a>Odstraňuje se během iterace  
 Pokud chcete odstranit všechny uzly na určité úrovni, můžete mít tendenci psát kód podobný tomuto:  
  
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
  
 Ale to není nutné co chcete. V takovém případě po odebrání prvního prvku, A odebere se ze stromu XML obsažených v kořenovém adresáři a kód v metodě prvků, který provádí iteraci nelze najít další prvek.  
  
 Předcházející kód vygeneruje následující výstup:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Toto řešení je opět volání <xref:System.Linq.Enumerable.ToList%2A> sloučit kolekci, následujícím způsobem:  
  
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
  
 To vytvoří následující výstup:  
  
```xml  
<Root />  
```  
  
 Alternativně můžete eliminovat iterace úplně voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Proč nelze LINQ umožňují automaticky zpracovat to?  
 Jedním z přístupů je vždy přenést vše do paměti namísto provádění opožděné vyhodnocení. Nicméně by bylo velmi náročné z hlediska výkonu a paměti. Ve skutečnosti LINQ a (LINQ to XML) byly pro tento postup, je selže v reálných situacích.  
  
 Další z možných způsobů je vložit nějaký druh transakce syntaxe na LINQ a mít kompilátoru pokus o analýzu kódu a určit, pokud materializace potřeba žádné konkrétní kolekce. Pokus o určení veškerý kód, který má vedlejší účinky je ale mimořádně složité. Vezměte v úvahu následující kód:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Tyto analýzy kódu by bylo potřeba analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volat k určení, pokud žádný kód má vedlejší účinky. Ale analýzy kódu nelze právě hledat jakýkoli kód, který má vedlejší účinky. Je potřeba zvolit pro přesně takový kód, který má vedlejší účinky na podřízených elementů `root` v této situaci.  
  
 Technologie LINQ to XML nebude pokoušet provést tyto analýzy.  
  
 Je vás, abyste se těmto problémům vyhnuli.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Nekombinujte nejprve deklarativního a imperativního kódu.  
  
 I v případě, že víte přesně sémantiku kolekce a sémantika metody, které určuje stromu XML, pokud napsání chytřejší kódu, které se vyhýbají tyto druhy problémů, váš kód bude nutné udržovat jinými vývojáři v budoucnu , a nemusí být jako prostý na problémy. Pokud kombinujete deklarativního a imperativního programování styly, bude váš kód více křehký.  
  
 Pokud píšete kód, který bude realizována kolekce tak, aby se vyhnout těmto problémům, poznamenejte si ji s komentáři, případně ve vašem kódu tak, aby programátoři údržba bude porozumět danému problému.  
  
 Za druhé Pokud výkon a další důležité informace povolit, použijte pouze deklarativního kódu. Neupravujte vaše stávající stromu XML. Vygenerujte nový token.  
  
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
  
## <a name="see-also"></a>Viz také

- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
