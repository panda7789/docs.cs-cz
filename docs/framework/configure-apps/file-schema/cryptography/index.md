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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087997"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="42dcb-102">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="42dcb-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="42dcb-103">Schéma nastavení kryptografie obsahuje prvky, které určují způsob mapování popisných názvů algoritmů na třídy, které implementují algoritmy kryptografie.</span><span class="sxs-lookup"><span data-stu-id="42dcb-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="42dcb-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="42dcb-104">Element</span></span>|<span data-ttu-id="42dcb-105">Description</span><span class="sxs-lookup"><span data-stu-id="42dcb-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="42dcb-106">Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v **\<nameEntry>** elementu.</span><span class="sxs-lookup"><span data-stu-id="42dcb-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="42dcb-107">Obsahuje třídu kryptografie, která má mapování na popisný název v **\<nameEntry>** elementu.</span><span class="sxs-lookup"><span data-stu-id="42dcb-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="42dcb-108">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="42dcb-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="42dcb-109">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="42dcb-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="42dcb-110">**\<mscorlib>**– element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="42dcb-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="42dcb-111">Obsahuje **\<cryptographySettings>** element.</span><span class="sxs-lookup"><span data-stu-id="42dcb-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="42dcb-112">Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.</span><span class="sxs-lookup"><span data-stu-id="42dcb-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="42dcb-113">Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.</span><span class="sxs-lookup"><span data-stu-id="42dcb-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="42dcb-114">Obsahuje mapování ID ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="42dcb-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42dcb-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="42dcb-115">See also</span></span>

- [<span data-ttu-id="42dcb-116">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="42dcb-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="42dcb-117">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="42dcb-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
