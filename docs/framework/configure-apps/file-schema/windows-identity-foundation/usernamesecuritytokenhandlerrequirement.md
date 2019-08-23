---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944256"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="48735-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="48735-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="48735-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="48735-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="48735-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="48735-103">\<system.identityModel></span></span>  
<span data-ttu-id="48735-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="48735-104">\<identityConfiguration></span></span>  
<span data-ttu-id="48735-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="48735-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="48735-106">\<add></span><span class="sxs-lookup"><span data-stu-id="48735-106">\<add></span></span>  
<span data-ttu-id="48735-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="48735-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48735-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48735-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48735-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48735-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48735-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48735-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48735-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="48735-111">Attributes</span></span>  
  
|<span data-ttu-id="48735-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="48735-112">Attribute</span></span>|<span data-ttu-id="48735-113">Popis</span><span class="sxs-lookup"><span data-stu-id="48735-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48735-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="48735-114">membershipProviderName</span></span>|<span data-ttu-id="48735-115"><xref:System.Web.Security.MembershipProvider> Určuje, které má obslužná rutina tokenu zabezpečení použít.</span><span class="sxs-lookup"><span data-stu-id="48735-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48735-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48735-116">Child Elements</span></span>  
 <span data-ttu-id="48735-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="48735-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48735-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48735-118">Parent Elements</span></span>  
  
|<span data-ttu-id="48735-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="48735-119">Element</span></span>|<span data-ttu-id="48735-120">Popis</span><span class="sxs-lookup"><span data-stu-id="48735-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48735-121">\<add></span><span class="sxs-lookup"><span data-stu-id="48735-121">\<add></span></span>](add.md)|<span data-ttu-id="48735-122">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="48735-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48735-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48735-123">Remarks</span></span>  
 <span data-ttu-id="48735-124">Element nastaví vlastnost, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> když <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> je objekt inicializován z konfigurace. `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="48735-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48735-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="48735-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
