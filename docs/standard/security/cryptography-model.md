---
title: "Kryptografický model rozhraní .NET framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 842ebbe9104463a3c75f01f41a4fe5953b95303d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-framework-cryptography-model"></a>Kryptografický model rozhraní .NET framework
Rozhraní .NET Framework poskytuje implementace mnoho standardní kryptografických algoritmů. Tyto algoritmy jsou snadno použitelné a mají nejbezpečnější možné výchozí vlastnosti. Kromě toho je velmi extensible Kryptografický model rozhraní .NET Framework objekt dědičnosti, datový proud návrh a konfigurace.  
  
## <a name="object-inheritance"></a>Objekt dědičnosti  
 Systém zabezpečení rozhraní .NET Framework implementuje rozšiřitelné vzory odvozené dědičnosti tříd. V hierarchii je následující:  
  
-   Typ algoritmu třídy, jako například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>. Tato úroveň je abstraktní.  
  
-   Třída algoritmu, který dědí z třídy typu algoritmus; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, nebo <xref:System.Security.Cryptography.ECDiffieHellman>. Tato úroveň je abstraktní.  
  
-   Implementace třídy algoritmu, který dědí z třídy algoritmus; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Tato úroveň je plně implementováno.  
  
 Pomocí tohoto vzoru odvozených tříd, je snadné přidání nového algoritmu nebo nové implementace existujícího algoritmu. Například pokud chcete vytvořit nový algoritmus veřejného klíče, by dědění ze <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy. K vytvoření nové implementace konkrétní algoritmem, by vytvořit třídu odvozené neabstraktní tento algoritmus.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak jsou implementované algoritmy v rozhraní .NET Framework  
 Jako příklad různé implementace, které jsou k dispozici pro algoritmus vezměte v úvahu symetrické algoritmy. Základ pro všechny symetrické algoritmy je <xref:System.Security.Cryptography.SymmetricAlgorithm>, který zdědí tyto algoritmy:  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes>zdědí dvě třídy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Třída je obálku kolem implementace rozhraní API kryptografie systému Windows (CAPI) Aes, zatímco <xref:System.Security.Cryptography.AesManaged> třída je zapsán zcela ve spravovaném kódu. Je také třetí typ implementace Cryptography Next Generation (CNG), v CAPI implementace a přidání do spravovaný. Je například algoritmus CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>. CNG algoritmy jsou k dispozici v systému Windows Vista nebo novější.  
  
 Můžete zvolit, které implementace je pro vás nejvhodnější.  Spravované implementace jsou k dispozici na všech platformách, které podporují rozhraní .NET Framework.  Implementace CAPI jsou dostupné ve starších operačních systémech a jsou už vyvíjených. CNG je velmi nejnovější implementace, kde bude probíhat vývoj nových. Spravované implementace však nejsou certifikovány podle na zpracování standardů FIPS (Federal Information) a může být pomalejší než obálkové třídy.  
  
## <a name="stream-design"></a>Návrh datového proudu  
 Modul common language runtime používá návrh orientované na datový proud pro implementaci symetrické algoritmy a algoritmů hash. Je základní tohoto návrhu <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena z <xref:System.IO.Stream> třídy. Na základě datového proudu kryptografické objekty podporují jediné standardní rozhraní (`CryptoStream`) pro zpracování datové části přenosu objektu. Vzhledem k tomu, že všechny objekty jsou postaveny na standardní rozhraní, můžete společně zřetězit více objektů (například objekt algoritmu hash a potom objektem šifrování), a můžete provádět více operací na základě dat bez nutnosti jakékoli zprostředkující úložiště pro ni. Streamování modelu také umožňuje vytvářet objekty z menších objektů. Například Kombinovaný algoritmus šifrování a hash lze zobrazit jako objekt jednoho datového proudu, i když tento objekt může být sestaven z sadu objektů datového proudu.  
  
## <a name="cryptographic-configuration"></a>Konfigurace kryptografie  
 Konfigurace kryptografie umožňuje vyřešit konkrétní implementaci algoritmu na název algoritmu, což rozšíření tříd šifrování .NET Framework. Můžete přidat vlastní hardware nebo software implementaci algoritmu a mapovat implementaci název algoritmu podle svého výběru. Pokud není algoritmus zadané v konfiguračním souboru, použijí se výchozí nastavení. Další informace o kryptografických konfiguraci najdete v tématu [konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Výběr algoritmu  
 Můžete vybrat algoritmus různých důvodů: například pro integritu dat, ochrany osobních údajů, nebo informace o generování klíče. Algoritmy Symmetric a hash jsou určeny k ochraně dat pro integritu důvodů (chránit před změn) nebo z důvodů ochrany osobních údajů (ochrana ze zobrazení). Algoritmy hash se používají primárně pro integritu dat.  
  
 Tady je seznam doporučené algoritmy aplikací:  
  
-   Ochrana dat:  
  
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
  
-   Generování klíče z hesla:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)  
 
