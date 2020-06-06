---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252020"
---
# \<customCookieHandler>
<span data-ttu-id="bca7d-101">Nastaví typ obslužné rutiny vlastního souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="bca7d-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="bca7d-102">Tento element může být k dispozici pouze v případě, že `mode` `<cookieHandler>` je atribut elementu "Custom".</span><span class="sxs-lookup"><span data-stu-id="bca7d-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="bca7d-103">Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bca7d-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="bca7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca7d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca7d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bca7d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bca7d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bca7d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca7d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="bca7d-107">Attributes</span></span>  
  
|<span data-ttu-id="bca7d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="bca7d-108">Attribute</span></span>|<span data-ttu-id="bca7d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bca7d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bca7d-110">typ</span><span class="sxs-lookup"><span data-stu-id="bca7d-110">type</span></span>|<span data-ttu-id="bca7d-111">Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bca7d-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="bca7d-112">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="bca7d-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bca7d-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bca7d-113">Child Elements</span></span>  
 <span data-ttu-id="bca7d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="bca7d-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca7d-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bca7d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bca7d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="bca7d-116">Element</span></span>|<span data-ttu-id="bca7d-117">Description</span><span class="sxs-lookup"><span data-stu-id="bca7d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="bca7d-118">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , že <xref:System.IdentityModel.Services.SessionAuthenticationModule> používá ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="bca7d-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca7d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bca7d-119">Remarks</span></span>  
 <span data-ttu-id="bca7d-120">Když zadáte vlastní obslužnou rutinu souborů cookie nastavením `mode` atributu `<cookieHandler>` elementu na "Custom", je nutné zadat typ obslužné rutiny vlastního souboru cookie zahrnutím `<customCookieHandler>` podřízeného prvku, který odkazuje na typ obslužné rutiny cookie.</span><span class="sxs-lookup"><span data-stu-id="bca7d-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="bca7d-121">Tento prvek nelze zadat, pokud `mode` je atribut nastaven na hodnotu "v bloku" nebo "default".</span><span class="sxs-lookup"><span data-stu-id="bca7d-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="bca7d-122">Vlastní obslužné rutiny souborů cookie musí být odvozeny od <xref:System.IdentityModel.Services.CookieHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="bca7d-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="bca7d-123">`<customCookieHandler>`Element je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="bca7d-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca7d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="bca7d-124">Example</span></span>  
 <span data-ttu-id="bca7d-125">Následující příklad nakonfiguruje SAM tak, aby používal vlastní obslužnou rutinu cookie typu `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="bca7d-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bca7d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="bca7d-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
