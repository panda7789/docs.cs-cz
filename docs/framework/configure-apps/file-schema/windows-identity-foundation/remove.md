---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 11aeed0277fc13cbd9a65232311bd575a4a81ff7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942574"
---
# <a name="remove"></a><span data-ttu-id="6f6fb-101">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="6f6fb-101">\<remove></span></span>
<span data-ttu-id="6f6fb-102">Odebere zadanou obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="6f6fb-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6f6fb-103">\<system.identityModel></span></span>  
<span data-ttu-id="6f6fb-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="6f6fb-104">\<identityConfiguration></span></span>  
<span data-ttu-id="6f6fb-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6f6fb-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6f6fb-106">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="6f6fb-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f6fb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f6fb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6f6fb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f6fb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f6fb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6f6fb-110">Attributes</span></span>  
  
|<span data-ttu-id="6f6fb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6f6fb-111">Attribute</span></span>|<span data-ttu-id="6f6fb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6f6fb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f6fb-113">– typ</span><span class="sxs-lookup"><span data-stu-id="6f6fb-113">type</span></span>|<span data-ttu-id="6f6fb-114">Název typu CLR obslužné rutiny tokenu, která má být odebrána.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="6f6fb-115">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="6f6fb-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="6f6fb-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f6fb-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6f6fb-117">Child Elements</span></span>  
 <span data-ttu-id="6f6fb-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f6fb-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f6fb-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6f6fb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f6fb-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6f6fb-120">Element</span></span>|<span data-ttu-id="6f6fb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6f6fb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f6fb-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6f6fb-122">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="6f6fb-123">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f6fb-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f6fb-124">Example</span></span>  
 <span data-ttu-id="6f6fb-125">Následující kód XML ukazuje použití `<add>` elementů a `<remove>` k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="6f6fb-126">Kód XML je získán z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="6f6fb-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
