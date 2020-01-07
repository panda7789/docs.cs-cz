---
title: Funkční konstrukce (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a51360d6c8d44770c462afb728a1fb78d3e2cd42
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636845"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Funkční konstrukce (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*. Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.  
  
 Existuje několik klíčových funkcí rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, které umožňují konstrukci funkčnosti:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> přebírá různé typy argumentů pro obsah. Například můžete předat další objekt <xref:System.Xml.Linq.XElement>, který se stal podřízeným prvkem. Můžete předat objekt <xref:System.Xml.Linq.XAttribute>, který se stal atributem elementu. Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete konstruktoru předat libovolný počet objektů. To umožňuje vytvořit prvek, který má složitý obsah.  
  
- Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vyhodnocena kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje objekty <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, každá položka v kolekci se přidá samostatně. To je důležité, protože umožňuje předat výsledky dotazu LINQ do konstruktoru.  
  
 Tady je příklad:  
  
 Tyto funkce umožňují psát kód pomocí literálů XML pro vytvoření stromu XML a také pro psaní kódu, který používá výsledky dotazů LINQ při vytváření stromu XML:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
