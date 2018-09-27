---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236884"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="78492-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="78492-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="78492-103">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="78492-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="78492-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="78492-104">\<system.identityModel></span></span>  
<span data-ttu-id="78492-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="78492-105">\<identityConfiguration></span></span>  
<span data-ttu-id="78492-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="78492-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="78492-107">\<add></span><span class="sxs-lookup"><span data-stu-id="78492-107">\<add></span></span>  
<span data-ttu-id="78492-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="78492-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78492-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78492-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78492-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78492-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78492-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78492-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78492-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="78492-112">Attributes</span></span>  
  
|<span data-ttu-id="78492-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="78492-113">Attribute</span></span>|<span data-ttu-id="78492-114">Popis</span><span class="sxs-lookup"><span data-stu-id="78492-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78492-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="78492-115">lifetime</span></span>|<span data-ttu-id="78492-116">Určuje životnost relace tokenů.</span><span class="sxs-lookup"><span data-stu-id="78492-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78492-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78492-117">Child Elements</span></span>  
 <span data-ttu-id="78492-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="78492-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78492-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78492-119">Parent Elements</span></span>  
  
|<span data-ttu-id="78492-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="78492-120">Element</span></span>|<span data-ttu-id="78492-121">Popis</span><span class="sxs-lookup"><span data-stu-id="78492-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78492-122">\<add></span><span class="sxs-lookup"><span data-stu-id="78492-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="78492-123">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="78492-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78492-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="78492-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
