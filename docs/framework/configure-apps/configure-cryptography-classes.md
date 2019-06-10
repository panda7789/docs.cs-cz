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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816173"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="8b146-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="8b146-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="8b146-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umožňuje správcům počítači nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které rozhraní .NET Framework a odpovídajícím způsobem vytvořené aplikace použít.</span><span class="sxs-lookup"><span data-stu-id="8b146-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="8b146-104">Například organizace, která má vlastní implementaci kryptografický algoritmus mohli tuto implementaci výchozí místo implementace dodávané v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8b146-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="8b146-105">I když spravovaných aplikací, které používají šifrování lze vybrat vždy explicitně vytvořit vazbu na konkrétní implementaci, se doporučuje, že kryptografické objekty vytvořit pomocí konfigurace kryptografie systému.</span><span class="sxs-lookup"><span data-stu-id="8b146-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b146-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8b146-106">In This Section</span></span>  
 [<span data-ttu-id="8b146-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="8b146-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="8b146-108">Popisuje, jak namapovat název algoritmu na kryptografickou třídu.</span><span class="sxs-lookup"><span data-stu-id="8b146-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="8b146-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="8b146-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="8b146-110">Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.</span><span class="sxs-lookup"><span data-stu-id="8b146-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b146-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8b146-111">Related Sections</span></span>  
 [<span data-ttu-id="8b146-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="8b146-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="8b146-113">Poskytuje přehled kryptografických služeb sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8b146-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="8b146-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="8b146-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="8b146-115">Popisuje elementy, které mapují popisné názvy algoritmů tříd, které implementují algoritmy šifrování.</span><span class="sxs-lookup"><span data-stu-id="8b146-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
