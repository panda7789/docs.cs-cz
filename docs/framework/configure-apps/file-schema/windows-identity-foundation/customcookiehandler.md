---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942785"
---
# <a name="customcookiehandler"></a><span data-ttu-id="80709-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="80709-101">\<customCookieHandler></span></span>
<span data-ttu-id="80709-102">Nastaví typ obslužné rutiny vlastního souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="80709-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="80709-103">Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že je atribut elementu "Custom".</span><span class="sxs-lookup"><span data-stu-id="80709-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="80709-104">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="80709-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="80709-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="80709-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="80709-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="80709-106">\<federationConfiguration></span></span>  
<span data-ttu-id="80709-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="80709-107">\<cookieHandler></span></span>  
<span data-ttu-id="80709-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="80709-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80709-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80709-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80709-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80709-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80709-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80709-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80709-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="80709-112">Attributes</span></span>  
  
|<span data-ttu-id="80709-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="80709-113">Attribute</span></span>|<span data-ttu-id="80709-114">Popis</span><span class="sxs-lookup"><span data-stu-id="80709-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80709-115">– typ</span><span class="sxs-lookup"><span data-stu-id="80709-115">type</span></span>|<span data-ttu-id="80709-116">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="80709-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="80709-117">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="80709-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80709-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80709-118">Child Elements</span></span>  
 <span data-ttu-id="80709-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="80709-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80709-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80709-120">Parent Elements</span></span>  
  
|<span data-ttu-id="80709-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="80709-121">Element</span></span>|<span data-ttu-id="80709-122">Popis</span><span class="sxs-lookup"><span data-stu-id="80709-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80709-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="80709-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="80709-124">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , že používá ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="80709-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80709-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80709-125">Remarks</span></span>  
 <span data-ttu-id="80709-126">Když zadáte vlastní obslužnou rutinu souborů cookie nastavením `mode` atributu `<cookieHandler>` elementu na "Custom", je nutné zadat typ obslužné rutiny vlastního `<customCookieHandler>` souboru cookie zahrnutím podřízeného prvku, který odkazuje na typ obslužné rutiny cookie.</span><span class="sxs-lookup"><span data-stu-id="80709-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="80709-127">Tento prvek nelze zadat, pokud `mode` je atribut nastaven na hodnotu "v bloku" nebo "default".</span><span class="sxs-lookup"><span data-stu-id="80709-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="80709-128">Vlastní obslužné rutiny souborů cookie musí <xref:System.IdentityModel.Services.CookieHandler> být odvozeny od třídy.</span><span class="sxs-lookup"><span data-stu-id="80709-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="80709-129">Element je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement>třídou. `<customCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="80709-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80709-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="80709-130">Example</span></span>  
 <span data-ttu-id="80709-131">Následující příklad nakonfiguruje SAM tak, aby používal vlastní obslužnou rutinu cookie `MyNamespace.MyCustomCookieHandler`typu.</span><span class="sxs-lookup"><span data-stu-id="80709-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80709-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80709-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
