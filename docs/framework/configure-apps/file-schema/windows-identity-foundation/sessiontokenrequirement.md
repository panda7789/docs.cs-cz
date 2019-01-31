---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271899"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="ea131-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ea131-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="ea131-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ea131-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="ea131-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ea131-103">\<system.identityModel></span></span>  
<span data-ttu-id="ea131-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ea131-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ea131-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ea131-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ea131-106">\<add></span><span class="sxs-lookup"><span data-stu-id="ea131-106">\<add></span></span>  
<span data-ttu-id="ea131-107">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ea131-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea131-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea131-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea131-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ea131-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea131-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ea131-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea131-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ea131-111">Attributes</span></span>  
  
|<span data-ttu-id="ea131-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ea131-112">Attribute</span></span>|<span data-ttu-id="ea131-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ea131-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea131-114">doba platnosti</span><span class="sxs-lookup"><span data-stu-id="ea131-114">lifetime</span></span>|<span data-ttu-id="ea131-115">Určuje životnost relace tokenů.</span><span class="sxs-lookup"><span data-stu-id="ea131-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea131-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ea131-116">Child Elements</span></span>  
 <span data-ttu-id="ea131-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="ea131-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea131-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ea131-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ea131-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea131-119">Element</span></span>|<span data-ttu-id="ea131-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ea131-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea131-121">\<add></span><span class="sxs-lookup"><span data-stu-id="ea131-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="ea131-122">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="ea131-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ea131-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea131-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
