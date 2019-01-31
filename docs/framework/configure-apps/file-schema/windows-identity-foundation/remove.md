---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: a54957458311e2d5941d1aa1c2486a2f66994d9b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288129"
---
# <a name="remove"></a><span data-ttu-id="2fbd0-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="2fbd0-101">\<remove></span></span>
<span data-ttu-id="2fbd0-102">Odebere obslužnou rutinu tokenu se zadaným zabezpečením z kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="2fbd0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2fbd0-103">\<system.identityModel></span></span>  
<span data-ttu-id="2fbd0-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2fbd0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2fbd0-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2fbd0-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2fbd0-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="2fbd0-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbd0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fbd0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fbd0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fbd0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fbd0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fbd0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fbd0-110">Attributes</span></span>  
  
|<span data-ttu-id="2fbd0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2fbd0-111">Attribute</span></span>|<span data-ttu-id="2fbd0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2fbd0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fbd0-113">– typ</span><span class="sxs-lookup"><span data-stu-id="2fbd0-113">type</span></span>|<span data-ttu-id="2fbd0-114">Název typu CLR obslužnou rutinu tokenu, která se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="2fbd0-115">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="2fbd0-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="2fbd0-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fbd0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fbd0-117">Child Elements</span></span>  
 <span data-ttu-id="2fbd0-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="2fbd0-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fbd0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fbd0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2fbd0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fbd0-120">Element</span></span>|<span data-ttu-id="2fbd0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2fbd0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fbd0-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2fbd0-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="2fbd0-123">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2fbd0-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fbd0-124">Example</span></span>  
 <span data-ttu-id="2fbd0-125">Následující kód XML ukazuje použití `<add>` a `<remove>` prvků, které mají výchozí obslužnou rutinu tokenu relace nahraďte obslužnou rutinu tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="2fbd0-126">XML je převzata z `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="2fbd0-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
