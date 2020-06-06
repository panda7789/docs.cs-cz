---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251738"
---
# \<userNameSecurityTokenHandlerRequirement>
<span data-ttu-id="84b9f-101">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="84b9f-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="84b9f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84b9f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84b9f-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="84b9f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="84b9f-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="84b9f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84b9f-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="84b9f-105">Attributes</span></span>  
  
|<span data-ttu-id="84b9f-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="84b9f-106">Attribute</span></span>|<span data-ttu-id="84b9f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="84b9f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84b9f-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="84b9f-108">membershipProviderName</span></span>|<span data-ttu-id="84b9f-109">Určuje <xref:System.Web.Security.MembershipProvider> , které má obslužná rutina tokenu zabezpečení použít.</span><span class="sxs-lookup"><span data-stu-id="84b9f-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84b9f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="84b9f-110">Child Elements</span></span>  
 <span data-ttu-id="84b9f-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="84b9f-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84b9f-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="84b9f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="84b9f-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="84b9f-113">Element</span></span>|<span data-ttu-id="84b9f-114">Description</span><span class="sxs-lookup"><span data-stu-id="84b9f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="84b9f-115">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="84b9f-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84b9f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84b9f-116">Remarks</span></span>  
 <span data-ttu-id="84b9f-117">`<userNameSecurityTokenHandlerRequirement>`Element nastaví vlastnost, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Když <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> je objekt inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="84b9f-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84b9f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="84b9f-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
