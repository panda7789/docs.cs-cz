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
ms.openlocfilehash: c4ee8833578b082f25c427b13d77072d1954197f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="f6acc-102">&lt;Typ claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="f6acc-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="f6acc-103">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f6acc-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="f6acc-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="f6acc-104">\<system.identityModel></span></span>  
<span data-ttu-id="f6acc-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f6acc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f6acc-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="f6acc-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="f6acc-107">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="f6acc-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6acc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6acc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6acc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6acc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f6acc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6acc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6acc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6acc-111">Attributes</span></span>  
  
|<span data-ttu-id="f6acc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6acc-112">Attribute</span></span>|<span data-ttu-id="f6acc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f6acc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6acc-114">– typ</span><span class="sxs-lookup"><span data-stu-id="f6acc-114">type</span></span>|<span data-ttu-id="f6acc-115">Typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="f6acc-115">The claim type.</span></span> <span data-ttu-id="f6acc-116">Obvykle identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="f6acc-116">Typically a URI.</span></span> <span data-ttu-id="f6acc-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f6acc-117">Required.</span></span>|  
|<span data-ttu-id="f6acc-118">optional</span><span class="sxs-lookup"><span data-stu-id="f6acc-118">optional</span></span>|<span data-ttu-id="f6acc-119">Logická hodnota, která určuje, jestli je typ deklarace volitelné.</span><span class="sxs-lookup"><span data-stu-id="f6acc-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="f6acc-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f6acc-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6acc-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6acc-121">Child Elements</span></span>  
 <span data-ttu-id="f6acc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6acc-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6acc-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6acc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f6acc-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6acc-124">Element</span></span>|<span data-ttu-id="f6acc-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f6acc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6acc-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="f6acc-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="f6acc-127">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f6acc-127">Specifies the set of required claims for incoming security tokens.</span></span>|
