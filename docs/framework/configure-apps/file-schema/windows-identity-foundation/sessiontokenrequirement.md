---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="ff7a2-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="ff7a2-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="ff7a2-103">Obsahuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ff7a2-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="ff7a2-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-104">\<system.identityModel></span></span>  
<span data-ttu-id="ff7a2-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ff7a2-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ff7a2-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-107">\<add></span></span>  
<span data-ttu-id="ff7a2-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7a2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff7a2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff7a2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff7a2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff7a2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff7a2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff7a2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff7a2-112">Attributes</span></span>  
  
|<span data-ttu-id="ff7a2-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ff7a2-113">Attribute</span></span>|<span data-ttu-id="ff7a2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ff7a2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff7a2-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="ff7a2-115">lifetime</span></span>|<span data-ttu-id="ff7a2-116">Určuje životnost tokenů relace.</span><span class="sxs-lookup"><span data-stu-id="ff7a2-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff7a2-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ff7a2-117">Child Elements</span></span>  
 <span data-ttu-id="ff7a2-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ff7a2-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff7a2-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ff7a2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ff7a2-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff7a2-120">Element</span></span>|<span data-ttu-id="ff7a2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ff7a2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff7a2-122">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="ff7a2-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="ff7a2-123">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="ff7a2-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff7a2-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff7a2-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
