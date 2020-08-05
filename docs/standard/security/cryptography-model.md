---
title: Kryptografický model .NET
description: Projděte si implementace obvyklých kryptografických algoritmů v .NET. Seznamte se s rozšiřitelným kryptografickým modelem dědičnosti objektů, návrhem datového proudu a konfigurací &.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 0b3e07238bf0932572c222f7b947cfa7ae0221a9
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556992"
---
# <a name="net-cryptography-model"></a>Kryptografický model .NET

Rozhraní .NET poskytuje implementace mnoha standardních kryptografických algoritmů a model kryptografie .NET je rozšiřitelný.

## <a name="object-inheritance"></a>Dědičnost objektů

Systém kryptografie rozhraní .NET implementuje rozšiřitelný vzor dědičnosti odvozené třídy. Hierarchie je následující:

- Třída typu algoritmu, například <xref:System.Security.Cryptography.SymmetricAlgorithm> , <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm> . Tato úroveň je abstraktní.

- Třída algoritmu, která dědí z třídy typu algoritmu; Například,, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.RSA> nebo <xref:System.Security.Cryptography.ECDiffieHellman> . Tato úroveň je abstraktní.

- Implementace třídy algoritmu, která dědí z třídy algoritmu; Například,, <xref:System.Security.Cryptography.AesManaged> <xref:System.Security.Cryptography.RC2CryptoServiceProvider> nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Tato úroveň je plně implementovaná.

Tento vzor odvozených tříd umožňuje přidat nový algoritmus nebo novou implementaci existujícího algoritmu. Například pro vytvoření nového algoritmu veřejného klíče byste měli dědit z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy. Chcete-li vytvořit novou implementaci konkrétního algoritmu, je třeba vytvořit neabstraktní odvozenou třídu tohoto algoritmu.

## <a name="how-algorithms-are-implemented-in-net"></a>Způsob implementace algoritmů v rozhraní .NET

Jako příklad různých implementací dostupných pro algoritmus zvažte symetrické algoritmy. Základem všech symetrických algoritmů je <xref:System.Security.Cryptography.SymmetricAlgorithm> , který je zděděn pomocí <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.TripleDES> a dalších, které již nejsou doporučovány.

<xref:System.Security.Cryptography.Aes>dědí <xref:System.Security.Cryptography.AesCryptoServiceProvider> aplikace, <xref:System.Security.Cryptography.AesCng> a <xref:System.Security.Cryptography.AesManaged> .

V .NET Framework ve Windows:

* `*CryptoServiceProvider`třídy algoritmů, například <xref:System.Security.Cryptography.AesCryptoServiceProvider> , jsou obálkou v rámci implementace algoritmu rozhraní API kryptografických služeb systému Windows (CAPI).
* `*Cng`třídy algoritmů, jako <xref:System.Security.Cryptography.ECDiffieHellmanCng> jsou obálky, představují implementaci Kryptografické služby Windows Cryptography Next Generation (CNG).
* `*Managed`třídy, jako <xref:System.Security.Cryptography.AesManaged> jsou, jsou zapsány výhradně ve spravovaném kódu. `*Managed`implementace nejsou certifikovány standardy FIPS (Federal Information Processing Standards) a mohou být nižší než `*CryptoServiceProvider` `*Cng` obálkové třídy a.

V rozhraní .NET Core a .NET 5 a novějších verzích jsou všechny implementační třídy ( `*CryptoServiceProvider` , `*Managed` a `*Cng` ) obálky pro algoritmy operačního systému (OS). Pokud jsou algoritmy operačního systému certifikované pro Standard FIPS, používá .NET algoritmy s certifikací FIPS. Další informace najdete v tématu [kryptografie mezi platformami](cross-platform-cryptography.md).

Ve většině případů nemusíte přímo odkazovat na třídu implementace algoritmu, jako je například `AesCryptoServiceProvider` . Metody a vlastnosti, které obvykle potřebujete, jsou v základní třídě algoritmu, například `Aes` . Vytvořte instanci výchozí třídy implementace pomocí metody Factory v základní třídě algoritmu a přečtěte si základní třídu algoritmu. Podívejte se například na zvýrazněný řádek kódu v následujícím příkladu:

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a>Konfigurace kryptografie

Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmu pro název algoritmu, což umožňuje rozšiřitelnost tříd kryptografie .NET. Můžete přidat vlastní hardware nebo softwarovou implementaci algoritmu a namapovat implementaci na název algoritmu podle vašeho výběru. Pokud v konfiguračním souboru není zadaný algoritmus, použijí se výchozí nastavení.

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
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- Generuje se klíč z hesla:
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Viz také

- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
