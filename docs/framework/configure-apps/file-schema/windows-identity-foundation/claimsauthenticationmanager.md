---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152746"
---
# \<claimsAuthenticationManager>
<span data-ttu-id="edaca-101">Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="edaca-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="edaca-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edaca-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edaca-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="edaca-103">Attributes and Elements</span></span>  
 <span data-ttu-id="edaca-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="edaca-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edaca-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="edaca-105">Attributes</span></span>  
  
|<span data-ttu-id="edaca-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="edaca-106">Attribute</span></span>|<span data-ttu-id="edaca-107">Popis</span><span class="sxs-lookup"><span data-stu-id="edaca-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edaca-108">typ</span><span class="sxs-lookup"><span data-stu-id="edaca-108">type</span></span>|<span data-ttu-id="edaca-109">Určuje vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="edaca-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="edaca-110">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="edaca-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edaca-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="edaca-111">Child Elements</span></span>  
 <span data-ttu-id="edaca-112">Pokud neexistuje žádný `type` atribut, nebo pokud `type` atribut odkazuje na <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, `<claimsAuthenticationManager>` element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> mohou však definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="edaca-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="edaca-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="edaca-113">Parent Elements</span></span>  
  
|<span data-ttu-id="edaca-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="edaca-114">Element</span></span>|<span data-ttu-id="edaca-115">Description</span><span class="sxs-lookup"><span data-stu-id="edaca-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="edaca-116">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="edaca-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edaca-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edaca-117">Remarks</span></span>  
 <span data-ttu-id="edaca-118">Výchozí chování poskytované prostřednictvím třídy vychází <xref:System.Security.Claims.ClaimsAuthenticationManager> z příchozích deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="edaca-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="edaca-119">Pokud není `type` zadán žádný atribut nebo pokud `type` atribut specifikuje <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, `<claimsAuthenticationManager>` element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="edaca-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="edaca-120">Můžete určit `type` atribut pro registraci typu odvozeného od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="edaca-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="edaca-121">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody pro zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="edaca-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="edaca-122">Schéma definované pro podřízené prvky je až do návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="edaca-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="edaca-123">`<claimsAuthenticationManager>`Prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="edaca-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edaca-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="edaca-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
