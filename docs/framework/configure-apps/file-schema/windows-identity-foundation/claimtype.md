---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 6bc185572528d4229ee53f1421eaa5bf27b053e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267232"
---
# <a name="claimtype"></a><span data-ttu-id="3e241-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="3e241-101">\<claimType></span></span>
<span data-ttu-id="3e241-102">Určuje jednu deklaraci nepovinné nebo povinné pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e241-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="3e241-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3e241-103">\<system.identityModel></span></span>  
<span data-ttu-id="3e241-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3e241-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3e241-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="3e241-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="3e241-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="3e241-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e241-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e241-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e241-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3e241-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e241-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3e241-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e241-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3e241-110">Attributes</span></span>  
  
|<span data-ttu-id="3e241-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3e241-111">Attribute</span></span>|<span data-ttu-id="3e241-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3e241-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e241-113">– typ</span><span class="sxs-lookup"><span data-stu-id="3e241-113">type</span></span>|<span data-ttu-id="3e241-114">Typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="3e241-114">The claim type.</span></span> <span data-ttu-id="3e241-115">Obvykle identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="3e241-115">Typically a URI.</span></span> <span data-ttu-id="3e241-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3e241-116">Required.</span></span>|  
|<span data-ttu-id="3e241-117">optional</span><span class="sxs-lookup"><span data-stu-id="3e241-117">optional</span></span>|<span data-ttu-id="3e241-118">Logická hodnota určující, zda je typ deklarace identity volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e241-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="3e241-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e241-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e241-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3e241-120">Child Elements</span></span>  
 <span data-ttu-id="3e241-121">Žádná</span><span class="sxs-lookup"><span data-stu-id="3e241-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e241-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3e241-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3e241-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="3e241-123">Element</span></span>|<span data-ttu-id="3e241-124">Popis</span><span class="sxs-lookup"><span data-stu-id="3e241-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e241-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="3e241-125">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="3e241-126">Určuje sadu požadované deklarace identit pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e241-126">Specifies the set of required claims for incoming security tokens.</span></span>|
