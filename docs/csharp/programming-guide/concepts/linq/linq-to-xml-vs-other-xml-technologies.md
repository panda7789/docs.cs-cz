---
title: Technologie LINQ to XML vs. Další Technologies3 XML
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 5c8b043055660ad272e46e72c877729086689158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>Technologie LINQ to XML vs. Další technologie XML
Toto téma porovnává [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] na následující technologie XML: <xref:System.Xml.XmlReader>, XSLT, MSXML a analyzátor XmlLite. Tyto informace mohou pomoci při rozhodování, kterou technologii použít.  
  
 Porovnání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k modelu DOM (Document Object), najdete v části [technologie LINQ to XML vs. MODEL DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>Technologie LINQ to XML vs. XmlReader  
 <xref:System.Xml.XmlReader> je analyzátor rychlé dopředné, bez ukládání do mezipaměti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je implementováno na <xref:System.Xml.XmlReader>, a jsou pevně integrovány. Ale můžete také použít <xref:System.Xml.XmlReader> samostatně.  
  
 Například předpokládejme, že jsou vytváření webové služby, který bude analýzy stovky dokumentů XML za sekundu a dokumenty mít stejnou strukturu, což znamená, že máte jenom zápisu jednu implementaci kód analyzovat kód XML. V takovém případě by pravděpodobně chcete použít <xref:System.Xml.XmlReader> samostatně.  
  
 Pokud vytváříte systému, která analyzuje mnoho menší dokumentů XML a každé z nich se liší, by chcete využít výhod vylepšení produktivitu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje.  
  
## <a name="linq-to-xml-vs-xslt"></a>Technologie LINQ to XML vs. XSLT  
 Obě [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a XSLT nabízí rozsáhlé možnosti transformace dokumentů XML. XSLT je založený na pravidlech, deklarativní přístup. Rozšířené XSLT programátory zápisu XSLT ve stylu funkční programovací které klade důraz bezstavové přístup. Transformace lze zapsat pomocí čistý funkcí, které jsou implementovány bez vedlejší účinky. Tento přístup založený na pravidlech nebo funkční neznámého mnoho vývojářům a může být obtížné a časově náročné na další.  
  
 XSLT může být velmi produktivní systém, který poskytuje vysoce výkonné aplikace. Například některé velký Web společnosti použít XSLT jako způsob, jak generují kód HTML z XML, která byla stažena z různých datových úložišť. Spravovaný modul XSLT zkompiluje XSLT CLR kódu a provádí i lépe v některých scénářích než nativní modul XSLT.  
  
 XSLT však není využít výhod C# a Visual Basic znalostních bází, které mají celá řada vývojářů. To vyžaduje vývojářům psát kód v jiné a komplexní programovací jazyk. V systémech softwarového, které jsou obtížnější vývoj a údržba pomocí dvou-integrated vývoj systémů, jako je například C# (nebo Visual Basic) a výsledky XSLT.  
  
 Až zvládnete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz na výrazy, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] transformace jsou výkonné technologie, která je snadno použitelný. V podstatě, můžete formuláři dokumentu XML pomocí funkční konstrukce, stahování dat z různých zdrojů, vytváření <xref:System.Xml.Linq.XElement> objektů dynamicky a ty celek do novou větev XML. Transformace můžete vygenerovat zcela nový dokument. Transformace ve vytváření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je poměrně jednoduché a intuitivní, a výsledný kód je čitelná. To snižuje náklady na vývoj a údržba.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] není určena k nahrazení XSLT. XSLT je stále z nástrojů pro složité a zaměřené na dokument XML transformace, zejména v případě, že není dobře definované strukturu dokumentu.  
  
 XSLT nabízí výhodu v podobě probíhá World Wide Web Consortium (W3C) standardní. Pokud máte požadavek používat jenom ty technologie, které jsou standardů, může být vhodnější XSLT.  
  
 XSLT je XML a proto se dá programově upravit.  
  
## <a name="linq-to-xml-vs-msxml"></a>Technologie LINQ to XML vs. MSXML  
 MSXML je založená na modelu COM technologie pro zpracování XML, který je součástí systému Microsoft Windows. MSXML poskytuje nativní implementaci DOM s podporou jazyka XPath a XSLT. Obsahuje taky SAX2 bez ukládání do mezipaměti, na základě událostí analyzátor.  
  
 MSXML dobře provádí, je ve výchozím nastavení ve většině scénářů zabezpečené a je přístupný v aplikaci Internet Explorer pro provádění zpracování v aplikace ve stylu jazyka AJAX XML na straně klienta. MSXML lze z žádný programovací jazyk, který podporuje modelu COM, včetně C++, JavaScript a Visual Basic 6.0.  
  
 MSXML se nedoporučuje pro použití ve spravovaném kódu podle common language runtime (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>Technologie LINQ to XML vs. Analyzátor XmlLite  
 Analyzátor XmlLite je bez ukládání do mezipaměti, předat dál pouze pro vyžádání obsahu analyzátor. Vývojáři především pomocí analyzátoru XmlLite s jazykem C++. Není doporučeno pro vývojáře k použití analyzátoru XmlLite se spravovaným kódem.  
  
 Hlavní výhodou analyzátor XmlLite je, že je jednoduché, rychlé analyzátor XML, který je ve většině scénářů zabezpečený. Jeho útoku na threat jsou velmi malé. Pokud máte analyzovat nedůvěryhodné dokumenty a chcete chránit před útoky, jako je například odmítnutí služby nebo prozrazení dat, může být analyzátor XmlLite vhodný.  
  
 Analyzátor XmlLite není integrovaná s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Není yield programátorů produktivitu vylepšení, které jsou motivačních force za [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Začínáme (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
