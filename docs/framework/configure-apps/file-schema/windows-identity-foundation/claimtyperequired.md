---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: df4494de6b76943849db2bedef8f43ad894b6bd1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084225"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="61666-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="61666-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="61666-103">Určuje sadu požadované deklarace identit pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61666-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="61666-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="61666-104">\<system.identityModel></span></span>  
<span data-ttu-id="61666-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="61666-105">\<identityConfiguration></span></span>  
<span data-ttu-id="61666-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="61666-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61666-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61666-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61666-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61666-108">Attributes and Elements</span></span>  
 <span data-ttu-id="61666-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61666-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61666-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="61666-110">Attributes</span></span>  
 <span data-ttu-id="61666-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="61666-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61666-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61666-112">Child Elements</span></span>  
  
|<span data-ttu-id="61666-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="61666-113">Element</span></span>|<span data-ttu-id="61666-114">Popis</span><span class="sxs-lookup"><span data-stu-id="61666-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61666-115">\<Typ claimType ></span><span class="sxs-lookup"><span data-stu-id="61666-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="61666-116">Určuje jednu deklaraci nepovinné nebo povinné pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61666-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61666-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61666-117">Parent Elements</span></span>  
  
|<span data-ttu-id="61666-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="61666-118">Element</span></span>|<span data-ttu-id="61666-119">Popis</span><span class="sxs-lookup"><span data-stu-id="61666-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61666-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="61666-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="61666-121">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="61666-121">Specifies service-level identity settings.</span></span>|
