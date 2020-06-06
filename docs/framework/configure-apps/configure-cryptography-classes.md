---
title: Konfigurace šifrovacích tříd
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927770"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="eddb5-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="eddb5-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="eddb5-103">Windows SDK umožňuje správcům počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které používají .NET Framework a správné psané aplikace.</span><span class="sxs-lookup"><span data-stu-id="eddb5-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="eddb5-104">Například podnik, který má vlastní implementaci kryptografického algoritmu, může tuto implementaci nastavit jako výchozí místo implementace dodávané v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="eddb5-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="eddb5-105">I když spravované aplikace, které používají kryptografii, se můžou vždy výslovně navazovat na konkrétní implementaci, doporučujeme, aby vytvářeli kryptografické objekty pomocí konfiguračního systému šifrování.</span><span class="sxs-lookup"><span data-stu-id="eddb5-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eddb5-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eddb5-106">In This Section</span></span>  
 [<span data-ttu-id="eddb5-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="eddb5-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="eddb5-108">Popisuje, jak namapovat název algoritmu na kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="eddb5-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="eddb5-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="eddb5-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="eddb5-110">Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="eddb5-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eddb5-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="eddb5-111">Related Sections</span></span>  
 [<span data-ttu-id="eddb5-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="eddb5-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="eddb5-113">Poskytuje přehled kryptografických služeb poskytovaných Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="eddb5-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="eddb5-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="eddb5-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="eddb5-115">Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="eddb5-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
