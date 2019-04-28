---
title: Technologie LINQ to XML vs. Další Technologies3 XML
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 8e2a6b11e450890373de449c0a55839460b97566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682401"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>Technologie LINQ to XML vs. jiné technologie XML
Toto téma srovnává [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] na následující technologie XML: <xref:System.Xml.XmlReader>, XSLT, MSXML a analyzátoru XmlLite. Tyto informace mohou pomoci při rozhodování, technologii, která má použít.  
  
 Porovnání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k Document Object Model (DOM), najdete v článku [LINQ to XML versus. DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>Technologie LINQ to XML vs. XmlReader  
 <xref:System.Xml.XmlReader> jedná o analyzátor rychlé, pouze vpřed, bez ukládání do mezipaměti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se implementuje nad <xref:System.Xml.XmlReader>, a jsou úzce integrovány. Ale můžete také použít <xref:System.Xml.XmlReader> samostatně.  
  
 Například předpokládejme, že vytváříte webovou službu, která bude parsovat stovky dokumentů XML za sekundu a dokumenty mají stejnou strukturu, což znamená, že stačí napsat jednu implementaci kódu analyzovat kód XML. V takovém případě by pravděpodobně chcete použít <xref:System.Xml.XmlReader> samostatně.  
  
 Naopak pokud vytváříte systému, který analyzuje mnoho menších dokumentů XML a každý z nich se liší, chcete využít výhod vylepšení produktivity, která [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje.  
  
## <a name="linq-to-xml-vs-xslt"></a>Technologie LINQ to XML vs. XSLT  
 Obě [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a XSLT poskytuje rozsáhlé možnosti pro transformaci dokumentů XML. XSLT je založený na pravidlech, deklarativní přístup. Pokročilé XSLT programátoři zápisu XSLT ve stylu funkční programování, které zvýrazní bezstavové přístup. Transformace lze zapsat pomocí čisté funkce, které jsou implementovány bez vedlejších účinků. Tento přístup založený na pravidlech nebo funkční neznáš celá řada vývojářů a může být obtížné a časově náročné Další.  
  
 XSLT může být velmi produktivní systému, který poskytuje vysoce výkonné aplikace. Například některé velké objemy webových společnosti použít XSLT jako způsob, jak ze souboru XML, která byla stažena z různých úložišť dat generují kód HTML. Spravovaný modul XSLT zkompiluje XSLT do kódu CLR a ještě lepší výkon v některých scénářích než nativní modul XSLT.  
  
 Ale XSLT není výhod, které mají mnoho vývojářů znalosti jazyka C# a Visual Basic. Vyžaduje vývojářům umožňuje psát kód v různých a složité programovací jazyk. Pomocí dvou neintegrovaném vývoj systémy, jako je C# (nebo Visual Basic) a výsledky XSLT v systémech softwarového, které jsou pro vývoj a údržbu obtížnější.  
  
 Až zvládnete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazech, dotazů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] transformace jsou výkonné technologie, která se snadno používá. V podstatě, při vytváření dokumentu XML pomocí funkční konstrukce, stahování dat z různých zdrojů, vytváření <xref:System.Xml.Linq.XElement> objekty dynamicky a propojením celé do nového stromu XML. Transformace můžete vygenerovat zcela nový dokument. Vytváření transformace v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je poměrně jednoduché a intuitivní, a výsledný kód je čitelný. To snižuje náklady na vývoj a údržbu.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] není určena k nahrazení XSLT. XSLT je stále nástroj volí složité a zaměřené na dokument XML transformací, zejména v případě, že struktura dokumentu není dobře definované.  
  
 XSLT je výhodou World Wide Web Consortium (W3C) standard. Pokud máte požadavek, že používáte jenom ty technologie, které jsou standardy, může být vhodnější XSLT.  
  
 Je XML XSLT a proto lze programově manipulovat.  
  
## <a name="linq-to-xml-vs-msxml"></a>Technologie LINQ to XML vs. MSXML  
 MSXML je technologie založené na modelu COM. ke zpracování jazyka XML, který je součástí systému Microsoft Windows. MSXML poskytuje nativní implementaci modelu DOM s podporou jazyka XPath a XSLT. Obsahuje také analyzátor SAX2 bez ukládání do mezipaměti, založený na událostech.  
  
 MSXML také provádí, je ve výchozím nastavení ve většině případů zabezpečený a je přístupný pro provádění zpracování v aplikacích stylu AJAX na straně klienta XML v aplikaci Internet Explorer. MSXML je možné z libovolného programovacího jazyka, který podporuje modelu COM, včetně jazyka C++, JavaScript a Visual Basic 6.0.  
  
 MSXML se nedoporučuje používat ve spravovaném kódu založené na common language runtime (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>Technologie LINQ to XML vs. XmlLite  
 Analyzátor XmlLite je bez ukládání do mezipaměti, předat dál pouze o přijetí změn analyzátor. Vývojáři pomocí analyzátoru XmlLite především v jazyce C++. Není doporučeno vývojáři mohou použít analyzátor XmlLite se spravovaným kódem.  
  
 Hlavní výhodou analyzátor XmlLite je, že je jednoduché a rychlé analyzátor XML, který je ve většině případů zabezpečený. Jeho plochu hrozeb je velmi malý. Pokud potřebujete analyzovat nedůvěryhodné dokumenty a chcete pro ochranu před útoky, jako je útok DOS nebo prozrazení dat, analyzátor XmlLite může být dobrou volbou.  
  
 Analyzátor XmlLite není integrován s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Nevydává programátor vylepšení produktivity, které mají být motivačním nuceně za [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Viz také:

- [Začínáme (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
