---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 61b128d5856fd8e35516949b637177dc38a17164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="bad01-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="bad01-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="bad01-103">Nastaví typ obslužné rutiny vlastní soubor cookie.</span><span class="sxs-lookup"><span data-stu-id="bad01-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="bad01-104">Tento element může být pouze existuje-li `mode` atribut `<cookieHandler>` element je "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="bad01-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="bad01-105">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bad01-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="bad01-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="bad01-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="bad01-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bad01-107">\<federationConfiguration></span></span>  
<span data-ttu-id="bad01-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bad01-108">\<cookieHandler></span></span>  
<span data-ttu-id="bad01-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bad01-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad01-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bad01-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bad01-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bad01-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bad01-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bad01-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bad01-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bad01-113">Attributes</span></span>  
  
|<span data-ttu-id="bad01-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bad01-114">Attribute</span></span>|<span data-ttu-id="bad01-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bad01-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bad01-116">– typ</span><span class="sxs-lookup"><span data-stu-id="bad01-116">type</span></span>|<span data-ttu-id="bad01-117">Určuje vlastního typu, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bad01-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="bad01-118">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="bad01-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bad01-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bad01-119">Child Elements</span></span>  
 <span data-ttu-id="bad01-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="bad01-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bad01-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bad01-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bad01-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="bad01-122">Element</span></span>|<span data-ttu-id="bad01-123">Popis</span><span class="sxs-lookup"><span data-stu-id="bad01-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bad01-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bad01-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="bad01-125">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="bad01-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad01-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bad01-126">Remarks</span></span>  
 <span data-ttu-id="bad01-127">Pokud zadáte vlastní soubor cookie obslužnou rutinu nastavením `mode` atribut `<cookieHandler>` element na "Vlastní", je třeba zadat typ obslužné rutiny vlastní soubor cookie zahrnutím `<customCookieHandler>` podřízený element, který odkazuje na typ obslužné rutiny souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="bad01-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="bad01-128">Tento element nemůže být zadán, kdy `mode` atributu je nastavena na "Chunked" nebo "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="bad01-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="bad01-129">Vlastní soubor cookie obslužné rutiny musí být odvozeny od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bad01-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="bad01-130">`<customCookieHandler>` Element je reprezentována <xref:System.IdentityModel.Configuration.CustomTypeElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="bad01-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad01-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="bad01-131">Example</span></span>  
 <span data-ttu-id="bad01-132">Následující příklad konfiguruje SAM použít vlastní soubor cookie obslužnou rutinu typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="bad01-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bad01-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bad01-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
