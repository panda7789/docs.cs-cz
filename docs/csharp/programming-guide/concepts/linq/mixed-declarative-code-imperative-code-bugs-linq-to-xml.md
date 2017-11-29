---
title: "Smíšený kód deklarativní imperativní kód chyby (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 328a266d910e57dc089991ead5fe09a87e722688
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>Smíšený kód deklarativní nebo imperativní kód chyby (technologie LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsahuje různé metody, které vám umožní změnit strom XML přímo. Můžete přidat elementy, odstraňte prvky, změňte obsah elementu, přidání atributů a podobně. Toto programovací rozhraní je popsaná v [úpravy stromů XML (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Pokud jste se iterace v rámci některá z OS, například <xref:System.Xml.Linq.XContainer.Elements%2A>a budete upravovat stromu XML jako iterace ose, můžou skončit s některé neznámé chyby.  
  
 Tento problém se někdy označuje jako "Potíží s Masopust".  
  
## <a name="definition-of-the-problem"></a>Definice problému  
 Při psaní kódu s využitím LINQ, který iteruje v rámci kolekce jsou psaní kódu v deklarativní stylu. Se více podobají popisující *co* chcete, místo, *jak* chcete ho provést. Pokud napíšete kód, který 1) získá první prvek, 2) testy pro některé podmínky, 3) upraví ho a 4) vloží ho zpět do seznamu, pak bude nutné kódu. Oznamujete počítač *jak* udělat, co chcete Hotovo.  
  
 Kombinování tyto styly kódu v rámci jedné operace je co vede k problémům. Zvažte následující:  
  
 Předpokládejme, že máte odkazovaného seznamu s tři položky v něm (a, b a c):  
  
 `a -> b -> c`  
  
 Nyní předpokládejme, že chcete přesunout prostřednictvím odkazovaného seznamu přidání tři nové položky (", b" a c'). Je vhodné výsledné odkazovaného seznamu vypadat takto:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Tak psát kód, který iteruje prostřednictvím seznamu a pro každou položku přidá novou položku vpravo za ním. Co se stane, je, že se nejprve zobrazí kódu `a` prvku a vložení `a'` za ním. Nyní se váš kód přesune na další uzel v seznamu, který je nyní `a'`! Brouka přidá novou položku do seznamu, `a''`.  
  
 Jak by vám vyřešit to v praxi? Dobře můžete vytvořit kopii původního odkazovaného seznamu a vytvořit zcela nový seznam. Nebo pokud vytváříte čistě imperativní kód, můžete zjistit, první položka přidat novou položku a pak dvakrát v seznamu propojené přechodu přes elementu, který jste právě přidali zálohy.  
  
## <a name="adding-while-iterating"></a>Přidání při iterace  
 Předpokládejme například, že chcete napsat kód, že pro každý element ve stromu, kterou chcete vytvořit duplicitní element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Tento kód přejde do nekonečné smyčce. `foreach` Příkaz iteruje `Elements()` osy, přidávání nových elementů do `doc` elementu. Ho ukončí si také iterace v rámci prvky, které právě přidali. A protože přiděluje nový objekty s každou iteraci smyčky, bude nakonec využívat všechny dostupné paměti.  
  
 Tento problém můžete vyřešit přidáváním kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> operátor standardní dotazu, následujícím způsobem:  
  
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
  
## <a name="deleting-while-iterating"></a>Odstraňování při iterace  
 Pokud chcete odstranit všechny uzly na určité úrovni, může být tendenci napsat kód, podobně jako tento:  
  
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
  
 Ale to neprovádí co chcete použít. V takovém případě po odebrání první prvek A, odebere se ze stromu XML obsažených v kořenové a kód v metodě elementy, který provádí iterace nelze najít na další prvek.  
  
 Předchozí kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Řešení, znovu je volání <xref:System.Linq.Enumerable.ToList%2A> do kolekce, vyhodnotit takto:  
  
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
  
 Alternativně můžete eliminovat iterace zcela voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Proč nelze LINQ zpracovávat automaticky to?  
 Jeden z přístupů by vždy všechno zařazení do paměti namísto provádění opožděné vyhodnocení. Ale je velmi náročná z hlediska výkonu a paměti použití. Ve skutečnosti Pokud LINQ a (technologie LINQ to XML) byly pro tento postup, je by selhání v reálných situacích.  
  
 Další možné přístup by mohla být chápat nějaká syntaxe transakce do LINQ a kompilátoru pokusil analyzovat kód a určit, pokud vyžaduje potřeba žádné konkrétní kolekce. Při pokusu o určení všechen kód, který má vedlejší účinky je však velmi složitý. Vezměte v úvahu následující kód:  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Takový kód analysis by bylo nutné analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody voláno k určení, pokud žádný kód měl vedlejší účinky. Ale kód analysis nelze právě vyhledejte kód, který měl vedlejší účinky. Je potřeba zvolit pro pouze kód, který měl vedlejší účinky na podřízených elementů `root` v této situaci.  
  
 Technologie LINQ to XML se nebude pokoušet provést tyto analýzy.  
  
 Můžete se rozhodnout, nechcete-li tyto problémy.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Nejprve nemíchat deklarativní a imperativní kódu.  
  
 I v případě, že znáte přesně sémantika kolekce a sémantika metody, které upravit stromu XML zápisu některé inteligentní kód, který zabraňuje těchto kategorií problémy, bude nutné udržovat jinými vývojáři v budoucnu kódu , a nemusí být jako prostý na problémy. Pokud kombinujete deklarativní a imperativní kódování styly, bude váš kód více křehká.  
  
 Pokud napíšete kód, který bude realizována kolekce tak, aby se tak předejde tyto problémy, mějte na paměti, ho komentáře podle potřeby ve vašem kódu tak, aby se tento problém pochopit programátory údržby.  
  
 Druhý Pokud výkon a další důležité informace povolit, použijte jenom deklarativní kód. Neupravujte vaše stávající strom XML. Vygenerujte nový token.  
  
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
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
