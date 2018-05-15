---
title: Schéma nastavení šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b7f41bc477f8d8095bf73859c02b7e2fc2443c14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="7193a-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="7193a-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="7193a-103">Schéma nastavení šifrování obsahuje prvky, které určují, jak k mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="7193a-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="7193a-104">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="7193a-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="7193a-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="7193a-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="7193a-106">**\<cryptographySettings – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="7193a-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="7193a-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="7193a-108">**\<cryptoClasses – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="7193a-109">**\<cryptoclass – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="7193a-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="7193a-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="7193a-111">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="7193a-112">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="7193a-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="7193a-113">Element</span></span>|<span data-ttu-id="7193a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7193a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7193a-115">**\<cryptoClasses –**></span><span class="sxs-lookup"><span data-stu-id="7193a-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="7193a-116">Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do  **\<nameEntry >** element.</span><span class="sxs-lookup"><span data-stu-id="7193a-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7193a-117">**\<cryptoclass –**></span><span class="sxs-lookup"><span data-stu-id="7193a-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="7193a-118">Obsahuje třídy šifrování, která má mapování na popisného názvu do  **\<nameEntry >** element.</span><span class="sxs-lookup"><span data-stu-id="7193a-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7193a-119">**\<cryptographySettings –**></span><span class="sxs-lookup"><span data-stu-id="7193a-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="7193a-120">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="7193a-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="7193a-121">**\<cryptoNameMapping –**></span><span class="sxs-lookup"><span data-stu-id="7193a-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="7193a-122">Obsahuje mapování třídy popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="7193a-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="7193a-123">**\<mscorlib >** element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="7193a-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="7193a-124">Obsahuje  **\<cryptographySettings – >** element.</span><span class="sxs-lookup"><span data-stu-id="7193a-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="7193a-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="7193a-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="7193a-126">Mapuje název třídy algoritmus popisný název, který umožňuje jednu třídu k mít mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="7193a-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="7193a-127">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="7193a-128">Mapuje ASN.1 identifikátor objektu (OID) popisný název.</span><span class="sxs-lookup"><span data-stu-id="7193a-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="7193a-129">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="7193a-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="7193a-130">Obsahuje ASN.1 OID mapování třídy.</span><span class="sxs-lookup"><span data-stu-id="7193a-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7193a-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7193a-131">See Also</span></span>  
 [<span data-ttu-id="7193a-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7193a-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7193a-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="7193a-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
