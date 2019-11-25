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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087997"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="79d94-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="79d94-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="79d94-103">Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.</span><span class="sxs-lookup"><span data-stu-id="79d94-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
<span data-ttu-id="79d94-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="79d94-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="79d94-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="79d94-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="79d94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="79d94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="79d94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>\
<span data-ttu-id="79d94-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>\
<span data-ttu-id="79d94-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="79d94-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d94-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>

|<span data-ttu-id="79d94-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="79d94-113">Element</span></span>|<span data-ttu-id="79d94-114">Popis</span><span class="sxs-lookup"><span data-stu-id="79d94-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d94-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="79d94-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="79d94-116">Obsahuje seznam tříd kryptografie, které mají mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="79d94-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="79d94-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="79d94-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="79d94-118">Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="79d94-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="79d94-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="79d94-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="79d94-120">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="79d94-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="79d94-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="79d94-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="79d94-122">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="79d94-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="79d94-123"> **\<element > mscorlib** pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="79d94-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="79d94-124">Obsahuje prvek **\<cryptographySettings >** .</span><span class="sxs-lookup"><span data-stu-id="79d94-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="79d94-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="79d94-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="79d94-126">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="79d94-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="79d94-127"> **\<oidEntry >** </span><span class="sxs-lookup"><span data-stu-id="79d94-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="79d94-128">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="79d94-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="79d94-129"> **\<oidMap >** </span><span class="sxs-lookup"><span data-stu-id="79d94-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="79d94-130">Obsahuje mapování ID ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="79d94-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79d94-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79d94-131">See also</span></span>

- [<span data-ttu-id="79d94-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="79d94-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="79d94-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="79d94-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
