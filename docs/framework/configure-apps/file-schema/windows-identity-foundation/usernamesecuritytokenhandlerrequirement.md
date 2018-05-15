---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d725cc0d16457f2bdfb404baf4758e3431ce6b7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="493a3-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="493a3-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="493a3-103">Obsahuje konfiguraci <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="493a3-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="493a3-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="493a3-104">\<system.identityModel></span></span>  
<span data-ttu-id="493a3-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="493a3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="493a3-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="493a3-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="493a3-107">\<add></span><span class="sxs-lookup"><span data-stu-id="493a3-107">\<add></span></span>  
<span data-ttu-id="493a3-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="493a3-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493a3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="493a3-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="493a3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="493a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="493a3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="493a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="493a3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="493a3-112">Attributes</span></span>  
  
|<span data-ttu-id="493a3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="493a3-113">Attribute</span></span>|<span data-ttu-id="493a3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="493a3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="493a3-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="493a3-115">membershipProviderName</span></span>|<span data-ttu-id="493a3-116">Určuje, <xref:System.Web.Security.MembershipProvider> který má být používána obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="493a3-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="493a3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="493a3-117">Child Elements</span></span>  
 <span data-ttu-id="493a3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="493a3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="493a3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="493a3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="493a3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="493a3-120">Element</span></span>|<span data-ttu-id="493a3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="493a3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="493a3-122">\<add></span><span class="sxs-lookup"><span data-stu-id="493a3-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="493a3-123">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="493a3-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="493a3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="493a3-124">Remarks</span></span>  
 <span data-ttu-id="493a3-125">`<userNameSecurityTokenHandlerRequirement>` Nastaví element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> vlastnost při <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="493a3-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="493a3-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="493a3-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
