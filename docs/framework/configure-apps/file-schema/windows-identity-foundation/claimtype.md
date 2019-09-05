---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252073"
---
# <a name="claimtype"></a><span data-ttu-id="6b86e-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="6b86e-101">\<claimType></span></span>
<span data-ttu-id="6b86e-102">Určuje jednu volitelnou nebo požadovanou deklaraci příchozích tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b86e-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="6b86e-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b86e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b86e-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b86e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="6b86e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="6b86e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="6b86e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequired >** ](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="6b86e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="6b86e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> deklarace identity**</span><span class="sxs-lookup"><span data-stu-id="6b86e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b86e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b86e-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b86e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b86e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6b86e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b86e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b86e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b86e-111">Attributes</span></span>  
  
|<span data-ttu-id="6b86e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b86e-112">Attribute</span></span>|<span data-ttu-id="6b86e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6b86e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b86e-114">– typ</span><span class="sxs-lookup"><span data-stu-id="6b86e-114">type</span></span>|<span data-ttu-id="6b86e-115">Typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6b86e-115">The claim type.</span></span> <span data-ttu-id="6b86e-116">Obvykle je identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="6b86e-116">Typically a URI.</span></span> <span data-ttu-id="6b86e-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6b86e-117">Required.</span></span>|  
|<span data-ttu-id="6b86e-118">optional</span><span class="sxs-lookup"><span data-stu-id="6b86e-118">optional</span></span>|<span data-ttu-id="6b86e-119">Logická hodnota, která určuje, zda je typ deklarace je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="6b86e-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="6b86e-120">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="6b86e-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b86e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b86e-121">Child Elements</span></span>  
 <span data-ttu-id="6b86e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="6b86e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b86e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b86e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6b86e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b86e-124">Element</span></span>|<span data-ttu-id="6b86e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6b86e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b86e-126">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="6b86e-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="6b86e-127">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b86e-127">Specifies the set of required claims for incoming security tokens.</span></span>|
