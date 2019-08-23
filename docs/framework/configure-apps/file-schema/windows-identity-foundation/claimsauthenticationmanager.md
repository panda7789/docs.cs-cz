---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941819"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="37d92-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="37d92-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="37d92-102">Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="37d92-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="37d92-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37d92-103">\<system.identityModel></span></span>  
<span data-ttu-id="37d92-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37d92-104">\<identityConfiguration></span></span>  
<span data-ttu-id="37d92-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="37d92-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d92-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37d92-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37d92-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37d92-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37d92-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37d92-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37d92-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="37d92-109">Attributes</span></span>  
  
|<span data-ttu-id="37d92-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="37d92-110">Attribute</span></span>|<span data-ttu-id="37d92-111">Popis</span><span class="sxs-lookup"><span data-stu-id="37d92-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37d92-112">– typ</span><span class="sxs-lookup"><span data-stu-id="37d92-112">type</span></span>|<span data-ttu-id="37d92-113">Určuje vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="37d92-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="37d92-114">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="37d92-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37d92-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37d92-115">Child Elements</span></span>  
 <span data-ttu-id="37d92-116">`type` Pokud neexistuje žádný atribut, nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Pokud atribut `<claimsAuthenticationManager>` odkazuje na třídu, element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> mohou však definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="37d92-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37d92-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37d92-117">Parent Elements</span></span>  
  
|<span data-ttu-id="37d92-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="37d92-118">Element</span></span>|<span data-ttu-id="37d92-119">Popis</span><span class="sxs-lookup"><span data-stu-id="37d92-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37d92-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37d92-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="37d92-121">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="37d92-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37d92-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37d92-122">Remarks</span></span>  
 <span data-ttu-id="37d92-123">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vychází z příchozích deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="37d92-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="37d92-124">Pokud není `type` zadán žádný atribut nebo `type` Pokud atribut `<claimsAuthenticationManager>` specifikuje <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="37d92-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="37d92-125">Můžete určit `type` atribut pro registraci typu odvozeného <xref:System.Security.Claims.ClaimsAuthenticationManager> od třídy pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="37d92-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="37d92-126">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> přepsáním metody pro zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="37d92-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="37d92-127">Schéma definované pro podřízené prvky je až do návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="37d92-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="37d92-128">`<claimsAuthenticationManager>` Prvek<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> nastaví vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37d92-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37d92-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="37d92-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
