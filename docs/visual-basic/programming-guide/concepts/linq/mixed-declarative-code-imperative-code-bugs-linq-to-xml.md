---
title: Smíšeného deklarativního a imperativního kódu chyby (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e7b3b624bb91525d2cda9477c29291e25eba1b07
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842275"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Smíšený kód deklarativní nebo imperativní kód chyby (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje různé metody, které umožňují upravit stromu XML přímo. Můžete přidat prvky, odstranění prvků, změňte obsah elementu, přidejte atributy a tak dále. Toto programovací rozhraní je popsán v [změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Pokud jste se provede iterace přes jeden z OS, jako <xref:System.Xml.Linq.XContainer.Elements%2A>a jak iterovat na ose upravujete stromu XML, můžete skončit s některé chyby neobvyklé.  
  
 Tento problém se někdy označuje jako "The Halloweenem problém".  
  
## <a name="definition-of-the-problem"></a>Definice problému  
 Při psaní kódu s využitím LINQ, který Iteruje přes kolekci jsou deklarativní stylem psaní kódu. Se více podobají popisující *co* chcete, místo toho, který *jak* chcete pracovat efektivněji. Pokud píšete kód, který 1) získá první prvek, 2) testy se některé podmínky, 3) upraví jeho a 4) vloží jej zpět do seznamu, pak by to imperativního kódu. Oznamujete tím počítače *jak* udělat, co chcete Hotovo.  
  
 Kombinování tyto styly kódu v rámci jedné operace je co vede k problémům. Zvažte použití těchto zdrojů:  
  
 Předpokládejme, že v něm máte odkazovaného seznamu se tři položky (a, b a c):  
  
 `a -> b -> c`  
  
 Nyní předpokládejme, že chcete přesunout prostřednictvím propojeného seznamu přidáte tři nové položky (", b" a jazyka c "). Chcete, aby výsledný odkazovaného seznamu vypadat nějak takto:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Proto můžete napsat kód, který Iteruje přes seznam a pro každou položku, přidá nové právo položku za ním. Co se stane, je, že váš kód se nejprve zobrazí `a` elementu a vložit `a'` po něm. Nyní, váš kód se přesune na další uzel v seznamu, který je teď `a'`! Využívá elastic přidá novou položku do seznamu, `a''`.  
  
 Jak by vás tento problém vyřešit v reálném světě? Dobře můžete vytvořit kopii původní propojeného seznamu a vytvořit zcela nový seznam. Nebo pokud vytváříte čistě imperativního kódu, můžete se setkat na první položku Přidat novou položku a pak přejděte dvakrát v propojeném seznamu posunutí je nad prvkem, který jste právě přidali.  
  
## <a name="adding-while-iterating"></a>Přidání během iterace  
 Předpokládejme například, že chcete napsat kód pro každý element ve stromové struktuře chcete vytvořit duplicitní element:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 Tento kód přejde do nekonečné smyčky. `foreach` Příkaz prochází `Elements()` osy, přidávání nových elementů do `doc` elementu. To končí také iterace prvků, které právě přidali. A vzhledem k tomu, že ji přidělí nové objekty při každé iteraci smyčky, budou nakonec spotřebovávat veškerou dostupnou paměť.  
  
 Tento problém můžete vyřešit přidáním kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> standardní operátor dotazu, následujícím způsobem:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
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
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
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
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 To vytvoří následující výstup:  
  
```xml  
<Root />  
```  
  
 Alternativně můžete eliminovat iterace úplně voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>Proč nelze LINQ umožňují automaticky zpracovat to?  
 Jedním z přístupů je vždy přenést vše do paměti namísto provádění opožděné vyhodnocení. Nicméně by bylo velmi náročné z hlediska výkonu a paměti. Ve skutečnosti LINQ a (LINQ to XML) byly pro tento postup, je selže v reálných situacích.  
  
 Další z možných způsobů je vložit nějaký druh transakce syntaxe na LINQ a mít kompilátoru pokus o analýzu kódu a určit, pokud materializace potřeba žádné konkrétní kolekce. Pokus o určení veškerý kód, který má vedlejší účinky je ale mimořádně složité. Vezměte v úvahu následující kód:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Tyto analýzy kódu by bylo potřeba analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volat k určení, pokud žádný kód má vedlejší účinky. Ale analýzy kódu nelze právě hledat jakýkoli kód, který má vedlejší účinky. Je potřeba zvolit pro přesně takový kód, který má vedlejší účinky na podřízených elementů `root` v této situaci.  
  
 Technologie LINQ to XML nebude pokoušet provést tyto analýzy.  
  
 Je vás, abyste se těmto problémům vyhnuli.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Nekombinujte nejprve deklarativního a imperativního kódu.  
  
 I v případě, že víte přesně sémantiku kolekce a sémantika metody, které určuje stromu XML, pokud napsání chytřejší kódu, které se vyhýbají tyto druhy problémů, váš kód bude nutné udržovat jinými vývojáři v budoucnu , a nemusí být jako prostý na problémy. Pokud kombinujete deklarativního a imperativního programování styly, bude váš kód více křehký.  
  
 Pokud píšete kód, který bude realizována kolekce tak, aby se vyhnout těmto problémům, poznamenejte si ji s komentáři, případně ve vašem kódu tak, aby programátoři údržba bude porozumět danému problému.  
  
 Za druhé Pokud výkon a další důležité informace povolit, použijte pouze deklarativního kódu. Neupravujte vaše stávající stromu XML. Vygenerujte nový token.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a>Viz také:

- [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
