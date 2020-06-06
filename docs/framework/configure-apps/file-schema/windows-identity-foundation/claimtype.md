---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252073"
---
# \<claimType>
<span data-ttu-id="4c1ed-101">Určuje jednu volitelnou nebo požadovanou deklaraci příchozích tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="4c1ed-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c1ed-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c1ed-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c1ed-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4c1ed-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c1ed-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c1ed-105">Attributes</span></span>  
  
|<span data-ttu-id="4c1ed-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c1ed-106">Attribute</span></span>|<span data-ttu-id="4c1ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4c1ed-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c1ed-108">typ</span><span class="sxs-lookup"><span data-stu-id="4c1ed-108">type</span></span>|<span data-ttu-id="4c1ed-109">Typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-109">The claim type.</span></span> <span data-ttu-id="4c1ed-110">Obvykle je identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-110">Typically a URI.</span></span> <span data-ttu-id="4c1ed-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-111">Required.</span></span>|  
|<span data-ttu-id="4c1ed-112">optional</span><span class="sxs-lookup"><span data-stu-id="4c1ed-112">optional</span></span>|<span data-ttu-id="4c1ed-113">Logická hodnota, která určuje, zda je typ deklarace je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="4c1ed-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c1ed-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c1ed-115">Child Elements</span></span>  
 <span data-ttu-id="4c1ed-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c1ed-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c1ed-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c1ed-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4c1ed-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c1ed-118">Element</span></span>|<span data-ttu-id="4c1ed-119">Description</span><span class="sxs-lookup"><span data-stu-id="4c1ed-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="4c1ed-120">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c1ed-120">Specifies the set of required claims for incoming security tokens.</span></span>|
