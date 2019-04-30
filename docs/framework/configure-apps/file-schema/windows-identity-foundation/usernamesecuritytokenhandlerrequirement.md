---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790452"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="67e5e-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="67e5e-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="67e5e-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="67e5e-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="67e5e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="67e5e-103">\<system.identityModel></span></span>  
<span data-ttu-id="67e5e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="67e5e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="67e5e-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="67e5e-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="67e5e-106">\<add></span><span class="sxs-lookup"><span data-stu-id="67e5e-106">\<add></span></span>  
<span data-ttu-id="67e5e-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="67e5e-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e5e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67e5e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67e5e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="67e5e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="67e5e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="67e5e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67e5e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="67e5e-111">Attributes</span></span>  
  
|<span data-ttu-id="67e5e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="67e5e-112">Attribute</span></span>|<span data-ttu-id="67e5e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="67e5e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67e5e-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="67e5e-114">membershipProviderName</span></span>|<span data-ttu-id="67e5e-115">Určuje, <xref:System.Web.Security.MembershipProvider> , který by měly být používány obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67e5e-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67e5e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="67e5e-116">Child Elements</span></span>  
 <span data-ttu-id="67e5e-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="67e5e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67e5e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="67e5e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="67e5e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="67e5e-119">Element</span></span>|<span data-ttu-id="67e5e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="67e5e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67e5e-121">\<add></span><span class="sxs-lookup"><span data-stu-id="67e5e-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="67e5e-122">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="67e5e-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67e5e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67e5e-123">Remarks</span></span>  
 <span data-ttu-id="67e5e-124">`<userNameSecurityTokenHandlerRequirement>` Nastaví element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> vlastnost při <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67e5e-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e5e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="67e5e-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
