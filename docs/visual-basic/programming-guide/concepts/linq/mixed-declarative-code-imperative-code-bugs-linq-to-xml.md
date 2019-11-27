---
title: Chyby smíšeného deklarativního a imperativního kódu (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: 369fae59516df785ac686645d47e74e69a8f1457
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331650"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>Smíšený deklarativní kód/chyby nepodmíněných kódů (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje různé metody, které umožňují přímou úpravu stromu XML. Můžete přidat prvky, odstranit prvky, změnit obsah elementu, přidat atributy a tak dále. Toto programovací rozhraní je popsáno v tématu [Úprava stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Pokud provádíte iteraci na jednu z OS, jako je například <xref:System.Xml.Linq.XContainer.Elements%2A>, a upravujete strom XML při iteraci přes osu, můžete ukončit některé neobvyklé chyby.  
  
 Tento problém se někdy označuje jako "problém Halloweenem".  
  
## <a name="definition-of-the-problem"></a>Definice problému  
 Při psaní kódu pomocí LINQ, který projde kolekcí, píšete kód v deklarativním stylu. K popisu *toho, co* chcete udělat, je další podobají, a to tak, *jak* chcete. Pokud napíšete kód, který 1) získá první prvek, 2) ho testuje v nějaké podmínce, 3) ho upraví a 4) ho vrátí zpátky do seznamu, pak by to byl imperativní kód. Informujete o tom, *jak* se má počítač provést.  
  
 Kombinování těchto stylů kódu ve stejné operaci je to, co vede k problémům. Zvažte použití těchto zdrojů:  
  
 Předpokládejme, že máte propojený seznam se třemi položkami (a, b a c):  
  
 `a -> b -> c`  
  
 Nyní předpokládejme, že chcete přejít přes propojený seznam a přidat tři nové položky (a, b a c). Chcete, aby výsledný propojený seznam vypadal takto:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Takže napíšete kód, který projde seznamem, a pro každou položku přidá novou položku hned po ní. Co se stane, váš kód nejprve uvidí prvek `a` a vloží `a'` po něm. Nyní se váš kód přesune na další uzel v seznamu, který je nyní `a'`! Happily přidá novou položku do seznamu, `a''`.  
  
 Jak to byste měli v reálném světě vyřešit? Také můžete vytvořit kopii původního propojeného seznamu a vytvořit úplně nový seznam. Nebo pokud píšete čistě imperativní kód, můžete najít první položku, přidat novou položku a pak dvakrát v propojeném seznamu a přejít tak na prvek, který jste právě přidali.  
  
## <a name="adding-while-iterating"></a>Přidávání během iterací  
 Předpokládejme například, že chcete napsat kód, který je pro každý prvek ve stromové struktuře, chcete vytvořit duplicitní prvek:  
  
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
  
 Tento kód přejde do nekonečné smyčky. Příkaz `foreach` prochází osu `Elements()` a přidává nové prvky do `doc` elementu. Ukončí iteraci také prostřednictvím prvků, které jste právě přidali. A protože přiděluje nové objekty s každou iterací smyčky, bude nakonec využívat veškerou dostupnou paměť.  
  
 Tento problém můžete vyřešit tak, že narazíte kolekci do paměti pomocí operátoru dotazu <xref:System.Linq.Enumerable.ToList%2A> Standard následujícím způsobem:  
  
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
  
## <a name="deleting-while-iterating"></a>Odstraňování během iterace  
 Pokud chcete odstranit všechny uzly na určité úrovni, můžete se rozhodnout, že napíšete kód podobný následujícímu:  
  
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
  
 To ale neudělá to, co chcete. V takové situaci, po odebrání prvního prvku, je odebrán ze stromu XML obsaženého v kořenovém adresáři a kódem v metodě element, který provádí iteraci, nelze najít další prvek.  
  
 Předchozí kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 Řešením je znovu volat <xref:System.Linq.Enumerable.ToList%2A>, aby se kolekce vyhodnotit, jak je znázorněno níže:  
  
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
  
 Výsledkem je následující výstup:  
  
```xml  
<Root />  
```  
  
 Případně můžete iteraci zcela eliminovat voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> v nadřazeném elementu:  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a>Proč nedokážete tuto technologii LINQ automaticky zpracovat?  
 Jedním z přístupů je vždycky přenášet vše do paměti namísto opožděného vyhodnocení. Je ale velmi nákladný z pohledu výkonu a využití paměti. Pokud by se jednalo o tento přístup v praxi LINQ and (LINQ to XML), nedošlo by k chybě v reálných situacích.  
  
 Dalším možným přístupem by bylo, že se do LINQ vloží syntaxe transakce a pokusí se kompilátor analyzovat kód a určí, jestli je potřeba vyhodnocená konkrétní kolekce. Nicméně pokus o určení veškerého kódu, který má vedlejší účinky, je neuvěřitelně složitý. Vezměte v úvahu následující kód:  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 Takový kód analýzy by musel analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volaly, k určení, zda nějaký kód měl vedlejší účinky. Ale kód analýzy nemůže vyhledat žádný kód, který má vedlejší účinky. Bylo by nutné vybrat pouze kód, který měl vedlejší účinky na podřízené prvky `root` v této situaci.  
  
 LINQ to XML se neprovede žádná taková analýza.  
  
 Abyste se těmto problémům vyhnuli, je to na vás.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Nejdříve Nekombinujte deklarativní a imperativní kód.  
  
 I v případě, že znáte přesně sémantiku vašich kolekcí a sémantiku metod, které mění strom XML, pokud napíšete kód chytřejší, který brání těmto kategoriím problémů, váš kód bude muset být v budoucnu udržován jinými vývojáři. a nemusí být na problémech jasné. Pokud kombinujete deklarativní a imperativní styly kódování, váš kód bude více poměrně křehký.  
  
 Pokud píšete kód, který materializuje kolekci tak, aby se tyto problémy předešly, poznamenejte si je podle potřeby v kódu, aby Programátori údržby porozuměli problému.  
  
 Za druhé, pokud povolíte výkon a další okolnosti, používejte pouze deklarativní kód. Neměňte existující strom XML. Vygenerujte nový.  
  
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

- [Rozšířené programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
