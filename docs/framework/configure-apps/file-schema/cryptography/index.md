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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699806"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="4cac1-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="4cac1-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="4cac1-103">Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.</span><span class="sxs-lookup"><span data-stu-id="4cac1-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[<span data-ttu-id="4cac1-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="4cac1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4cac1-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="4cac1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="4cac1-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="4cac1-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="4cac1-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>  
<span data-ttu-id="4cac1-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>  
<span data-ttu-id="4cac1-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="4cac1-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="4cac1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>  
  
|<span data-ttu-id="4cac1-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="4cac1-113">Element</span></span>|<span data-ttu-id="4cac1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4cac1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cac1-115"> **@no__t – 2cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="4cac1-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="4cac1-116">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="4cac1-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="4cac1-117"> **@no__t – 2cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="4cac1-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="4cac1-118">Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="4cac1-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="4cac1-119"> **@no__t – 2cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="4cac1-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="4cac1-120">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="4cac1-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="4cac1-121"> **@no__t – 2cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="4cac1-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="4cac1-122">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="4cac1-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="4cac1-123"> **@no__t – element > 2mscorlib** pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="4cac1-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="4cac1-124">Obsahuje prvek **> \<cryptographySettings** .</span><span class="sxs-lookup"><span data-stu-id="4cac1-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="4cac1-125"> **@no__t – 2nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="4cac1-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="4cac1-126">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="4cac1-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="4cac1-127"> **@no__t – 2oidEntry >** </span><span class="sxs-lookup"><span data-stu-id="4cac1-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="4cac1-128">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="4cac1-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="4cac1-129"> **@no__t – 2oidMap >** </span><span class="sxs-lookup"><span data-stu-id="4cac1-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="4cac1-130">Obsahuje mapování ID ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="4cac1-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cac1-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cac1-131">See also</span></span>

- [<span data-ttu-id="4cac1-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4cac1-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4cac1-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="4cac1-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
