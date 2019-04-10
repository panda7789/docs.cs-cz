---
title: Kryptografický model rozhraní .NET framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a60f03d85997d20b54366360f104519c9c75f5e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343867"
---
# <a name="net-framework-cryptography-model"></a>Kryptografický model rozhraní .NET framework
Rozhraní .NET Framework poskytuje mnoho standardních kryptografických algoritmů implementace. Tyto algoritmy jsou snadné použití a nejbezpečnější možné výchozí vlastnosti. Kryptografický model rozhraní .NET Framework dědičnost objektů, stream návrhu a konfigurace je také velmi rozšiřitelné.  
  
## <a name="object-inheritance"></a>Dědičnost objektů  
 Systém zabezpečení rozhraní .NET Framework implementuje extensible vzor odvozené dědičnosti tříd. Hierarchie vypadá takto:  
  
-   Třídy typu algoritmu, jako například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>. Tato úroveň je abstraktní.  
  
-   Třída algoritmu, který dědí z třídy typu algoritmu; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, nebo <xref:System.Security.Cryptography.ECDiffieHellman>. Tato úroveň je abstraktní.  
  
-   Implementace třídy algoritmus, který dědí z třídy algoritmus; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Tato úroveň je plně implementovány.  
  
 Použití tohoto modelu odvozené třídy, je snadné přidat nový algoritmus nebo nové implementace algoritmu existující. Například pokud chcete vytvořit nový algoritmus veřejného klíče, by dědění z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy. Chcete-li vytvořit nové implementace algoritmu konkrétní, vytvořili byste Odvozené neabstraktní třídy tohoto algoritmu.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak se implementují algoritmy v rozhraní .NET Framework  
 Jako příklad různé implementace, které jsou k dispozici pro algoritmus vezměte v úvahu symetrické algoritmy. Základ pro všechny symetrické algoritmy je <xref:System.Security.Cryptography.SymmetricAlgorithm>, která dědí tyto algoritmy:  
  
1. <xref:System.Security.Cryptography.Aes>  
  
2. <xref:System.Security.Cryptography.DES>  
  
3. <xref:System.Security.Cryptography.RC2>  
  
4. <xref:System.Security.Cryptography.Rijndael>  
  
5. <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> zdědí dvou tříd: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Třída představuje obálku kolem Windows Cryptography API (CAPI) provádění Aes, zatímco <xref:System.Security.Cryptography.AesManaged> třídy je vytvořené zcela v spravovaném kódu. Existuje také třetí typ implementace, Cryptography Next Generation (CNG), také na spravovanou a CAPI implementace. Je například algoritmus CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algoritmy CNG jsou k dispozici v systému Windows Vista nebo novější.  
  
 Můžete zvolit, která implementace je pro vás nejvhodnější.  Spravované implementace jsou k dispozici na všech platformách, které podporují rozhraní .NET Framework.  Implementace CAPI jsou k dispozici ve starších operačních systémech a jsou už nevyvíjí. CNG je velmi nejnovější implementace, ve kterém bude probíhat vývoj nových projektů. Spravované implementace však nejsou certifikovány podle informace o zpracování normy FIPS (Federal) a může být pomalejší než obálkové třídy.  
  
## <a name="stream-design"></a>Stream návrhu  
 Modul common language runtime používá orientovaný na stream návrhu pro implementaci symetrické algoritmy a hashovacích algoritmů. Je základní tento návrh <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena z <xref:System.IO.Stream> třídy. Na základě Stream kryptografických objekty podporují rozhraní jediným standardním (`CryptoStream`) pro zpracování části přenosu dat objektu. Vzhledem k tomu, že všechny objekty jsou postavené na standardní rozhraní, můžete zřetězit dohromady víc objektů (například objekt algoritmu hash, za nímž následuje objekt šifrování) a můžete provádět více operací s daty bez nutnosti jakékoli sloužící jako přechodné úložiště pro něj. Streamování modelu také umožňuje vytvářet objekty z menších objektů. Kombinované šifrování a hashovací algoritmus může například zobrazit jako objekt jeden datový proud, i když tento objekt může být sestavena na základě sady objektů datového proudu.  
  
## <a name="cryptographic-configuration"></a>Cryptographic Configuration  
 Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmus název algoritmu, což rozšíření tříd šifrování .NET Framework. Můžete přidat vlastní hardware ani software provádění algoritmu a implementaci namapovat název algoritmu podle vašeho výběru. Pokud algoritmus není zadané v konfiguračním souboru, použijí se výchozí nastavení. Další informace o kryptografická konfigurace najdete v tématu [konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Výběr algoritmu  
 Algoritmus můžete vybrat z různých důvodů: třeba pro integritu dat, ochrany osobních údajů nebo ke generování klíče. Symmetric a hashovací algoritmy jsou určené pro ochranu dat z důvodu zachování integrity (Ochrana před změnami) nebo z důvodů ochrany osobních údajů (ochrana ze zobrazení). Algoritmy hash se používají především pro integritu dat.  
  
 Tady je seznam doporučených algoritmy aplikací:  
  
-   Data o ochraně osobních údajů:  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   Integrita dat:  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   Digitální podpis:  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Výměna klíčů:  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Náhodné generování čísel:  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   Generuje se klíč z hesla:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Viz také:

- [Šifrovací služby](../../../docs/standard/security/cryptographic-services.md)
