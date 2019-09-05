---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251931"
---
# <a name="remove"></a><span data-ttu-id="0e124-101">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="0e124-101">\<remove></span></span>
<span data-ttu-id="0e124-102">Odebere zadanou obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="0e124-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="0e124-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e124-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0e124-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="0e124-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="0e124-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0e124-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="0e124-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="0e124-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="0e124-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="0e124-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e124-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e124-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e124-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e124-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e124-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e124-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e124-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e124-111">Attributes</span></span>  
  
|<span data-ttu-id="0e124-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="0e124-112">Attribute</span></span>|<span data-ttu-id="0e124-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0e124-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e124-114">– typ</span><span class="sxs-lookup"><span data-stu-id="0e124-114">type</span></span>|<span data-ttu-id="0e124-115">Název typu CLR obslužné rutiny tokenu, která má být odebrána.</span><span class="sxs-lookup"><span data-stu-id="0e124-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="0e124-116">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="0e124-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="0e124-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0e124-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e124-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e124-118">Child Elements</span></span>  
 <span data-ttu-id="0e124-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="0e124-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e124-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e124-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0e124-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e124-121">Element</span></span>|<span data-ttu-id="0e124-122">Popis</span><span class="sxs-lookup"><span data-stu-id="0e124-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e124-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0e124-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="0e124-124">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0e124-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e124-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e124-125">Example</span></span>  
 <span data-ttu-id="0e124-126">Následující kód XML ukazuje použití `<add>` elementů a `<remove>` k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="0e124-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="0e124-127">Kód XML je získán z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="0e124-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
