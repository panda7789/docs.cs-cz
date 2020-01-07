---
title: LINQ to XML vs. jiné XML Technologies3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 4cade6ecbee95ee288db34246986858609697731
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635675"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML vs. další technologie XML
Toto téma porovnává [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s následujícími technologiemi XML: <xref:System.Xml.XmlReader>, XSLT, MSXML a analyzátor XmlLite. Tyto informace vám pomohou rozhodnout, kterou technologii použít.  
  
 Porovnání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro model DOM (Document Object Model) (DOM) naleznete v tématu [LINQ to XML vs. DOMC#()](./linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML vs. XmlReader  
 <xref:System.Xml.XmlReader> je rychlý, výhradně s dopředný analyzátor bez ukládání do mezipaměti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je implementováno nad <xref:System.Xml.XmlReader>a je pevně integrovaná. Můžete ale také použít <xref:System.Xml.XmlReader> sám o sobě.  
  
 Předpokládejme například, že vytváříte webovou službu, která bude analyzovat stovky dokumentů XML za sekundu a dokumenty mají stejnou strukturu, což znamená, že stačí napsat jednu implementaci kódu k analýze XML. V takovém případě byste pravděpodobně chtěli použít <xref:System.Xml.XmlReader> sám o sobě.  
  
 Naproti tomu, pokud vytváříte systém, který analyzuje mnoho menších dokumentů XML a každá z nich je odlišná, budete chtít využívat vylepšení produktivity, která [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML vs. XSLT  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i XSLT poskytují rozsáhlé funkce transformace dokumentu XML. XSLT je deklarativní přístup založený na pravidle. Rozšířené programátory XSLT zapisují XSLT do funkčního stylu programování, který zvýrazňuje bezstavový přístup. Transformace lze zapsat pomocí čistě funkcí, které jsou implementovány bez vedlejších účinků. Tento přístup založený na pravidlech nebo funkci není známý pro mnoho vývojářů a může být obtížné a časově náročný.  
  
 XSLT může být velmi produktivní systém, který poskytuje vysoce výkonné aplikace. Například některé velké webové společnosti používají transformaci XSLT jako způsob generování kódu HTML z formátu XML, který byl získán z nejrůznějších úložišť dat. Spravovaný modul XSLT zkompiluje XSLT do kódu CLR a v některých scénářích provede ještě lepší, než nativní modul XSLT.  
  
 XSLT C# ale nevyužívá Visual Basic znalosti, které má mnoho vývojářů. Vyžaduje, aby vývojáři psát kód v jiném a složitém programovacím jazyce. Použití dvou neintegrovaných vývojových systémů, C# jako jsou například (nebo Visual Basic) a výsledky XSLT v softwarových systémech, které jsou obtížnější při vývoji a údržbě.  
  
 Po vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazů dotazů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] transformace představují výkonnou technologii, která se snadno používá. V podstatě vytváříte dokument XML pomocí funkční konstrukce, vybíráte data z různých zdrojů, vytváříte <xref:System.Xml.Linq.XElement> objektů dynamicky a sestavíte celých objektů do nového stromu XML. Transformace může vygenerovat zcela nový dokument. Vytváření transformací v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je poměrně jednoduché a intuitivní a výsledný kód je čitelný. Tím se sníží náklady na vývoj a údržbu.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] není určena k nahrazení souboru XSLT. XSLT je stále nástrojem volby pro komplikované a transformaci XML orientované na dokumenty, zejména v případě, že struktura dokumentu není správně definovaná.  
  
 XSLT má výhodu jako standard konsorcium World Wide Web (W3C). Pokud máte požadavek, abyste používali pouze technologie, které jsou standardy, může být soubor XSLT vhodnější.  
  
 XSLT je XML, a proto lze programově manipulovat.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML vs. MSXML  
 MSXML je technologie založená na modelu COM pro zpracování XML, která je součástí systému Microsoft Windows. Služba MSXML poskytuje nativní implementaci modelu DOM s podporou XPath a XSLT. Obsahuje také SAX2, který neukládá do mezipaměti, analyzátor založený na událostech.  
  
 Služba MSXML správně funguje, ve většině případů je zabezpečená a v aplikaci Internet Explorer je možné k provádění zpracování XML na straně klienta v aplikacích ve stylu AJAX. Službu MSXML lze použít z libovolného programovacího jazyka, který podporuje model C++com, včetně jazyků JavaScript a Visual Basic 6,0.  
  
 MSXML se nedoporučuje pro použití ve spravovaném kódu založeném na modulu CLR (Common Language Runtime).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML vs. analyzátor XmlLite  
 Analyzátor XmlLite není ukládání do mezipaměti, pouze k přeposílání, analyzátoru Pull. Vývojáři primárně používají analyzátor XmlLite C++s nástrojem. Pro vývojáře se nedoporučuje používat analyzátor XmlLite se spravovaným kódem.  
  
 Hlavní výhodou analyzátoru XmlLite je, že se jedná o odlehčený a rychlý analyzátor XML, který je ve většině scénářů zabezpečený. Oblast jeho hrozby je velmi malá. Pokud je nutné analyzovat nedůvěryhodné dokumenty a chcete chránit před útoky, jako je třeba odepření služby nebo únik dat, může být analyzátor XmlLite vhodný pro možnost.  
  
 Analyzátor XmlLite není integrovaný do LINQ (Language-Integrated Query). Nepřinese vám vylepšení produktivity v programátorech, která jsou pro technologii LINQ vynucená.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme (LINQ to XML)](./linq-to-xml-overview.md)
