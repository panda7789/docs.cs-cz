---
title: Technologie LINQ to XML přehled (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 3818177c2ed14b1159b8e63e324894d7e89b72b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-overview-visual-basic"></a>Technologie LINQ to XML přehled (Visual Basic)
XML byl široce přijat jako způsob formátování dat v mnoha kontexty. Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databází.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přepracovanou přístup k programování se souborem XML. Poskytuje možnosti úprav z objektu modelu dokumentu (DOM) v dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy. I když jsou tyto výrazy dotazů syntakticky liší od jazyka XPath, poskytují podobné funkce.  
  
## <a name="linq-to-xml-developers"></a>Technologie LINQ to XML vývojáři  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílem celou řadu vývojáři. Pro průměrné vývojáře, kteří právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML tím, že poskytuje podobné do SQL možnosti dotazu. S jenom kousek studii můžete postup programátory v jazyce psát dotazy stručného a výkonné v jejich programovací jazyk podle volby.  
  
 Můžete použít profesionální vývojáře [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mohou zapisovat menší kód, který je více výrazovou, kompaktnější a účinnější. Výrazy dotazů použitím z několika domén dat ve stejnou dobu.  
  
## <a name="what-is-linq-to-xml"></a>Co je technologie LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je povolené LINQ, v paměti XML programovací rozhraní, které umožňuje pracovat s XML uvnitř [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programovacích jazyků.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jako objektu modelu dokumentu (DOM) je v tom, že přináší dokumentu XML do paměti. Můžete vyhledat a upravit dokumentu, a po úpravě ho můžete uložit do souboru nebo jej serializovat a poslat přes Internet. Ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od DOM: poskytuje nový model objektu, který je světlejší váhy a snadnější pracovat, a který využívá funkce jazyka v jazyce Visual Basic.  
  
 Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Tato integrace umožňuje psát dotazy na dokument XML v paměti pro načtení kolekce elementů a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná ve funkcích (i když není v syntaxi) XPath a XQuery. Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce Visual Basic poskytuje silnější zadáte, kompilace kontrolu a vylepšenou podporu ladicí program.  
  
 Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňuje efektivní přístup pro vytváření stromů XML. Tuto metodu volá *funkční konstrukce*, umožňuje vývojářům snadno transformace stromy XML z jednoho obrazce do jiného.  
  
 Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číslo atribut pro každý element položky v nákupní objednávka:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Například můžete seznam seřadit podle počtu část položky s hodnotou větší než 100 USD. Chcete-li získat tyto informace, můžete spustit následující dotaz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:  
  
-   Načtení XML ze souborů nebo datových proudů.  
  
-   Serializace XML na soubory nebo datové proudy.  
  
-   Vytvoření XML od začátku pomocí funkční konstrukce.  
  
-   Dotaz pomocí jazyka XPath jako osy XML.  
  
-   Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Ověření XML stromy pomocí XSD.  
  
-   Použijte kombinaci těchto funkcí k transformaci stromy XML z jednoho obrazce do jiné.  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 IOne nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML. Například pokud chcete vytvořit malé stromu XML, můžete napsat kód následujícím způsobem:  
  
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
  
 Visual Basic – kompilátor překládá literálů XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.  
  
 Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq>  
 [Začínáme (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
