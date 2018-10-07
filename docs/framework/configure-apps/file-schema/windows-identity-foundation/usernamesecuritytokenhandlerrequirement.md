---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: dfcaad8b150321fda2a86e601bf57204cbdc1a0e
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844231"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="14080-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="14080-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="14080-103">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="14080-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="14080-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="14080-104">\<system.identityModel></span></span>  
<span data-ttu-id="14080-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="14080-105">\<identityConfiguration></span></span>  
<span data-ttu-id="14080-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="14080-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="14080-107">\<add></span><span class="sxs-lookup"><span data-stu-id="14080-107">\<add></span></span>  
<span data-ttu-id="14080-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="14080-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14080-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14080-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14080-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14080-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14080-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14080-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14080-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="14080-112">Attributes</span></span>  
  
|<span data-ttu-id="14080-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="14080-113">Attribute</span></span>|<span data-ttu-id="14080-114">Popis</span><span class="sxs-lookup"><span data-stu-id="14080-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14080-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="14080-115">membershipProviderName</span></span>|<span data-ttu-id="14080-116">Určuje, <xref:System.Web.Security.MembershipProvider> , který by měly být používány obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="14080-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14080-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14080-117">Child Elements</span></span>  
 <span data-ttu-id="14080-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="14080-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14080-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14080-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14080-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="14080-120">Element</span></span>|<span data-ttu-id="14080-121">Popis</span><span class="sxs-lookup"><span data-stu-id="14080-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14080-122">\<add></span><span class="sxs-lookup"><span data-stu-id="14080-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="14080-123">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="14080-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14080-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14080-124">Remarks</span></span>  
 <span data-ttu-id="14080-125">`<userNameSecurityTokenHandlerRequirement>` Nastaví element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> vlastnost při <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="14080-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14080-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="14080-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
