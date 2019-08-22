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
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664299"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="dfa1d-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="dfa1d-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="dfa1d-103">Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="dfa1d-104"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="dfa1d-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="dfa1d-105"> **\<mscorlib>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="dfa1d-106"> **\<cryptographySettings >** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="dfa1d-107"> **\<cryptoNameMapping>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="dfa1d-108"> **\<cryptoClasses>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="dfa1d-109"> **\<cryptoClass>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="dfa1d-110"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="dfa1d-111"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="dfa1d-112"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="dfa1d-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="dfa1d-113">Element</span></span>|<span data-ttu-id="dfa1d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dfa1d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfa1d-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="dfa1d-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="dfa1d-116">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v  **\<elementu nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="dfa1d-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="dfa1d-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="dfa1d-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="dfa1d-118">Obsahuje třídu kryptografie, která má mapování na popisný název v  **\<elementu nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="dfa1d-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="dfa1d-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="dfa1d-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="dfa1d-120">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="dfa1d-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="dfa1d-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="dfa1d-122">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="dfa1d-123">element > mscorlib pro nastavení kryptografie  **\<** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="dfa1d-124">Obsahuje element cryptographySettings >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="dfa1d-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="dfa1d-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="dfa1d-126">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="dfa1d-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="dfa1d-128">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="dfa1d-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="dfa1d-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="dfa1d-130">Obsahuje mapování ID ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfa1d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfa1d-131">See also</span></span>

- [<span data-ttu-id="dfa1d-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="dfa1d-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dfa1d-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="dfa1d-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
