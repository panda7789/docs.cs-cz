---
title: Přehled LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: ef3fca844dc98440eb4816110a5a78482cfa4f4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346797"
---
# <a name="linq-to-xml-overview-visual-basic"></a>Přehled LINQ to XML (Visual Basic)
Soubor XML byl široce přijat jako způsob, jak formátovat data v mnoha kontextech. Můžete například najít XML na webu, v konfiguračních souborech, v systém Microsoft Office soubory aplikace Word a v databázích.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přenavržený přístup k programování s XML. Poskytuje funkce pro úpravy dokumentů v paměti model DOM (Document Object Model) (DOM) a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazy dotazů. I když tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML vývojáři  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílí na celou řadu vývojářů. Pro průměrného vývojáře, který chce jenom udělat, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje práci s XML pomocí dotazů, které jsou podobné SQL. S pouhou bitovou studiem se programátoři můžou naučit psát stručné a výkonné dotazy v programovacím jazyce, který si vyberete.  
  
 Profesionální vývojáři můžou pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] významně zvýšit produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžou napsat méně kódu, který je více expresější, kompaktnější a výkonnější. Můžou používat výrazy dotazů z více domén dat současně.  
  
## <a name="what-is-linq-to-xml"></a>Co je LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je programovací rozhraní XML v paměti, které umožňuje pracovat s XML v rámci .NET Framework programovacích jazyků.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je stejně jako model DOM (Document Object Model) (DOM) v tom, že převede dokument XML do paměti. Můžete provést dotazování a úpravy dokumentu a až ho upravíte, můžete ho uložit do souboru nebo ho serializovat a poslat přes Internet. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se ale liší od modelu DOM: poskytuje nový objektový model, který je nevýznamný a usnadňuje práci s a který využívá funkce jazyka v Visual Basic.  
  
 Nejdůležitější výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je jeho integrace s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Tato integrace umožňuje zapisovat dotazy v dokumentu XML v paměti pro načtení kolekcí prvků a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná s funkcemi (i když není v syntaxi) do XPath a XQuery. Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v Visual Basic poskytuje silnější funkce pro psaní, kontrolu doby kompilace a vylepšenou podporu ladicího programu.  
  
 Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použití výsledků dotazu jako parametrů pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektů umožňuje účinný přístup k vytváření stromů XML. Tento přístup s názvem *funkční konstrukce*umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce na druhý.  
  
 Například můžete mít typické nákupní objednávky XML, jak je popsáno v [ukázkovém souboru XML: typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md). Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete spustit následující dotaz pro získání hodnoty atributu číslo součásti pro každý prvek položky v nákupní objednávce:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Jako další příklad můžete chtít seznam, který je seřazen podle čísla součásti, u položek s hodnotou větší než $100. Chcete-li získat tyto informace, můžete spustit následující dotaz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Kromě těchto možností [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete:  
  
- Načte XML ze souborů nebo datových proudů.  
  
- Serializace XML do souborů nebo datových proudů.  
  
- Vytvořte XML od začátku pomocí funkční konstrukce.  
  
- Dotazování XML pomocí osy jako XPath  
  
- Manipulace se stromovou strukturou XML v paměti pomocí metod, jako je <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>a <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
- Ověří stromy XML pomocí XSD.  
  
- Použijte kombinaci těchto funkcí pro transformaci stromů XML z jednoho obrazce do jiného.  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 IOne z nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je snadné vytváření stromů XML. Například pro vytvoření malého stromu XML můžete napsat kód následujícím způsobem:  
  
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
  
 Kompilátor Visual Basic překládá literály XML do volání metody [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq>
- [Začínáme (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [Přehled LINQ to XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
