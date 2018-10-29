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
ms.openlocfilehash: 9bf94c28522d42e1a763726469cf9b1a03ccd86e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196749"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="cf217-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="cf217-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="cf217-103">Schéma nastavení šifrování obsahuje elementy, které určují způsob mapování popisné názvy algoritmů tříd, které implementují algoritmy šifrování.</span><span class="sxs-lookup"><span data-stu-id="cf217-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="cf217-104">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="cf217-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="cf217-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="cf217-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="cf217-106">**\<cryptographySettings – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="cf217-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="cf217-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="cf217-108">**\<cryptoClasses – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="cf217-109">**\<cryptoclass – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="cf217-110">**\<nameEntry – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="cf217-111">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="cf217-112">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="cf217-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf217-113">Element</span></span>|<span data-ttu-id="cf217-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cf217-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf217-115">**\<cryptoClasses –**></span><span class="sxs-lookup"><span data-stu-id="cf217-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="cf217-116">Obsahuje seznam šifrovacích tříd, které mají na popisný název v mapování  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf217-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="cf217-117">**\<cryptoclass –**></span><span class="sxs-lookup"><span data-stu-id="cf217-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="cf217-118">Obsahuje kryptografickou třídu, která nemá mapování na popisný název v  **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf217-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="cf217-119">**\<cryptographySettings –**></span><span class="sxs-lookup"><span data-stu-id="cf217-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="cf217-120">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="cf217-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="cf217-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="cf217-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="cf217-122">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="cf217-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="cf217-123">**\<mscorlib >** – element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="cf217-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="cf217-124">Obsahuje  **\<cryptographySettings – >** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf217-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="cf217-125">**\<nameEntry – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="cf217-126">Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="cf217-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="cf217-127">**\<oidentry – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="cf217-128">Identifikátor objektu (OID) ASN.1 se mapuje na popisný název.</span><span class="sxs-lookup"><span data-stu-id="cf217-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="cf217-129">**\<oidmap – >**</span><span class="sxs-lookup"><span data-stu-id="cf217-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="cf217-130">Obsahuje mapování ASN.1 OID pro třídy.</span><span class="sxs-lookup"><span data-stu-id="cf217-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf217-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf217-131">See Also</span></span>  
- [<span data-ttu-id="cf217-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cf217-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="cf217-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="cf217-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
