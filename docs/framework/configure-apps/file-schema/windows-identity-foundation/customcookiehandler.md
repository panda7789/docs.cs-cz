---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a3d032279d0b568d7072dbbe020344365c341c1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724015"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="be71b-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="be71b-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="be71b-103">Nastaví typ obslužné rutiny vlastních souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="be71b-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="be71b-104">Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="be71b-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="be71b-105">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="be71b-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="be71b-106">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="be71b-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="be71b-107">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="be71b-107">\<federationConfiguration></span></span>  
<span data-ttu-id="be71b-108">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="be71b-108">\<cookieHandler></span></span>  
<span data-ttu-id="be71b-109">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="be71b-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be71b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be71b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be71b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="be71b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="be71b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="be71b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be71b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="be71b-113">Attributes</span></span>  
  
|<span data-ttu-id="be71b-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="be71b-114">Attribute</span></span>|<span data-ttu-id="be71b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="be71b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be71b-116">– typ</span><span class="sxs-lookup"><span data-stu-id="be71b-116">type</span></span>|<span data-ttu-id="be71b-117">Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="be71b-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="be71b-118">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="be71b-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be71b-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="be71b-119">Child Elements</span></span>  
 <span data-ttu-id="be71b-120">Žádná</span><span class="sxs-lookup"><span data-stu-id="be71b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be71b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="be71b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="be71b-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="be71b-122">Element</span></span>|<span data-ttu-id="be71b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="be71b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be71b-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="be71b-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="be71b-125">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="be71b-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be71b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be71b-126">Remarks</span></span>  
 <span data-ttu-id="be71b-127">Při zadání obslužné rutiny vlastních souborů cookie pomocí nastavení `mode` atribut `<cookieHandler>` element "Vlastní", je třeba zadat typ obslužné rutiny vlastních souborů cookie zahrnutím `<customCookieHandler>` podřízený prvek, který odkazuje na typ obslužné rutiny souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="be71b-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="be71b-128">Tento element nemůže být zadán při `mode` atribut je nastaven na "Bloku dat" nebo "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="be71b-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="be71b-129">Vlastní soubor cookie obslužné rutiny musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="be71b-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="be71b-130">`<customCookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="be71b-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be71b-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="be71b-131">Example</span></span>  
 <span data-ttu-id="be71b-132">Následující příklad nastaví SAM použít vlastní soubor cookie obslužné rutiny typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="be71b-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be71b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be71b-133">See also</span></span>
- <xref:System.IdentityModel.Services.CookieHandler>
