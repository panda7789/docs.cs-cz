---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791726"
---
# <a name="customcookiehandler"></a><span data-ttu-id="dfb70-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="dfb70-101">\<customCookieHandler></span></span>
<span data-ttu-id="dfb70-102">Nastaví typ obslužné rutiny vlastních souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="dfb70-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="dfb70-103">Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="dfb70-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="dfb70-104">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfb70-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="dfb70-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="dfb70-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="dfb70-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="dfb70-106">\<federationConfiguration></span></span>  
<span data-ttu-id="dfb70-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="dfb70-107">\<cookieHandler></span></span>  
<span data-ttu-id="dfb70-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="dfb70-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb70-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfb70-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfb70-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dfb70-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dfb70-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dfb70-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfb70-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="dfb70-112">Attributes</span></span>  
  
|<span data-ttu-id="dfb70-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="dfb70-113">Attribute</span></span>|<span data-ttu-id="dfb70-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dfb70-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfb70-115"> – typ</span><span class="sxs-lookup"><span data-stu-id="dfb70-115">type</span></span>|<span data-ttu-id="dfb70-116">Určuje, která je odvozena z vlastního typu <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfb70-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="dfb70-117">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfb70-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfb70-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dfb70-118">Child Elements</span></span>  
 <span data-ttu-id="dfb70-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="dfb70-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfb70-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dfb70-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dfb70-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="dfb70-121">Element</span></span>|<span data-ttu-id="dfb70-122">Popis</span><span class="sxs-lookup"><span data-stu-id="dfb70-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfb70-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="dfb70-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="dfb70-124">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="dfb70-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfb70-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfb70-125">Remarks</span></span>  
 <span data-ttu-id="dfb70-126">Při zadání obslužné rutiny vlastních souborů cookie pomocí nastavení `mode` atribut `<cookieHandler>` element "Vlastní", je třeba zadat typ obslužné rutiny vlastních souborů cookie zahrnutím `<customCookieHandler>` podřízený prvek, který odkazuje na typ obslužné rutiny souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="dfb70-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="dfb70-127">Tento element nemůže být zadán při `mode` atribut je nastaven na "Bloku dat" nebo "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="dfb70-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="dfb70-128">Vlastní soubor cookie obslužné rutiny musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfb70-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="dfb70-129">`<customCookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfb70-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfb70-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfb70-130">Example</span></span>  
 <span data-ttu-id="dfb70-131">Následující příklad nastaví SAM použít vlastní soubor cookie obslužné rutiny typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="dfb70-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfb70-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfb70-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
