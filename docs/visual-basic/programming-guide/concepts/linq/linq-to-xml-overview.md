---
title: Přehled LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368735"
---
# <a name="linq-to-xml-overview-visual-basic"></a>Přehled LINQ to XML (Visual Basic)
Soubor XML byl široce přijat jako způsob, jak formátovat data v mnoha kontextech. Můžete například najít XML na webu, v konfiguračních souborech, v systém Microsoft Office soubory aplikace Word a v databázích.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je aktuální, přenavržený přístup k programování s XML. Poskytuje funkce pro úpravy dokumentu v paměti model DOM (Document Object Model) (DOM) a podporuje výrazy dotazů LINQ. I když tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML vývojáři  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]cílí na celou řadu vývojářů. Pro průměrného vývojáře, který chce jenom udělat něco udělat, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML práci s dotazy, která je podobná SQL. S pouhou bitovou studiem se programátoři můžou naučit psát stručné a výkonné dotazy v programovacím jazyce, který si vyberete.  
  
 Profesionální vývojáři mohou využít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k výraznému zvýšení produktivity. Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] mohou napsat méně kódu, který je více expresější, kompaktnější a výkonnější. Můžou používat výrazy dotazů z více domén dat současně.  
  
## <a name="what-is-linq-to-xml"></a>Co je LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je programovací rozhraní XML v paměti, které umožňuje pracovat s XML v rámci .NET Framework programovacích jazyků.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je podobně jako model DOM (Document Object Model) (DOM) v tom, že převede dokument XML do paměti. Můžete provést dotazování a úpravy dokumentu a až ho upravíte, můžete ho uložit do souboru nebo ho serializovat a poslat přes Internet. Ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] liší se od modelu DOM: poskytuje nový objektový model, který je nevýznamný a usnadňuje práci s a který využívá funkce jazyka v Visual Basic.  
  
 Nejdůležitější výhodou je, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je její integrace s LINQ (Language-Integrated Query). Tato integrace umožňuje zapisovat dotazy v dokumentu XML v paměti pro načtení kolekcí prvků a atributů. Funkce dotazu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná s funkcemi (i když není v syntaxi) do XPath a XQuery. Integrace LINQ v Visual Basic poskytuje silnější psaní, kontrolu doby kompilace a vylepšenou podporu ladicího programu.  
  
 Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použít výsledky dotazu jako parametry <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektů umožňují účinný přístup k vytváření stromů XML. Tento přístup s názvem *funkční konstrukce*umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce na druhý.  
  
 Například můžete mít typické nákupní objednávky XML, jak je popsáno v [ukázkovém souboru XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md). Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete spustit následující dotaz pro získání hodnoty atributu číslo součásti pro každý prvek položky v nákupní objednávce:  
  
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
  
 Kromě těchto možností LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete:  
  
- Načte XML ze souborů nebo datových proudů.  
  
- Serializace XML do souborů nebo datových proudů.  
  
- Vytvořte XML od začátku pomocí funkční konstrukce.  
  
- Dotazování XML pomocí osy jako XPath  
  
- Manipulace se stromovou strukturou XML v paměti pomocí metod, jako <xref:System.Xml.Linq.XContainer.Add%2A> jsou,, <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> a <xref:System.Xml.Linq.XElement.SetValue%2A> .  
  
- Ověří stromy XML pomocí XSD.  
  
- Použijte kombinaci těchto funkcí pro transformaci stromů XML z jednoho obrazce do jiného.  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 IOne s nejvýznamnějšími výhodami programování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML. Například pro vytvoření malého stromu XML můžete napsat kód následujícím způsobem:  
  
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
  
 Kompilátor Visual Basic překládá literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.  
  
 Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](creating-xml-trees.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq>
- [Začínáme (LINQ to XML)](getting-started-linq-to-xml.md)
- [Přehled technologie LINQ to XML v jazyce Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../language-features/xml/index.md)
