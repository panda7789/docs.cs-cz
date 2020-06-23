---
title: Konfigurace šifrovacích tříd
description: Pochopte, jak můžou správci počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které využívají rozhraní .NET a aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5d12aae31ec78f80bea7df1bb0f37ac78dc37de2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105067"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="1b750-103">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="1b750-103">Configuring Cryptography Classes</span></span>
<span data-ttu-id="1b750-104">Windows SDK umožňuje správcům počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které používají .NET Framework a správné psané aplikace.</span><span class="sxs-lookup"><span data-stu-id="1b750-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="1b750-105">Například podnik, který má vlastní implementaci kryptografického algoritmu, může tuto implementaci nastavit jako výchozí místo implementace dodávané v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1b750-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="1b750-106">I když spravované aplikace, které používají kryptografii, se můžou vždy výslovně navazovat na konkrétní implementaci, doporučujeme, aby vytvářeli kryptografické objekty pomocí konfiguračního systému šifrování.</span><span class="sxs-lookup"><span data-stu-id="1b750-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b750-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1b750-107">In This Section</span></span>  
 [<span data-ttu-id="1b750-108">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="1b750-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="1b750-109">Popisuje, jak namapovat název algoritmu na kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="1b750-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="1b750-110">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="1b750-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="1b750-111">Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="1b750-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b750-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1b750-112">Related Sections</span></span>  
 [<span data-ttu-id="1b750-113">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="1b750-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="1b750-114">Poskytuje přehled kryptografických služeb poskytovaných Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1b750-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="1b750-115">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="1b750-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="1b750-116">Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="1b750-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
