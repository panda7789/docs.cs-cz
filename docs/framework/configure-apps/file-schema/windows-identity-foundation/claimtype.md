---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942884"
---
# <a name="claimtype"></a><span data-ttu-id="e67cc-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="e67cc-101">\<claimType></span></span>
<span data-ttu-id="e67cc-102">Určuje jednu volitelnou nebo požadovanou deklaraci příchozích tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e67cc-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="e67cc-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e67cc-103">\<system.identityModel></span></span>  
<span data-ttu-id="e67cc-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e67cc-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e67cc-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="e67cc-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="e67cc-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="e67cc-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e67cc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e67cc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e67cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e67cc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e67cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e67cc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e67cc-110">Attributes</span></span>  
  
|<span data-ttu-id="e67cc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e67cc-111">Attribute</span></span>|<span data-ttu-id="e67cc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e67cc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e67cc-113">– typ</span><span class="sxs-lookup"><span data-stu-id="e67cc-113">type</span></span>|<span data-ttu-id="e67cc-114">Typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e67cc-114">The claim type.</span></span> <span data-ttu-id="e67cc-115">Obvykle je identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="e67cc-115">Typically a URI.</span></span> <span data-ttu-id="e67cc-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e67cc-116">Required.</span></span>|  
|<span data-ttu-id="e67cc-117">optional</span><span class="sxs-lookup"><span data-stu-id="e67cc-117">optional</span></span>|<span data-ttu-id="e67cc-118">Logická hodnota, která určuje, zda je typ deklarace je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="e67cc-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="e67cc-119">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="e67cc-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e67cc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e67cc-120">Child Elements</span></span>  
 <span data-ttu-id="e67cc-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="e67cc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e67cc-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e67cc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e67cc-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="e67cc-123">Element</span></span>|<span data-ttu-id="e67cc-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e67cc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e67cc-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="e67cc-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="e67cc-126">Určuje sadu požadovaných deklarací pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e67cc-126">Specifies the set of required claims for incoming security tokens.</span></span>|
