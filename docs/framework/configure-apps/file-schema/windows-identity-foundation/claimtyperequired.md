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
ms.openlocfilehash: 89d42cba78eb9758d8b3491fd1bd3b25ef168f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="f6af9-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="f6af9-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="f6af9-103">Určuje sadu požadované deklarací identity pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f6af9-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="f6af9-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="f6af9-104">\<system.identityModel></span></span>  
<span data-ttu-id="f6af9-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f6af9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f6af9-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="f6af9-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6af9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6af9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6af9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6af9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f6af9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6af9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6af9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6af9-110">Attributes</span></span>  
 <span data-ttu-id="f6af9-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6af9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f6af9-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6af9-112">Child Elements</span></span>  
  
|<span data-ttu-id="f6af9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6af9-113">Element</span></span>|<span data-ttu-id="f6af9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f6af9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6af9-115">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="f6af9-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="f6af9-116">Určuje jedno volitelné nebo požadované pravidlo pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f6af9-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6af9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6af9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f6af9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6af9-118">Element</span></span>|<span data-ttu-id="f6af9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f6af9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6af9-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f6af9-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="f6af9-121">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="f6af9-121">Specifies service-level identity settings.</span></span>|
