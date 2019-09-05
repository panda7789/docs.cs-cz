---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251738"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="1dbeb-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="1dbeb-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="1dbeb-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1dbeb-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="1dbeb-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1dbeb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1dbeb-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1dbeb-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1dbeb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1dbeb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1dbeb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="1dbeb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="1dbeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="1dbeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="1dbeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameSecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="1dbeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbeb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dbeb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dbeb-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1dbeb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1dbeb-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1dbeb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dbeb-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1dbeb-112">Attributes</span></span>  
  
|<span data-ttu-id="1dbeb-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1dbeb-113">Attribute</span></span>|<span data-ttu-id="1dbeb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1dbeb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dbeb-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="1dbeb-115">membershipProviderName</span></span>|<span data-ttu-id="1dbeb-116"><xref:System.Web.Security.MembershipProvider> Určuje, které má obslužná rutina tokenu zabezpečení použít.</span><span class="sxs-lookup"><span data-stu-id="1dbeb-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dbeb-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1dbeb-117">Child Elements</span></span>  
 <span data-ttu-id="1dbeb-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1dbeb-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1dbeb-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1dbeb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1dbeb-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1dbeb-120">Element</span></span>|<span data-ttu-id="1dbeb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1dbeb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dbeb-122">\<add></span><span class="sxs-lookup"><span data-stu-id="1dbeb-122">\<add></span></span>](add.md)|<span data-ttu-id="1dbeb-123">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1dbeb-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dbeb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1dbeb-124">Remarks</span></span>  
 <span data-ttu-id="1dbeb-125">Element nastaví vlastnost, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> když <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> je objekt inicializován z konfigurace. `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="1dbeb-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dbeb-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="1dbeb-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
