---
title: Schéma nastavení šifrování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 6b6d9eeacb38531ced5768f29bf26de3c9294b71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="6ec8c-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="6ec8c-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="6ec8c-103">Schéma nastavení šifrování obsahuje prvky, které určují, jak k mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="6ec8c-104">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="6ec8c-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="6ec8c-106">**\<cryptographySettings – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="6ec8c-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="6ec8c-108">**\<cryptoClasses – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="6ec8c-109">**\<cryptoclass – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="6ec8c-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="6ec8c-111">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="6ec8c-112">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="6ec8c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ec8c-113">Element</span></span>|<span data-ttu-id="6ec8c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6ec8c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ec8c-115">**\<cryptoClasses –**></span><span class="sxs-lookup"><span data-stu-id="6ec8c-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="6ec8c-116">Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do  **\<nameEntry >** element.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="6ec8c-117">**\<cryptoclass –**></span><span class="sxs-lookup"><span data-stu-id="6ec8c-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="6ec8c-118">Obsahuje třídy šifrování, která má mapování na popisného názvu do  **\<nameEntry >** element.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="6ec8c-119">**\<cryptographySettings –**></span><span class="sxs-lookup"><span data-stu-id="6ec8c-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="6ec8c-120">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="6ec8c-121">**\<cryptoNameMapping –**></span><span class="sxs-lookup"><span data-stu-id="6ec8c-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="6ec8c-122">Obsahuje mapování třídy popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="6ec8c-123">**\<mscorlib >** element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="6ec8c-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="6ec8c-124">Obsahuje  **\<cryptographySettings – >** element.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="6ec8c-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="6ec8c-126">Mapuje název třídy algoritmus popisný název, který umožňuje jednu třídu k mít mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="6ec8c-127">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="6ec8c-128">Mapuje ASN.1 identifikátor objektu (OID) popisný název.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="6ec8c-129">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="6ec8c-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="6ec8c-130">Obsahuje ASN.1 OID mapování třídy.</span><span class="sxs-lookup"><span data-stu-id="6ec8c-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ec8c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ec8c-131">See Also</span></span>  
 [<span data-ttu-id="6ec8c-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6ec8c-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6ec8c-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="6ec8c-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
