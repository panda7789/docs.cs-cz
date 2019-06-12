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
ms.openlocfilehash: 23bf831a4374add55258f5fb41c17a5d4a8f14c3
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832817"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="ff446-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="ff446-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="ff446-103">Windows Software Development Kit (SDK) umožňuje správcům počítači nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které rozhraní .NET Framework a odpovídajícím způsobem vytvořené aplikace použít.</span><span class="sxs-lookup"><span data-stu-id="ff446-103">The Windows Software Development Kit (SDK) allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="ff446-104">Například organizace, která má vlastní implementaci kryptografický algoritmus mohli tuto implementaci výchozí místo implementace dodávané v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ff446-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="ff446-105">I když spravovaných aplikací, které používají šifrování lze vybrat vždy explicitně vytvořit vazbu na konkrétní implementaci, se doporučuje, že kryptografické objekty vytvořit pomocí konfigurace kryptografie systému.</span><span class="sxs-lookup"><span data-stu-id="ff446-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff446-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ff446-106">In This Section</span></span>  
 [<span data-ttu-id="ff446-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="ff446-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="ff446-108">Popisuje, jak namapovat název algoritmu na kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="ff446-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="ff446-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="ff446-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="ff446-110">Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="ff446-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff446-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ff446-111">Related Sections</span></span>  
 [<span data-ttu-id="ff446-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="ff446-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="ff446-113">Poskytuje přehled kryptografických služeb sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ff446-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="ff446-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="ff446-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="ff446-115">Popisuje elementy, které mapují popisné názvy algoritmů tříd, které implementují algoritmy šifrování.</span><span class="sxs-lookup"><span data-stu-id="ff446-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
