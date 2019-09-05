---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252094"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="d6b3a-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="d6b3a-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="d6b3a-102">Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="d6b3a-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6b3a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6b3a-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d6b3a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d6b3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d6b3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d6b3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Komponenty ClaimsAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="d6b3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b3a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b3a-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6b3a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6b3a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6b3a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6b3a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6b3a-110">Attributes</span></span>  
  
|<span data-ttu-id="d6b3a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6b3a-111">Attribute</span></span>|<span data-ttu-id="d6b3a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b3a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6b3a-113">– typ</span><span class="sxs-lookup"><span data-stu-id="d6b3a-113">type</span></span>|<span data-ttu-id="d6b3a-114">Určuje vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="d6b3a-115">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="d6b3a-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6b3a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b3a-116">Child Elements</span></span>  
 <span data-ttu-id="d6b3a-117">`type` Pokud neexistuje žádný atribut, nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Pokud atribut `<claimsAuthenticationManager>` odkazuje na třídu, element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> mohou však definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6b3a-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b3a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d6b3a-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6b3a-119">Element</span></span>|<span data-ttu-id="d6b3a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b3a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6b3a-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d6b3a-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d6b3a-122">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b3a-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6b3a-123">Remarks</span></span>  
 <span data-ttu-id="d6b3a-124">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vychází z příchozích deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="d6b3a-125">Pokud není `type` zadán žádný atribut nebo `type` Pokud atribut `<claimsAuthenticationManager>` specifikuje <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="d6b3a-126">Můžete určit `type` atribut pro registraci typu odvozeného <xref:System.Security.Claims.ClaimsAuthenticationManager> od třídy pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="d6b3a-127">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> přepsáním metody pro zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="d6b3a-128">Schéma definované pro podřízené prvky je až do návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="d6b3a-129">`<claimsAuthenticationManager>` Prvek<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> nastaví vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d6b3a-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b3a-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b3a-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
