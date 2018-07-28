---
title: Funkční konstrukce (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 360c321f993c8adb17767987060a0edcccad082a
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2018
ms.locfileid: "39333010"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Funkční konstrukce (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje efektivní způsob, jak vytvořit XML elementů s názvem *funkční konstrukce*. Funkční konstrukce je schopnost vytvářet stromu XML v jediném příkazu.  
  
 Existuje několik klíčových funkcích služby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní, která umožňují funkční konstrukce:  
  
-   <xref:System.Xml.Linq.XElement> Konstruktoru přijímá různé typy argumentů pro obsah. Například lze předat jiné <xref:System.Xml.Linq.XElement> objekt, který bude podřízený element. Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který bude atribut prvku. Nebo můžete předat jakéhokoli jiného typu objektu, který je převeden na řetězec a stane se textového obsahu elementu.  
  
-   <xref:System.Xml.Linq.XElement> Přebírá konstruktor `params` pole typu <xref:System.Object>tak, aby libovolný počet objektů, které můžete předat konstruktoru. To umožňuje vytvořit element, který se složitým obsahem.  
  
-   Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně. To je důležité, protože to umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu do konstruktoru.  
  
 Následuje příklad:  
  
 Tyto funkce umožňují také napsat kód pomocí literálů XML k vytvoření stromu XML a také napsat kód, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazuje při vytváření stromu XML:  
  
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
 [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
