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
ms.openlocfilehash: 8b729f588d2195992b231661f7bb718240141fdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="cafd3-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="cafd3-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="cafd3-103">Obsahuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="cafd3-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="cafd3-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="cafd3-104">\<system.identityModel></span></span>  
<span data-ttu-id="cafd3-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cafd3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cafd3-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="cafd3-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cafd3-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="cafd3-107">\<add></span></span>  
<span data-ttu-id="cafd3-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="cafd3-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cafd3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cafd3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cafd3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cafd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cafd3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cafd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cafd3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cafd3-112">Attributes</span></span>  
  
|<span data-ttu-id="cafd3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cafd3-113">Attribute</span></span>|<span data-ttu-id="cafd3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cafd3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cafd3-115">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="cafd3-115">lifetime</span></span>|<span data-ttu-id="cafd3-116">Určuje životnost tokenů relace.</span><span class="sxs-lookup"><span data-stu-id="cafd3-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cafd3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cafd3-117">Child Elements</span></span>  
 <span data-ttu-id="cafd3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="cafd3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cafd3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cafd3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cafd3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="cafd3-120">Element</span></span>|<span data-ttu-id="cafd3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="cafd3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cafd3-122">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="cafd3-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="cafd3-123">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="cafd3-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cafd3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="cafd3-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
