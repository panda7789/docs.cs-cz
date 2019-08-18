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
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567330"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="15370-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="15370-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="15370-103">Windows SDK umožňuje správcům počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které používají .NET Framework a správné psané aplikace.</span><span class="sxs-lookup"><span data-stu-id="15370-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="15370-104">Například podnik, který má vlastní implementaci kryptografického algoritmu, může tuto implementaci nastavit jako výchozí místo implementace dodávané v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="15370-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="15370-105">I když spravované aplikace, které používají kryptografii, se můžou vždy výslovně navazovat na konkrétní implementaci, doporučujeme, aby vytvářeli kryptografické objekty pomocí konfiguračního systému šifrování.</span><span class="sxs-lookup"><span data-stu-id="15370-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15370-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="15370-106">In This Section</span></span>  
 [<span data-ttu-id="15370-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="15370-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="15370-108">Popisuje, jak namapovat název algoritmu na kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="15370-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="15370-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="15370-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="15370-110">Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="15370-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15370-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="15370-111">Related Sections</span></span>  
 [<span data-ttu-id="15370-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="15370-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="15370-113">Poskytuje přehled kryptografických služeb poskytovaných Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="15370-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="15370-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="15370-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="15370-115">Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="15370-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
