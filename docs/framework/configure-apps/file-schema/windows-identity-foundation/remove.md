---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfea0b0eb4b133308f10b523a659cc00f87252b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755070"
---
# <a name="ltremovegt"></a><span data-ttu-id="6c597-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="6c597-102">&lt;remove&gt;</span></span>
<span data-ttu-id="6c597-103">Odebere zadaný zabezpečení obslužná rutina tokenu z kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="6c597-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="6c597-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6c597-104">\<system.identityModel></span></span>  
<span data-ttu-id="6c597-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6c597-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6c597-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6c597-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6c597-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="6c597-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c597-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c597-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c597-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c597-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c597-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c597-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c597-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c597-111">Attributes</span></span>  
  
|<span data-ttu-id="6c597-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c597-112">Attribute</span></span>|<span data-ttu-id="6c597-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6c597-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c597-114">– typ</span><span class="sxs-lookup"><span data-stu-id="6c597-114">type</span></span>|<span data-ttu-id="6c597-115">Název typu CLR obslužná rutina tokenu odeberou.</span><span class="sxs-lookup"><span data-stu-id="6c597-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="6c597-116">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="6c597-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="6c597-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c597-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c597-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6c597-118">Child Elements</span></span>  
 <span data-ttu-id="6c597-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="6c597-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c597-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6c597-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6c597-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c597-121">Element</span></span>|<span data-ttu-id="6c597-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6c597-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c597-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6c597-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="6c597-124">Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6c597-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c597-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c597-125">Example</span></span>  
 <span data-ttu-id="6c597-126">Následující kód XML ukazuje použití `<add>` a `<remove>` elementy nahradit výchozí obslužnou rutinu tokenu relace obslužnou rutinu tokenu vlastní relaci.</span><span class="sxs-lookup"><span data-stu-id="6c597-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="6c597-127">Soubor XML je převzat ze `ClaimsAwareWebFarm` ukázka.</span><span class="sxs-lookup"><span data-stu-id="6c597-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
