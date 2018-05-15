---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6fb600aac46b3ee5cb54fa904d35ac7b7ed90719
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="7a0da-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="7a0da-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="7a0da-103">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7a0da-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="7a0da-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7a0da-104">\<system.identityModel></span></span>  
<span data-ttu-id="7a0da-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7a0da-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7a0da-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="7a0da-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0da-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a0da-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a0da-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7a0da-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a0da-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7a0da-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a0da-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7a0da-110">Attributes</span></span>  
 <span data-ttu-id="7a0da-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="7a0da-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a0da-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7a0da-112">Child Elements</span></span>  
  
|<span data-ttu-id="7a0da-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a0da-113">Element</span></span>|<span data-ttu-id="7a0da-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7a0da-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a0da-115">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="7a0da-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="7a0da-116">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7a0da-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a0da-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7a0da-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7a0da-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a0da-118">Element</span></span>|<span data-ttu-id="7a0da-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7a0da-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a0da-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7a0da-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="7a0da-121">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="7a0da-121">Specifies service-level identity settings.</span></span>|
