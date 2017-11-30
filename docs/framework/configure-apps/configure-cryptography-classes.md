---
title: "Konfigurace šifrovacích tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 79eb9f9ef95dae24dd38fa93b137c9303815143b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="9a82f-102">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="9a82f-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="9a82f-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umožňuje správci počítače a nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které používají rozhraní .NET Framework a správně vytvořené aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a82f-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="9a82f-104">Například organizace, která má svou vlastní implementaci kryptografických algoritmů můžete Ujistěte se, že implementace výchozí místo implementace poskytuje [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a82f-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="9a82f-105">I když spravovaných aplikací, které používají šifrování se vždy mohou rozhodnout explicitně vytvořit vazbu na konkrétní implementace, se doporučuje, aby vytvořili kryptografických objekty pomocí kryptografických konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="9a82f-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a82f-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9a82f-106">In This Section</span></span>  
 [<span data-ttu-id="9a82f-107">Mapování názvů algoritmů na třídy šifrování</span><span class="sxs-lookup"><span data-stu-id="9a82f-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="9a82f-108">Popisuje, jak mapovat název algoritmu šifrování třídu.</span><span class="sxs-lookup"><span data-stu-id="9a82f-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="9a82f-109">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="9a82f-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="9a82f-110">Popisuje, jak mapovat identifikátor objektu algoritmus šifrování.</span><span class="sxs-lookup"><span data-stu-id="9a82f-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a82f-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9a82f-111">Related Sections</span></span>  
 [<span data-ttu-id="9a82f-112">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="9a82f-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="9a82f-113">Obsahuje základní informace o kryptografických služeb poskytovaných [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a82f-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="9a82f-114">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="9a82f-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="9a82f-115">Popisuje elementy, které mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="9a82f-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
