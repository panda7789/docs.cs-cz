---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="2dd0c-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="2dd0c-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="2dd0c-103">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="2dd0c-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="2dd0c-104">\<system.identityModel></span></span>  
<span data-ttu-id="2dd0c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2dd0c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2dd0c-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="2dd0c-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd0c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dd0c-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dd0c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2dd0c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dd0c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-110">Attributes</span></span>  
 <span data-ttu-id="2dd0c-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="2dd0c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2dd0c-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-112">Child Elements</span></span>  
  
|<span data-ttu-id="2dd0c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="2dd0c-113">Element</span></span>|<span data-ttu-id="2dd0c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2dd0c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2dd0c-115">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="2dd0c-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="2dd0c-116">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2dd0c-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2dd0c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2dd0c-118">Element</span></span>|<span data-ttu-id="2dd0c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2dd0c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2dd0c-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2dd0c-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="2dd0c-121">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-121">Specifies service-level identity settings.</span></span>|
