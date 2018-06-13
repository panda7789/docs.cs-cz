---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6c40948633eaf892db06e9bba756158dfc3c4a2e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754987"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="1310e-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="1310e-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="1310e-103">Obsahuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1310e-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="1310e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1310e-104">\<system.identityModel></span></span>  
<span data-ttu-id="1310e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1310e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1310e-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1310e-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1310e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="1310e-107">\<add></span></span>  
<span data-ttu-id="1310e-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="1310e-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1310e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1310e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1310e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1310e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1310e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1310e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1310e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1310e-112">Attributes</span></span>  
  
|<span data-ttu-id="1310e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1310e-113">Attribute</span></span>|<span data-ttu-id="1310e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1310e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1310e-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="1310e-115">lifetime</span></span>|<span data-ttu-id="1310e-116">Určuje životnost tokenů relace.</span><span class="sxs-lookup"><span data-stu-id="1310e-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1310e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1310e-117">Child Elements</span></span>  
 <span data-ttu-id="1310e-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1310e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1310e-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1310e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1310e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1310e-120">Element</span></span>|<span data-ttu-id="1310e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1310e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1310e-122">\<add></span><span class="sxs-lookup"><span data-stu-id="1310e-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="1310e-123">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="1310e-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1310e-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="1310e-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
