---
title: Podpora mezinárodních identifikátorů prostředků v System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: f78fff250aae177b5f0360e77a1c41a2f2bb0527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64647341"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Podpora mezinárodních identifikátorů prostředků v System.Uri
Třída <xref:System.Uri?displayProperty=nameWithType> byla rozšířena o podporu Mezinárodního identifikátoru prostředků (IRI) a Mezinárodní názvy domén (IDN). Tato vylepšení jsou k dispozici v rozhraních .NET Framework 3.5, 3.0 SP1 a 2.0 SP1.  
  
## <a name="iri-and-idn-support"></a>Podpora IRI a IDN  
 Webové adresy jsou obvykle vyjádřeny pomocí identifikátorů URI (Uniform Resource Identifiers), které se skládají z velmi omezené sady znaků:  
  
- Velká a malá písmena ASCII z anglické abecedy.  
  
- Číslice od 0 do 9.  
  
- Malý počet dalších symbolů ASCII.  
  
 Specifikace pro identifikátory URI jsou dokumentovány v dokumentech RFC 2396 a RFC 3986 publikovaných skupinou IETF (Internet Engineering Task Force).  
  
 S růstem internetu, tam je rostoucí potřeba identifikovat zdroje pomocí jiných jazyků než angličtiny. Identifikátory, které usnadňují tuto potřebu a umožňují znaky než ASCII (znaky v znakové sadě Unicode/ISO 10646), jsou označovány jako identifikátory mezinárodních prostředků (IIR). Specifikace pro idi jsou zdokumentovány v RFC 3987 zveřejněné iETF. Použití ifbi umožňuje adresu URL obsahovat znaky Unicode.  
  
 Stávající <xref:System.Uri?displayProperty=nameWithType> třída byla rozšířena o podporu IRI na základě RFC 3987. Aktuální uživatelé neuvidí žádnou změnu z chování rozhraní .NET Framework 2.0, pokud konkrétně nepovolí IRI. Tím je zajištěna kompatibilita aplikací s předchozími verzemi rozhraní .NET Framework.  
  
 Aplikace může určit, zda má být použita analýza mezinárodního názvu domény (IDN) použitá u názvů domén a zda mají být použita pravidla analýzy IRI. To lze provést v souboru machine.config nebo v souboru app.config.  
  
 Povolení mnoství IDN převede všechny popisky Unicode v názvu domény na jejich ekvivalenty Punycode. Punycode názvy obsahují pouze znaky ASCII a vždy začínat xn-- předponou. Důvodem je podpora existujících serverů DNS v Internetu, protože většina serverů DNS podporuje pouze znaky ASCII (viz RFC 3940).  
  
 Povolení IRI a IDN ovlivňuje <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> hodnotu vlastnosti. Povolení IRI a IDN můžete také <xref:System.Uri.Equals%2A?displayProperty=nameWithType> <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>změnit <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>chování <xref:System.Uri.IsWellFormedOriginalString%2A> , , a metody.  
  
 Třída <xref:System.GenericUriParser?displayProperty=nameWithType> byla také rozšířena tak, aby umožnila vytvoření přizpůsobitelného analyzátoru, který podporuje IRI a IDN. Chování objektu <xref:System.GenericUriParser?displayProperty=nameWithType> je určeno předáním bitové kombinace hodnot, <xref:System.GenericUriParserOptions?displayProperty=nameWithType> které jsou <xref:System.GenericUriParser?displayProperty=nameWithType> k dispozici ve výčtu konstruktoru. Typ <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> označuje, že analyzátor podporuje pravidla analýzy zadaná v rfc 3987 pro mezinárodní identifikátory prostředků (IRI). Zda je IRI skutečně používán, závisí na tom, zda je povolena IRI.  
  
 Typ <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> označuje, že analyzátor podporuje analýzu mezinárodního názvu domény (IDN) (IDN) názvů hostitelů. Zda je idn skutečně používá, závisí na tom, zda je povoleno IDN.  
  
 Povolení analýzy IRI provede normalizaci a kontrolu znaků podle nejnovějších pravidel IRI v RFC 3987. Výchozí hodnota je pro analýzu IRI, která má být zakázána, takže normalizace a kontrola znaků se provádí podle RFC 2396 a RFC 3986.  
  
 Zpracování IRI a IDN ve <xref:System.Uri?displayProperty=nameWithType> třídě lze <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> také řídit pomocí tříd nastavení konfigurace a. Nastavení <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> povolí nebo zakáže zpracování <xref:System.Uri?displayProperty=nameWithType> IRI ve třídě. Nastavení <xref:System.Configuration.IdnElement?displayProperty=nameWithType> povolí nebo zakáže zpracování <xref:System.Uri> IDN ve třídě. Nastavení <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> také nepřímo řídí IDN. Aby bylo zpracování IDN možné, musí být povoleno zpracování IRI. Pokud je zpracování IRI zakázáno, bude zpracování IDN nastaveno na výchozí nastavení, kde se pro kompatibilitu používá chování rozhraní .NET Framework 2.0 a názvy IDN se nepoužívají.  
  
 Nastavení konfigurace pro <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> třídy a konfigurace bude <xref:System.Uri?displayProperty=nameWithType> číst jednou při vytvoření první třídy. Změny nastavení konfigurace po uplynutí této doby jsou ignorovány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
