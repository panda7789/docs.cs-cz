---
title: '&lt;Typ claimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="9071c-102">&lt;Typ claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="9071c-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="9071c-103">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9071c-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="9071c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9071c-104">\<system.identityModel></span></span>  
<span data-ttu-id="9071c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9071c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9071c-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9071c-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="9071c-107">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="9071c-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9071c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9071c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9071c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9071c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9071c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9071c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9071c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9071c-111">Attributes</span></span>  
  
|<span data-ttu-id="9071c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9071c-112">Attribute</span></span>|<span data-ttu-id="9071c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9071c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9071c-114">– typ</span><span class="sxs-lookup"><span data-stu-id="9071c-114">type</span></span>|<span data-ttu-id="9071c-115">Typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="9071c-115">The claim type.</span></span> <span data-ttu-id="9071c-116">Obvykle identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="9071c-116">Typically a URI.</span></span> <span data-ttu-id="9071c-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9071c-117">Required.</span></span>|  
|<span data-ttu-id="9071c-118">optional</span><span class="sxs-lookup"><span data-stu-id="9071c-118">optional</span></span>|<span data-ttu-id="9071c-119">Logická hodnota, která určuje, jestli je typ deklarace volitelné.</span><span class="sxs-lookup"><span data-stu-id="9071c-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="9071c-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9071c-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9071c-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9071c-121">Child Elements</span></span>  
 <span data-ttu-id="9071c-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="9071c-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9071c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9071c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9071c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="9071c-124">Element</span></span>|<span data-ttu-id="9071c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="9071c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9071c-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9071c-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="9071c-127">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9071c-127">Specifies the set of required claims for incoming security tokens.</span></span>|
