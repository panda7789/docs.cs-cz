---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: eafaf253e27db632f17acfce4445a07d18b109aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778453"
---
# <a name="claimtyperequired"></a><span data-ttu-id="40747-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="40747-101">\<claimTypeRequired></span></span>
<span data-ttu-id="40747-102">Určuje sadu požadované deklarace identit pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40747-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="40747-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="40747-103">\<system.identityModel></span></span>  
<span data-ttu-id="40747-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="40747-104">\<identityConfiguration></span></span>  
<span data-ttu-id="40747-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="40747-105">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40747-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40747-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40747-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40747-107">Attributes and Elements</span></span>  
 <span data-ttu-id="40747-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40747-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40747-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="40747-109">Attributes</span></span>  
 <span data-ttu-id="40747-110">Žádný</span><span class="sxs-lookup"><span data-stu-id="40747-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40747-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40747-111">Child Elements</span></span>  
  
|<span data-ttu-id="40747-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="40747-112">Element</span></span>|<span data-ttu-id="40747-113">Popis</span><span class="sxs-lookup"><span data-stu-id="40747-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40747-114">\<claimType></span><span class="sxs-lookup"><span data-stu-id="40747-114">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="40747-115">Určuje jednu deklaraci nepovinné nebo povinné pro příchozí tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40747-115">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40747-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40747-116">Parent Elements</span></span>  
  
|<span data-ttu-id="40747-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="40747-117">Element</span></span>|<span data-ttu-id="40747-118">Popis</span><span class="sxs-lookup"><span data-stu-id="40747-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40747-119">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="40747-119">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="40747-120">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="40747-120">Specifies service-level identity settings.</span></span>|
