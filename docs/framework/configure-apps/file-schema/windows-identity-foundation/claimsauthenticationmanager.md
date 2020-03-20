---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152746"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="c43df-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="c43df-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="c43df-102">Registruje správce ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c43df-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="c43df-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c43df-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c43df-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c43df-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c43df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c43df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c43df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span><span class="sxs-lookup"><span data-stu-id="c43df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43df-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c43df-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c43df-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c43df-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c43df-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c43df-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c43df-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c43df-110">Attributes</span></span>  
  
|<span data-ttu-id="c43df-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c43df-111">Attribute</span></span>|<span data-ttu-id="c43df-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c43df-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c43df-113">type</span><span class="sxs-lookup"><span data-stu-id="c43df-113">type</span></span>|<span data-ttu-id="c43df-114">Určuje vlastní typ, který je <xref:System.Security.Claims.ClaimsAuthenticationManager> odvozen od třídy.</span><span class="sxs-lookup"><span data-stu-id="c43df-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="c43df-115">Další informace o tom, `type` jak zadat atribut, naleznete v tématu [Vlastní odkazy typu].</span><span class="sxs-lookup"><span data-stu-id="c43df-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c43df-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c43df-116">Child Elements</span></span>  
 <span data-ttu-id="c43df-117">Pokud neexistuje `type` žádný atribut nebo `type` pokud atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> odkazuje `<claimsAuthenticationManager>` na třídu, prvek nepřijímá podřízené prvky; třídy odvozené <xref:System.Security.Claims.ClaimsAuthenticationManager> z však můžete definovat podřízené konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="c43df-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c43df-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c43df-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c43df-119">Element</span><span class="sxs-lookup"><span data-stu-id="c43df-119">Element</span></span>|<span data-ttu-id="c43df-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c43df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c43df-121">\<identityKonfigurace></span><span class="sxs-lookup"><span data-stu-id="c43df-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="c43df-122">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="c43df-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c43df-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c43df-123">Remarks</span></span>  
 <span data-ttu-id="c43df-124">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy odráží příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c43df-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="c43df-125">Pokud `type` není zadán žádný `type` atribut nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> pokud atribut `<claimsAuthenticationManager>` určuje třídu, prvek nepřevezme podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="c43df-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="c43df-126">Můžete zadat `type` atribut pro registraci typu <xref:System.Security.Claims.ClaimsAuthenticationManager> odvozeného od třídy k implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="c43df-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="c43df-127">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody zpracování těchto prvků.</span><span class="sxs-lookup"><span data-stu-id="c43df-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="c43df-128">Schéma definované pro podřízené prvky je na návrháři třídy.</span><span class="sxs-lookup"><span data-stu-id="c43df-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="c43df-129">Element `<claimsAuthenticationManager>` nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c43df-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c43df-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c43df-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
