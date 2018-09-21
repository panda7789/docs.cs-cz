---
title: Přehled LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 962fddcfec04259425c1094f07adf0e3966dfab0
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46526715"
---
# <a name="linq-to-xml-overview-visual-basic"></a>Přehled LINQ to XML (Visual Basic)
XML je široce přijat jako způsob, jak formátování dat v mnoha kontextech. Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databázích.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přepracovaný přístup k programování v jazyce XML. Poskytuje možnosti úprav Document Object Model (DOM) dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. I když tyto výrazy dotazu představují syntakticky liší od jazyka XPath, poskytují podobné funkce.  
  
## <a name="linq-to-xml-developers"></a>Technologie LINQ to XML vývojáře  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílí na širokou škálu vývojáři. Průměrná vývojář, který právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML pomocí prostředí dotazu, který je podobný SQL. S jen trochu studii můžete další programátorům v jejich programovací jazyk podle vlastní volby psát stručné a výkonné dotazy.  
  
 Profesionální vývojáři mohou použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit svou produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zapisují menší kód, který je více výrazovými možnostmi, kompaktnějším a výkonnější. Použitím – výrazy dotazů z několika domén dat ve stejnou dobu.  
  
## <a name="what-is-linq-to-xml"></a>Co je LINQ to XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je povolené LINQ, v paměti XML programovací rozhraní, která umožňuje pracovat s jazykem XML z v rámci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programovacích jazyků.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je třeba Document Object Model (DOM) přináší dokumentu XML do paměti. Můžete zadávat dotazy a úpravě dokumentu a po úpravě ho můžete uložit do souboru nebo ho serializovat a odešle je prostřednictvím Internetu. Nicméně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od modelu DOM: poskytuje nové objektový model, který je světlejší váha a snadněji pracovat, a, který využívá funkce jazyka v jazyce Visual Basic.  
  
 Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Tato integrace umožňuje psát dotazy v dokumentu XML v paměti k načtení kolekce elementů a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelné funkci (i když nejsou v syntaxi) na XPath a XQuery. Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce Visual Basic nabízí silnější typy, kompilace kontrolu a vylepšená podpora ladicího programu.  
  
 Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektu umožňuje efektivní přístup k vytváření stromů XML. Tomuto přístupu se říká *funkční konstrukce*, umožňuje vývojářům snadno transformace stromů XML z jednoho obrazce na jiný.  
  
 Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md). S použitím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číselné atribut pro každý prvek položky v nákupní objednávky:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Další příklad můžete seznam seřazený podle čísel položky s hodnotou větší než 100 USD. Pro získání těchto informací, můžete spustit následující dotaz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:  
  
-   Načtení XML ze souborů nebo datových proudů.  
  
-   Serializace XML pro soubory nebo datové proudy.  
  
-   Vytvoření XML od začátku pomocí funkční konstrukce.  
  
-   Dotaz XML pomocí XPath jako osy.  
  
-   Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Ověření pomocí XSD stromů XML.  
  
-   Pomocí kombinace těchto funkcí transformace stromů XML z jednoho obrazce do jiné.  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 IOne nejvýznamnější výhody programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytváření stromů XML. Například k vytvoření malé stromu XML, můžete napsat kód následujícím způsobem:  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 Kompilátor jazyka Visual Basic přeloží literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.  
  
 Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq>  
- [Začínáme (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
- [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
