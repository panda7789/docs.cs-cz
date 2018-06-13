---
title: Podpora identifikátor mezinárodní prostředků v System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bf26f98773383ee6671162a53b84f155c18b5adf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398246"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Podpora identifikátor mezinárodní prostředků v System.Uri
<xref:System.Uri?displayProperty=nameWithType> Třída rozšířilo s podporou mezinárodní názvy domén (IDN) a mezinárodní prostředků identifikátor (IRI). Tato vylepšení jsou k dispozici v rozhraní .NET Framework 3.5 3.0 SP1 a 2.0 SP1.  
  
## <a name="iri-and-idn-support"></a>IRI a podporu IDN.  
 Webové adresy jsou obvykle vyjádřit pomocí identifikátorů URI (Uniform Resource) s velmi omezenou sadu znaků:  
  
-   Velká a malá písmena znaků ASCII – písmena anglické abecedy.  
  
-   Číslice od 0 do 9.  
  
-   Malý počet dalších symboly ASCII.  
  
 Specifikace pro identifikátory URI jsou popsány v dokumentu RFC 2396 a RFC 3986 publikovaná Internet Engineering Task Force (IETF).  
  
 S nárůstem Internetu se zvyšuje potřeba k identifikaci prostředků pomocí jiných jazyků než angličtiny. Identifikátory, které usnadňují tohoto požadavku a povolit jiné znaky než ASCII (znaky znakové sady Unicode nebo ISO 10646) jsou označovány jako identifikátory prostředků mezinárodní (IRIs). Specifikace pro IRIs jsou popsány v dokumentu RFC 3987 publikovaná sdružení IETF DEFINUJE. Použití IRIs umožňuje adresu URL tak, aby obsahovala znaky Unicode.  
  
 Existující <xref:System.Uri?displayProperty=nameWithType> třída rozšířilo a poskytovat podporu IRI podle RFC 3987. Aktuální uživatelé neuvidí žádné chování se liší od rozhraní .NET Framework 2.0, pokud se konkrétně povolit IRI. Tím se zajistí kompatibilitu aplikace s předchozí verze rozhraní .NET Framework.  
  
 Aplikace můžete určit, zda chcete použít mezinárodní název domény (IDN) analýza u názvů domén a zda má být použita IRI Analýza pravidla. To lze provést v souboru machine.config nebo v souboru app.config.  
  
 Povolení IDN převede všechny popisky kódování Unicode v názvu domény jejich ekvivalenty u Punycode. Názvy Punycode obsahovat pouze znaky ASCII a vždy začínají předponou xn –. Důvodem je podpora existující servery DNS na Internetu, protože většina servery DNS podporují pouze znaky ASCII (viz RFC 3940).  
  
 Povolení IRI a IDN. hodnota bude mít vliv <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> vlastnost. Povolení IRI a IDN. můžete také změnit chování <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, a <xref:System.Uri.IsWellFormedOriginalString%2A> metody.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Třída rozšířilo také umožňuje vytvoření přizpůsobitelné analyzátor, který podporuje IRI a IDN. Chování <xref:System.GenericUriParser?displayProperty=nameWithType> předáním bitovou kombinaci hodnot, které jsou k dispozici v je zadaný objekt <xref:System.GenericUriParserOptions?displayProperty=nameWithType> výčet <xref:System.GenericUriParser?displayProperty=nameWithType> konstruktor. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Typ určuje analyzátor podporuje analýzy pravidla stanovená v dokumentu RFC 3987 pro mezinárodní prostředků identifikátory (IRI). Jestli je ve skutečnosti používat IRI závisí na Pokud je povoleno IRI.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Typ určuje analyzátor podporuje mezinárodní domény název (IDN) analýza (IDN) názvů hostitelů. Určuje, zda IDN ve skutečnosti použije, závisí na Pokud je povoleno IDN.  
  
 Povolení IRI analýza provede normalizaci a znak kontrola podle nejnovější IRI pravidla v dokumentu RFC 3987. Výchozí hodnota je pro IRI analýza zakážete normalizaci a kontrola znak se provádějí podle RFC 2396 a RFC 3986.  
  
 IRI a IDN zpracování v <xref:System.Uri?displayProperty=nameWithType> třídy můžete řídit také pomocí <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> a <xref:System.Configuration.IdnElement?displayProperty=nameWithType> třídy nastavení konfigurace. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Nastavení povolí nebo zakáže IRI zpracování v <xref:System.Uri?displayProperty=nameWithType> třídy. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Nastavení povolí nebo zakáže IDN zpracování v <xref:System.Uri> třídy. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Taky nepřímo nastavení řídí IDN. Zpracování IRI musí být povolen pro zpracování tak, aby možné IDN. Pokud IRI zpracování je zakázána, bude zpracování IDN nastavit výchozí nastavení, kde chování rozhraní .NET Framework 2.0 se používá pro kompatibilitu a IDN. názvy nejsou.  
  
 Nastavení konfigurace pro <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> a <xref:System.Configuration.IdnElement?displayProperty=nameWithType> třídy konfigurace bude načten jednou při první <xref:System.Uri?displayProperty=nameWithType> třída je vytvořený. Změny nastavení konfigurace po uplynutí této doby se ignorují.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
