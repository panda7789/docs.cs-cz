---
title: funkční konstrukce (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f42cd6f31134c5f4c7d6a75f38997b2be0c317f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398061"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Funkční konstrukce (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*. Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.  
  
 Existuje několik klíčových funkcí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovacího rozhraní, které umožňují konstrukci funkčnosti:  
  
- <xref:System.Xml.Linq.XElement>Konstruktor přijímá různé typy argumentů pro obsah. Například můžete předat další <xref:System.Xml.Linq.XElement> objekt, který se stal podřízeným prvkem. Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který se stal atributem elementu. Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.  
  
- <xref:System.Xml.Linq.XElement>Konstruktor přebírá `params` pole typu <xref:System.Object> , aby bylo možné předat do konstruktoru libovolný počet objektů. To umožňuje vytvořit prvek, který má složitý obsah.  
  
- Pokud objekt implementuje, je vyhodnocena <xref:System.Collections.Generic.IEnumerable%601> kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> objekty nebo <xref:System.Xml.Linq.XAttribute> , každá položka v kolekci se přidá samostatně. To je důležité, protože umožňuje předat výsledky dotazu LINQ do konstruktoru.  
  
 Například:  
  
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
  
## <a name="see-also"></a>Viz také

- [Vytváření stromů XML (Visual Basic)](creating-xml-trees.md)
