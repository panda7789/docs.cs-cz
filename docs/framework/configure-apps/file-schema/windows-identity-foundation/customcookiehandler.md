---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252020"
---
# <a name="customcookiehandler"></a><span data-ttu-id="de29a-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="de29a-101">\<customCookieHandler></span></span>
<span data-ttu-id="de29a-102">Nastaví typ obslužné rutiny vlastního souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="de29a-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="de29a-103">Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že je atribut elementu "Custom".</span><span class="sxs-lookup"><span data-stu-id="de29a-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="de29a-104">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="de29a-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="de29a-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="de29a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de29a-106">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="de29a-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="de29a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="de29a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="de29a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="de29a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="de29a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="de29a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de29a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de29a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de29a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de29a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de29a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de29a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de29a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="de29a-113">Attributes</span></span>  
  
|<span data-ttu-id="de29a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="de29a-114">Attribute</span></span>|<span data-ttu-id="de29a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="de29a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de29a-116">– typ</span><span class="sxs-lookup"><span data-stu-id="de29a-116">type</span></span>|<span data-ttu-id="de29a-117">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="de29a-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="de29a-118">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="de29a-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de29a-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de29a-119">Child Elements</span></span>  
 <span data-ttu-id="de29a-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="de29a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de29a-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de29a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="de29a-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="de29a-122">Element</span></span>|<span data-ttu-id="de29a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="de29a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de29a-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="de29a-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="de29a-125">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , že používá ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="de29a-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de29a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de29a-126">Remarks</span></span>  
 <span data-ttu-id="de29a-127">Když zadáte vlastní obslužnou rutinu souborů cookie nastavením `mode` atributu `<cookieHandler>` elementu na "Custom", je nutné zadat typ obslužné rutiny vlastního `<customCookieHandler>` souboru cookie zahrnutím podřízeného prvku, který odkazuje na typ obslužné rutiny cookie.</span><span class="sxs-lookup"><span data-stu-id="de29a-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="de29a-128">Tento prvek nelze zadat, pokud `mode` je atribut nastaven na hodnotu "v bloku" nebo "default".</span><span class="sxs-lookup"><span data-stu-id="de29a-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="de29a-129">Vlastní obslužné rutiny souborů cookie musí <xref:System.IdentityModel.Services.CookieHandler> být odvozeny od třídy.</span><span class="sxs-lookup"><span data-stu-id="de29a-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="de29a-130">Element je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement>třídou. `<customCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="de29a-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de29a-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="de29a-131">Example</span></span>  
 <span data-ttu-id="de29a-132">Následující příklad nakonfiguruje SAM tak, aby používal vlastní obslužnou rutinu cookie `MyNamespace.MyCustomCookieHandler`typu.</span><span class="sxs-lookup"><span data-stu-id="de29a-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de29a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de29a-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
