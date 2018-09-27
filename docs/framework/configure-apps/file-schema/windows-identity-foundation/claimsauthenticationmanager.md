---
title: '&lt;komponenty claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 0ec7e44363f87e54eae97b70352f520fe87540be
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235267"
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="2b214-102">&lt;komponenty claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="2b214-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="2b214-103">Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="2b214-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="2b214-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2b214-104">\<system.identityModel></span></span>  
<span data-ttu-id="2b214-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2b214-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2b214-106">\<komponenty claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="2b214-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b214-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b214-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b214-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b214-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b214-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b214-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b214-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b214-110">Attributes</span></span>  
  
|<span data-ttu-id="2b214-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b214-111">Attribute</span></span>|<span data-ttu-id="2b214-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2b214-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b214-113">– typ</span><span class="sxs-lookup"><span data-stu-id="2b214-113">type</span></span>|<span data-ttu-id="2b214-114">Určuje, která je odvozena z vlastního typu <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="2b214-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="2b214-115">Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="2b214-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b214-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b214-116">Child Elements</span></span>  
 <span data-ttu-id="2b214-117">Pokud není žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2b214-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b214-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b214-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2b214-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b214-119">Element</span></span>|<span data-ttu-id="2b214-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2b214-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b214-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2b214-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="2b214-122">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="2b214-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b214-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b214-123">Remarks</span></span>  
 <span data-ttu-id="2b214-124">Výchozí chování zajišťována <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vypisuje příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="2b214-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="2b214-125">Pokud ne `type` je zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b214-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="2b214-126">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="2b214-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="2b214-127">Odvozené třídy může podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element tak, že přepíšete <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="2b214-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="2b214-128">Schéma definice pro podřízené prvky je až návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="2b214-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="2b214-129">`<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2b214-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b214-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b214-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
