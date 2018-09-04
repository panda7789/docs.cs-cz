---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 596cab4494ef3ba200fd0a046d7935f648fb7c4f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503212"
---
# <a name="ltremovegt"></a><span data-ttu-id="46611-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="46611-102">&lt;remove&gt;</span></span>
<span data-ttu-id="46611-103">Odebere obslužnou rutinu tokenu se zadaným zabezpečením z kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="46611-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="46611-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="46611-104">\<system.identityModel></span></span>  
<span data-ttu-id="46611-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="46611-105">\<identityConfiguration></span></span>  
<span data-ttu-id="46611-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="46611-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="46611-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="46611-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46611-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46611-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46611-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46611-109">Attributes and Elements</span></span>  
 <span data-ttu-id="46611-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46611-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46611-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="46611-111">Attributes</span></span>  
  
|<span data-ttu-id="46611-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="46611-112">Attribute</span></span>|<span data-ttu-id="46611-113">Popis</span><span class="sxs-lookup"><span data-stu-id="46611-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46611-114">– typ</span><span class="sxs-lookup"><span data-stu-id="46611-114">type</span></span>|<span data-ttu-id="46611-115">Název typu CLR obslužnou rutinu tokenu, která se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="46611-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="46611-116">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="46611-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="46611-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46611-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46611-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46611-118">Child Elements</span></span>  
 <span data-ttu-id="46611-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="46611-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46611-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46611-120">Parent Elements</span></span>  
  
|<span data-ttu-id="46611-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="46611-121">Element</span></span>|<span data-ttu-id="46611-122">Popis</span><span class="sxs-lookup"><span data-stu-id="46611-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46611-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="46611-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="46611-124">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="46611-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46611-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="46611-125">Example</span></span>  
 <span data-ttu-id="46611-126">Následující kód XML ukazuje použití `<add>` a `<remove>` prvků, které mají výchozí obslužnou rutinu tokenu relace nahraďte obslužnou rutinu tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="46611-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="46611-127">XML je převzata z `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="46611-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
