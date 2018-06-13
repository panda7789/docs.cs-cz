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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b12d5d95a17439308d79d094e8c22206778f3128
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743248"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="cdfb1-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="cdfb1-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="cdfb1-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umožňuje správci počítače a nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které používají rozhraní .NET Framework a správně vytvořené aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdfb1-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="cdfb1-104">Například organizace, která má svou vlastní implementaci kryptografických algoritmů můžete Ujistěte se, že implementace výchozí místo implementace poskytuje [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdfb1-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="cdfb1-105">I když spravovaných aplikací, které používají šifrování se vždy mohou rozhodnout explicitně vytvořit vazbu na konkrétní implementace, se doporučuje, aby vytvořili kryptografických objekty pomocí kryptografických konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="cdfb1-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdfb1-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cdfb1-106">In This Section</span></span>  
 [<span data-ttu-id="cdfb1-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="cdfb1-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="cdfb1-108">Popisuje, jak mapovat název algoritmu šifrování třídu.</span><span class="sxs-lookup"><span data-stu-id="cdfb1-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="cdfb1-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="cdfb1-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="cdfb1-110">Popisuje, jak mapovat identifikátor objektu algoritmus šifrování.</span><span class="sxs-lookup"><span data-stu-id="cdfb1-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cdfb1-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cdfb1-111">Related Sections</span></span>  
 [<span data-ttu-id="cdfb1-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="cdfb1-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="cdfb1-113">Obsahuje základní informace o kryptografických služeb poskytovaných [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdfb1-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="cdfb1-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="cdfb1-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="cdfb1-115">Popisuje elementy, které mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="cdfb1-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
