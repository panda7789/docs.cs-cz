---
title: '&lt;Typ claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="86990-102">&lt;Typ claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="86990-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="86990-103">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="86990-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="86990-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="86990-104">\<system.identityModel></span></span>  
<span data-ttu-id="86990-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="86990-105">\<identityConfiguration></span></span>  
<span data-ttu-id="86990-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="86990-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="86990-107">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="86990-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86990-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86990-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86990-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86990-109">Attributes and Elements</span></span>  
 <span data-ttu-id="86990-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86990-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86990-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="86990-111">Attributes</span></span>  
  
|<span data-ttu-id="86990-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="86990-112">Attribute</span></span>|<span data-ttu-id="86990-113">Popis</span><span class="sxs-lookup"><span data-stu-id="86990-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86990-114">– typ</span><span class="sxs-lookup"><span data-stu-id="86990-114">type</span></span>|<span data-ttu-id="86990-115">Typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="86990-115">The claim type.</span></span> <span data-ttu-id="86990-116">Obvykle identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="86990-116">Typically a URI.</span></span> <span data-ttu-id="86990-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="86990-117">Required.</span></span>|  
|<span data-ttu-id="86990-118">optional</span><span class="sxs-lookup"><span data-stu-id="86990-118">optional</span></span>|<span data-ttu-id="86990-119">Logická hodnota, která určuje, jestli je typ deklarace volitelné.</span><span class="sxs-lookup"><span data-stu-id="86990-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="86990-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="86990-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86990-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86990-121">Child Elements</span></span>  
 <span data-ttu-id="86990-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="86990-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86990-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86990-123">Parent Elements</span></span>  
  
|<span data-ttu-id="86990-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="86990-124">Element</span></span>|<span data-ttu-id="86990-125">Popis</span><span class="sxs-lookup"><span data-stu-id="86990-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86990-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="86990-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="86990-127">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="86990-127">Specifies the set of required claims for incoming security tokens.</span></span>|
