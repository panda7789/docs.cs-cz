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
ms.openlocfilehash: 3cd3ed8ab5005116971a79ad04d249ff14637f08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577081"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="b12b3-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b12b3-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="b12b3-103">Schéma nastavení šifrování obsahuje elementy, které určují způsob mapování popisné názvy algoritmů tříd, které implementují algoritmy šifrování.</span><span class="sxs-lookup"><span data-stu-id="b12b3-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="b12b3-104">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="b12b3-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="b12b3-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="b12b3-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="b12b3-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="b12b3-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="b12b3-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="b12b3-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="b12b3-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="b12b3-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="b12b3-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="b12b3-113">Element</span></span>|<span data-ttu-id="b12b3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b12b3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b12b3-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="b12b3-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="b12b3-116">Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b12b3-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b12b3-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="b12b3-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="b12b3-118">Obsahuje kryptografickou třídu, která nemá mapování na popisný název v  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b12b3-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b12b3-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="b12b3-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="b12b3-120">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="b12b3-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="b12b3-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="b12b3-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="b12b3-122">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="b12b3-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b12b3-123">**\<mscorlib >** – element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="b12b3-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="b12b3-124">Obsahuje  **\<cryptographySettings – >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b12b3-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="b12b3-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="b12b3-126">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="b12b3-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="b12b3-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="b12b3-128">Identifikátor objektu (OID) ASN.1 se mapuje na popisný název.</span><span class="sxs-lookup"><span data-stu-id="b12b3-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="b12b3-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="b12b3-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="b12b3-130">Obsahuje mapování ASN.1 OID pro třídy.</span><span class="sxs-lookup"><span data-stu-id="b12b3-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b12b3-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b12b3-131">See also</span></span>
- [<span data-ttu-id="b12b3-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b12b3-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b12b3-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b12b3-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
