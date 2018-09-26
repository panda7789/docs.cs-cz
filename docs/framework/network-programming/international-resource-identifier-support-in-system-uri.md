---
title: Podpora mezinárodních identifikátorů prostředků v System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ef44453dce2f59a2b481d0533b8bd28de516c630
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156563"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Podpora mezinárodních identifikátorů prostředků v System.Uri
<xref:System.Uri?displayProperty=nameWithType> Třídy bylo rozšířeno pomocí International Resource Identifier (IRI) a podporu mezinárodní názvy domén (IDN). Tato vylepšení jsou k dispozici v rozhraní .NET Framework 3.5, 3.0 SP1 a 2.0 SP1.  
  
## <a name="iri-and-idn-support"></a>IRI a podporu IDN  
 Webové adresy jsou obvykle vyjádřeny pomocí identifikátorů URI (Uniform Resource), které obsahují velmi omezené sady znaků:  
  
-   Velká a malá písmena znaků ASCII – písmena anglické abecedy.  
  
-   Číslice od 0 do 9.  
  
-   Malý počet dalších symbolů ASCII.  
  
 Specifikace pro identifikátory URI jsou popsány v dokumentu RFC 2396 a RFC 3986 publikovaná pomocí Engineering Task Force IETF (Internet).  
  
 S nárůstem Internet je rostoucí potřebu pro identifikaci prostředků, pomocí jiné jazyky než angličtinu. Identifikátory, které usnadňují potřebě a umožňují jiné znaky než ASCII (znaků ve znakové sadě Unicode/ISO 10646) jsou označovány jako International Resource Identifier (IRIs). Specifikace pro IRIs jsou popsány v dokumentu RFC 3987 publikoval(a) IETF. Použití IRIs umožňuje adresu URL tak, aby obsahovala znaky Unicode.  
  
 Existující <xref:System.Uri?displayProperty=nameWithType> třídy se prodloužila, k poskytování podpory IRI podle RFC 3987. Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud jsou specificky nepovolíte IRI. Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.  
  
 Aplikace můžete určit, jestli se má použít, analýze mezinárodních názvů domén (IDN) použitý pro názvy domén a určuje, zda by měl použít IRI pravidel pro analýzu. To můžete udělat v souboru machine.config nebo v souboru app.config.  
  
 Povolení IDN převede všechny popisky kódování Unicode v názvu domény na jejich ekvivalenty kódování Punycode. Kódování Punycode názvy obsahovat pouze znaky ASCII a vždy začínají předponou xn –. Důvodem je k podpoře existujících serverů DNS na Internetu, protože většina servery DNS podporují jenom znaky ASCII (viz RFC 3940).  
  
 Povolení IRI a IDN hodnota bude mít vliv <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> vlastnost. Povolení IRI a IDN můžete také změnit chování <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, a <xref:System.Uri.IsWellFormedOriginalString%2A> metody.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Třídy také bylo rozšířeno umožňující vytvoření přizpůsobitelné analyzátor, který podporuje IRI a IDN. Chování <xref:System.GenericUriParser?displayProperty=nameWithType> zadán objekt předáním bitová kombinace hodnot, které jsou k dispozici v <xref:System.GenericUriParserOptions?displayProperty=nameWithType> výčet <xref:System.GenericUriParser?displayProperty=nameWithType> konstruktoru. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Označuje analyzátor podporuje analýzy pravidel specifikovaných v dokumentu RFC 3987 pro identifikátory mezinárodní prostředků (IRI). Určuje, zda se ve skutečnosti používá IRI závisí na Pokud IRI je povolená.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Označuje analyzátor podporuje mezinárodních názvů domén (IDN) analýza (IDN) názvy hostitelů. Určuje, zda se ve skutečnosti používá IDN závisí na Pokud je povoleno IDN.  
  
 Povolení IRI parsování provede normalizaci a znak kontroly podle nejnovějších IRI pravidla v dokumentu RFC 3987. Výchozí hodnota je pro IRI parsování zakážete normalizace a znak kontroluje dokončení podle RFC 2396 a RFC 3986.  
  
 IRI a zpracování v IDN <xref:System.Uri?displayProperty=nameWithType> třídy je možné řídit také pomocí <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> a <xref:System.Configuration.IdnElement?displayProperty=nameWithType> třídy nastavení konfigurace. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Nastavení povolí nebo zakáže IRI zpracování <xref:System.Uri?displayProperty=nameWithType> třídy. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Nastavení povolí nebo zakáže zpracování v IDN <xref:System.Uri> třídy. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Nastavení taky nepřímo řídí IDN. Zpracování IRI musí být povolena pro zpracování bude možné IDN. Pokud IRI zpracování je zakázané, bude zpracování IDN nastavit na výchozí nastavení, pokud rozhraní .NET Framework 2.0 chování slouží k zajištění kompatibility a nepoužívají se názvy IDN.  
  
 Nastavení konfigurace pro <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> a <xref:System.Configuration.IdnElement?displayProperty=nameWithType> třídy pro konfiguraci se budou číst jednou při prvním <xref:System.Uri?displayProperty=nameWithType> třídy. Změny nastavení konfigurace po uplynutí této doby se ignorují.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
