---
title: LINQ to XML vs. jiné XML Technologies2
ms.date: 07/20/2015
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
ms.openlocfilehash: ee855c40e61a6b63c2891d8f30072fc8e235fe4b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389316"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>Technologie LINQ to XML vs. jiné technologie XML
Toto téma porovnává [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] následující technologie XML: <xref:System.Xml.XmlReader> , XSLT, MSXML a analyzátor XmlLite. Tyto informace vám pomohou rozhodnout, kterou technologii použít.  
  
 Porovnání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s model DOM (Document Object Model) (DOM) naleznete v tématu [LINQ to XML vs. DOM (Visual Basic)](linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML vs. XmlReader  
 <xref:System.Xml.XmlReader>je rychlý, výhradně s dopředný analyzátor bez ukládání do mezipaměti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je implementováno nad <xref:System.Xml.XmlReader> a je pevně integrovaná. Můžete ho ale použít i <xref:System.Xml.XmlReader> samostatně.  
  
 Předpokládejme například, že vytváříte webovou službu, která bude analyzovat stovky dokumentů XML za sekundu a dokumenty mají stejnou strukturu, což znamená, že stačí napsat jednu implementaci kódu k analýze XML. V takovém případě byste pravděpodobně chtěli použít <xref:System.Xml.XmlReader> sám sebe.  
  
 Naproti tomu, pokud vytváříte systém, který analyzuje mnoho menších dokumentů XML a každá z nich je odlišná, budete chtít využívat vylepšení produktivity, která [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML vs. XSLT  
 Jak i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XSLT poskytují rozsáhlé funkce transformace dokumentů XML. XSLT je deklarativní přístup založený na pravidle. Rozšířené programátory XSLT zapisují XSLT do funkčního stylu programování, který zvýrazňuje bezstavový přístup. Transformace lze zapsat pomocí čistě funkcí, které jsou implementovány bez vedlejších účinků. Tento přístup založený na pravidlech nebo funkci není známý pro mnoho vývojářů a může být obtížné a časově náročný.  
  
 XSLT může být velmi produktivní systém, který poskytuje vysoce výkonné aplikace. Například některé velké webové společnosti používají transformaci XSLT jako způsob generování kódu HTML z formátu XML, který byl získán z nejrůznějších úložišť dat. Spravovaný modul XSLT zkompiluje XSLT do kódu CLR a v některých scénářích provede ještě lepší, než nativní modul XSLT.  
  
 XSLT ale nevyužívá C# a Visual Basic znalosti, které má mnoho vývojářů. Vyžaduje, aby vývojáři psát kód v jiném a složitém programovacím jazyce. Použití dvou neintegrovaných vývojových systémů, jako jsou C# (nebo Visual Basic) a výsledky XSLT v softwarových systémech, které jsou obtížnější při vývoji a údržbě.  
  
 Po vytvoření řídicích [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazů dotazů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] představují transformace výkonnou technologii, která se snadno používá. V podstatě můžete dokument XML vytvořit pomocí funkční konstrukce, nastavovat data z různých zdrojů, dynamicky vytvářet objekty a sestavovat <xref:System.Xml.Linq.XElement> celých objektů do nového stromu XML. Transformace může vygenerovat zcela nový dokument. Vytváření transformací v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je poměrně snadné a intuitivní a výsledný kód je čitelný. Tím se sníží náklady na vývoj a údržbu.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]není určena k nahrazení XSLT. XSLT je stále nástrojem volby pro komplikované a transformaci XML orientované na dokumenty, zejména v případě, že struktura dokumentu není správně definovaná.  
  
 XSLT má výhodu jako standard konsorcium World Wide Web (W3C). Pokud máte požadavek, abyste používali pouze technologie, které jsou standardy, může být soubor XSLT vhodnější.  
  
 XSLT je XML, a proto lze programově manipulovat.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML vs. MSXML  
 MSXML je technologie založená na modelu COM pro zpracování XML, která je součástí systému Microsoft Windows. Služba MSXML poskytuje nativní implementaci modelu DOM s podporou XPath a XSLT. Obsahuje také SAX2, který neukládá do mezipaměti, analyzátor založený na událostech.  
  
 Služba MSXML správně funguje, ve většině případů je zabezpečená a v aplikaci Internet Explorer je možné k provádění zpracování XML na straně klienta v aplikacích ve stylu AJAX. Službu MSXML lze použít z libovolného programovacího jazyka, který podporuje model COM, včetně jazyků C++, JavaScript a Visual Basic 6,0.  
  
 MSXML se nedoporučuje pro použití ve spravovaném kódu založeném na modulu CLR (Common Language Runtime).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML vs. analyzátor XmlLite  
 Analyzátor XmlLite není ukládání do mezipaměti, pouze k přeposílání, analyzátoru Pull. Vývojáři primárně používají analyzátor XmlLite s C++. Pro vývojáře se nedoporučuje používat analyzátor XmlLite se spravovaným kódem.  
  
 Hlavní výhodou analyzátoru XmlLite je, že se jedná o odlehčený a rychlý analyzátor XML, který je ve většině scénářů zabezpečený. Oblast jeho hrozby je velmi malá. Pokud je nutné analyzovat nedůvěryhodné dokumenty a chcete chránit před útoky, jako je třeba odepření služby nebo únik dat, může být analyzátor XmlLite vhodný pro možnost.  
  
 Analyzátor XmlLite není integrovaný do LINQ (Language-Integrated Query). Nepřinese vám vylepšení produktivity v programátorech, která jsou pro technologii LINQ vynucená.  
  
## <a name="see-also"></a>Viz také

- [Začínáme (LINQ to XML)](getting-started-linq-to-xml.md)
