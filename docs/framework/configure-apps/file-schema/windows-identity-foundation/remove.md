---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758414"
---
# <a name="remove"></a><span data-ttu-id="a58fa-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="a58fa-101">\<remove></span></span>
<span data-ttu-id="a58fa-102">Odebere obslužnou rutinu tokenu se zadaným zabezpečením z kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="a58fa-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="a58fa-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a58fa-103">\<system.identityModel></span></span>  
<span data-ttu-id="a58fa-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a58fa-104">\<identityConfiguration></span></span>  
<span data-ttu-id="a58fa-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a58fa-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a58fa-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="a58fa-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58fa-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a58fa-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a58fa-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a58fa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a58fa-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a58fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a58fa-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a58fa-110">Attributes</span></span>  
  
|<span data-ttu-id="a58fa-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a58fa-111">Attribute</span></span>|<span data-ttu-id="a58fa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a58fa-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a58fa-113">– typ</span><span class="sxs-lookup"><span data-stu-id="a58fa-113">type</span></span>|<span data-ttu-id="a58fa-114">Název typu CLR obslužnou rutinu tokenu, která se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="a58fa-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="a58fa-115">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="a58fa-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="a58fa-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a58fa-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a58fa-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a58fa-117">Child Elements</span></span>  
 <span data-ttu-id="a58fa-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="a58fa-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a58fa-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a58fa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a58fa-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a58fa-120">Element</span></span>|<span data-ttu-id="a58fa-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a58fa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a58fa-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a58fa-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="a58fa-123">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a58fa-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a58fa-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a58fa-124">Example</span></span>  
 <span data-ttu-id="a58fa-125">Následující kód XML ukazuje použití `<add>` a `<remove>` prvků, které mají výchozí obslužnou rutinu tokenu relace nahraďte obslužnou rutinu tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="a58fa-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="a58fa-126">XML je převzata z `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="a58fa-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
