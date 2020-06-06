---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251931"
---
# \<remove>
<span data-ttu-id="4ea69-101">Odebere zadanou obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="4ea69-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="4ea69-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ea69-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ea69-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4ea69-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4ea69-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4ea69-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ea69-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="4ea69-105">Attributes</span></span>  
  
|<span data-ttu-id="4ea69-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="4ea69-106">Attribute</span></span>|<span data-ttu-id="4ea69-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4ea69-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ea69-108">typ</span><span class="sxs-lookup"><span data-stu-id="4ea69-108">type</span></span>|<span data-ttu-id="4ea69-109">Název typu CLR obslužné rutiny tokenu, která má být odebrána.</span><span class="sxs-lookup"><span data-stu-id="4ea69-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="4ea69-110">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="4ea69-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="4ea69-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4ea69-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ea69-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4ea69-112">Child Elements</span></span>  
 <span data-ttu-id="4ea69-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4ea69-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ea69-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4ea69-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4ea69-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="4ea69-115">Element</span></span>|<span data-ttu-id="4ea69-116">Description</span><span class="sxs-lookup"><span data-stu-id="4ea69-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="4ea69-117">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4ea69-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4ea69-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ea69-118">Example</span></span>  
 <span data-ttu-id="4ea69-119">Následující kód XML ukazuje použití `<add>` `<remove>` elementů a k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="4ea69-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="4ea69-120">KÓD XML je získán z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="4ea69-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
