---
title: Kryptografický model rozhraní .NET framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: f0c00e4cc866c537fe26dd1ad466d6cde95bc608
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706224"
---
# <a name="net-framework-cryptography-model"></a>Kryptografický model rozhraní .NET framework

.NET Framework poskytuje implementace mnoha standardních kryptografických algoritmů. Tyto algoritmy se snadno používají a mají nejbezpečnější možné výchozí vlastnosti. Kromě toho je model .NET Framework kryptografie dědičnosti objektů, návrh datového proudu a konfigurace velmi rozšiřitelný.

## <a name="object-inheritance"></a>Dědičnost objektů

Systém zabezpečení .NET Framework implementuje rozšiřitelný vzor dědičnosti odvozené třídy. Hierarchie je následující:

- Třída typu algoritmu, například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>. Tato úroveň je abstraktní.

- Třída algoritmu, která dědí z třídy typu algoritmu; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>nebo <xref:System.Security.Cryptography.ECDiffieHellman>. Tato úroveň je abstraktní.

- Implementace třídy algoritmu, která dědí z třídy algoritmu; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Tato úroveň je plně implementovaná.

Pomocí tohoto modelu odvozených tříd lze snadno přidat nový algoritmus nebo novou implementaci stávajícího algoritmu. Například pro vytvoření nového algoritmu veřejného klíče byste dědili z třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm>. Chcete-li vytvořit novou implementaci konkrétního algoritmu, je třeba vytvořit neabstraktní odvozenou třídu tohoto algoritmu.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Jak jsou implementovány algoritmy v .NET Framework

Jako příklad různých implementací dostupných pro algoritmus zvažte symetrické algoritmy. Základem všech symetrických algoritmů je <xref:System.Security.Cryptography.SymmetricAlgorithm>, které jsou zděděny následujícími algoritmy:

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes> dědí dvě třídy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>. Třída <xref:System.Security.Cryptography.AesCryptoServiceProvider> je Obálka kolem implementace rozhraní Windows Cryptography API (CAPI) pro AES, zatímco třída <xref:System.Security.Cryptography.AesManaged> je zapsána výhradně ve spravovaném kódu. Kromě implementace spravovaného rozhraní CAPI existuje také třetí typ implementace, kryptografická generace (CNG). Příkladem algoritmu CNG je <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algoritmy CNG jsou k dispozici v systému Windows Vista a novějších.

Můžete zvolit, která implementace je pro vás nejvhodnější.  Spravované implementace jsou k dispozici na všech platformách, které podporují .NET Framework.  Implementace rozhraní CAPI jsou k dispozici ve starších operačních systémech a již nejsou vyvíjeny. CNG je nejnovější implementace, při které bude provedeno nové vývojové prostředí. Spravované implementace však nejsou certifikovány standardy FIPS (Federal Information Processing Standards) a mohou být nižší než obálkové třídy.

## <a name="stream-design"></a>Návrh streamu

Modul common language runtime používá pro implementaci symetrických algoritmů a algoritmů hash návrh orientovaný na proud. Základem tohoto návrhu je <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena od <xref:System.IO.Stream> třídy. Kryptografické objekty založené na datových proudech podporují jedno standardní rozhraní (`CryptoStream`) pro zpracování části přenosu dat objektu. Vzhledem k tomu, že všechny objekty jsou postaveny na standardním rozhraní, můžete zřetězit více objektů (například objekt hash následovaný objektem šifrování) a můžete provádět více operací s daty, aniž byste pro ně potřebovali jakékoli zprostředkující úložiště. Model streamování také umožňuje vytvářet objekty z menších objektů. Například kombinované šifrování a algoritmus hash lze zobrazit jako jeden objekt datového proudu, i když tento objekt může být sestaven ze sady objektů datového proudu.

## <a name="cryptographic-configuration"></a>Konfigurace kryptografie

Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmu pro název algoritmu a umožňuje rozšiřitelnost .NET Frameworkch kryptografických tříd. Můžete přidat vlastní hardware nebo softwarovou implementaci algoritmu a namapovat implementaci na název algoritmu podle vašeho výběru. Pokud v konfiguračním souboru není zadaný algoritmus, použijí se výchozí nastavení. Další informace o konfiguraci kryptografie naleznete v tématu [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).

## <a name="choosing-an-algorithm"></a>Výběr algoritmu

Můžete vybrat algoritmus z různých důvodů: například pro integritu dat, pro ochranu osobních údajů nebo pro vygenerování klíče. Algoritmy symetrického a algoritmu hash jsou určené k ochraně dat z důvodů integrity (chráněných před změnou) nebo z důvodů ochrany osobních údajů (ochrana před zobrazením). Algoritmy hash jsou primárně používány pro integritu dat.

Tady je seznam doporučených algoritmů podle aplikace:

- Ochrana dat:

  - <xref:System.Security.Cryptography.Aes>

- Integrita dat:

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- Digitální podpis:

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- Výměna klíčů:

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- Náhodné číslo generace:

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- Generuje se klíč z hesla:

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
