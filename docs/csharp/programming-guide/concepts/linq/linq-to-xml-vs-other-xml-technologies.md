---
title: LINQ na XML vs. jiné technologie XML3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 4cade6ecbee95ee288db34246986858609697731
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635675"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ na XML vs. jiné technologie XML
Toto téma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je v porovnání <xref:System.Xml.XmlReader>s následujícími technologiemi XML: , XSLT, MSXML a XmlLite. Tyto informace vám mohou pomoci rozhodnout, kterou technologii použít.  
  
 Porovnání s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektovým modelem dokumentu (DOM) naleznete v tématu [LINQ to XML vs. DOM (C#)](./linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ na XML vs. XmlReader  
 <xref:System.Xml.XmlReader>je rychlý analyzátor pouze pro dopředu, bez ukládání do mezipaměti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je implementována <xref:System.Xml.XmlReader>nad , a jsou úzce integrovány. Můžete však také <xref:System.Xml.XmlReader> použít sám o sobě.  
  
 Předpokládejme například, že vytváříte webovou službu, která bude analyzovat stovky dokumentů XML za sekundu a dokumenty mají stejnou strukturu, což znamená, že k analýzě xml je třeba napsat pouze jednu implementaci kódu. V tomto případě byste pravděpodobně <xref:System.Xml.XmlReader> chtěli použít samostatně.  
  
 Naproti tomu pokud vytváříte systém, který analyzuje mnoho menších dokumentů XML a každý z nich je jiný, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] měli byste využít vylepšení produktivity, která poskytuje.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ na XML vs. XSLT  
 Oba [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a XSLT poskytují rozsáhlé možnosti transformace dokumentu XML. XSLT je deklarativní přístup založený na pravidlech. Pokročilí programátoři XSLT píší XSLT ve funkčním programovacím stylu, který zdůrazňuje přístup bez stavů. Transformace lze zapsat pomocí čisté funkce, které jsou implementovány bez vedlejších účinků. Tento přístup založený na pravidlech nebo funkční přístup je neznámý pro mnoho vývojářů a může být obtížné a časově náročné se učit.  
  
 XSLT může být velmi produktivní systém, který poskytuje vysoce výkonné aplikace. Některé velké webové společnosti například používají XSLT jako způsob generování kódu HTML z jazyka XML, který byl odebrán z různých úložišť dat. Spravovaný modul XSLT zkompiluje kód XSLT do CLR a v některých scénářích funguje ještě lépe než nativní modul XSLT.  
  
 XSLT však nevyužívá znalosti jazyka C# a Visual Basic, které mají mnoho vývojářů. Vyžaduje, aby vývojáři psát kód v jiném a složitéprogramovací jazyk. Použití dvou neintegrovaných vývojových systémů, jako je C# (nebo Visual Basic) a XSLT, má za následek vývoj a údržbu softwarových systémů, které jsou obtížněji vyvíjené a udržovatelné.  
  
 Po zvládnutí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazů dotazu jsou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] transformace výkonnou technologií, která se snadno používá. V podstatě vytvoříte dokument XML pomocí funkční konstrukce, vytahujete data z různých zdrojů, dynamicky vytváříte <xref:System.Xml.Linq.XElement> objekty a sestavujete celek do nového stromu XML. Transformace může generovat zcela nový dokument. Vytváření transformací [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v je relativně snadné a intuitivní a výsledný kód je čitelný. To snižuje náklady na vývoj a údržbu.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]není určen k nahrazení XSLT. XSLT je stále nástrojem volby pro složité transformace XML zaměřené na dokumenty, zejména pokud struktura dokumentu není správně definována.  
  
 XSLT má tu výhodu, že je standardem World Wide Web Consortium (W3C). Pokud máte požadavek, že používáte pouze technologie, které jsou standardy, XSLT může být vhodnější.  
  
 XSLT je XML, a proto může být programově manipulováno.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ na XML vs. MSXML  
 MSXML je technologie založená na com pro zpracování xml, která je součástí systému Microsoft Windows. MSXML poskytuje nativní implementaci dom s podporou XPath a XSLT. Obsahuje také analyzátor SAX2 bez ukládání do mezipaměti, analyzátor založený na událostech.  
  
 Jazyk MSXML funguje dobře, je ve většině scénářů ve výchozím nastavení zabezpečený a lze k němu přistupovat v aplikaci Internet Explorer pro provádění zpracování XML na straně klienta v aplikacích ve stylu AJAX. Jazyk MSXML lze použít z libovolného programovacího jazyka, který podporuje com, včetně C++, JavaScript a Visual Basic 6.0.  
  
 MSXML se nedoporučuje používat ve spravovaném kódu na základě clr (COMMON Language runtime).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ na XML vs. XmlLite  
 XmlLite je non-caching, pouze dopředu, pull analyzátor. Vývojáři používají především XmlLite s C++. Nedoporučuje se, aby vývojáři používali XmlLite se spravovaným kódem.  
  
 Hlavní výhodou XmlLite je, že je lehký, rychlý analyzátor XML, který je ve většině scénářů bezpečný. Jeho oblast ohrožení je velmi malá. Pokud máte analyzovat nedůvěryhodné dokumenty a chcete chránit před útoky, jako je odmítnutí služby nebo vystavení dat, XmlLite může být dobrou volbou.  
  
 XmlLite není integrován s jazykem integrovaný dotaz (LINQ). Nepřináší programátor zvýšení produktivity, které jsou motivační síla za LINQ.  
  
## <a name="see-also"></a>Viz také

- [Začínáme (LINQ to XML)](./linq-to-xml-overview.md)
