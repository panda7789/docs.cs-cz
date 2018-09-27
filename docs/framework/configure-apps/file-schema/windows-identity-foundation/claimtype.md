---
title: '&lt;Typ ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47234955"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="f1908-102">&lt;Typ ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="f1908-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="f1908-103">Určuje jednu deklaraci nepovinné nebo povinné pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f1908-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="f1908-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f1908-104">\<system.identityModel></span></span>  
<span data-ttu-id="f1908-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f1908-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f1908-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="f1908-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="f1908-107">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="f1908-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1908-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1908-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1908-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1908-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1908-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1908-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1908-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1908-111">Attributes</span></span>  
  
|<span data-ttu-id="f1908-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1908-112">Attribute</span></span>|<span data-ttu-id="f1908-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f1908-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1908-114">– typ</span><span class="sxs-lookup"><span data-stu-id="f1908-114">type</span></span>|<span data-ttu-id="f1908-115">Typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="f1908-115">The claim type.</span></span> <span data-ttu-id="f1908-116">Obvykle identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="f1908-116">Typically a URI.</span></span> <span data-ttu-id="f1908-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f1908-117">Required.</span></span>|  
|<span data-ttu-id="f1908-118">optional</span><span class="sxs-lookup"><span data-stu-id="f1908-118">optional</span></span>|<span data-ttu-id="f1908-119">Logická hodnota určující, zda je typ deklarace identity volitelné.</span><span class="sxs-lookup"><span data-stu-id="f1908-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="f1908-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f1908-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1908-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1908-121">Child Elements</span></span>  
 <span data-ttu-id="f1908-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1908-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1908-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1908-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f1908-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1908-124">Element</span></span>|<span data-ttu-id="f1908-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f1908-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1908-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="f1908-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="f1908-127">Určuje sadu požadované deklarace identit pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f1908-127">Specifies the set of required claims for incoming security tokens.</span></span>|
