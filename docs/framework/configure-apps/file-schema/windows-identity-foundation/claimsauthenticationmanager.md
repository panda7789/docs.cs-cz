---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667324"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="41f3c-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="41f3c-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="41f3c-102">Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="41f3c-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="41f3c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="41f3c-103">\<system.identityModel></span></span>  
<span data-ttu-id="41f3c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="41f3c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="41f3c-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="41f3c-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f3c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f3c-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f3c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="41f3c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="41f3c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="41f3c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f3c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="41f3c-109">Attributes</span></span>  
  
|<span data-ttu-id="41f3c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="41f3c-110">Attribute</span></span>|<span data-ttu-id="41f3c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="41f3c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41f3c-112"> – typ</span><span class="sxs-lookup"><span data-stu-id="41f3c-112">type</span></span>|<span data-ttu-id="41f3c-113">Určuje, která je odvozena z vlastního typu <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="41f3c-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="41f3c-114">Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="41f3c-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41f3c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="41f3c-115">Child Elements</span></span>  
 <span data-ttu-id="41f3c-116">Pokud není žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="41f3c-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f3c-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="41f3c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="41f3c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="41f3c-118">Element</span></span>|<span data-ttu-id="41f3c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="41f3c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41f3c-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="41f3c-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="41f3c-121">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="41f3c-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f3c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41f3c-122">Remarks</span></span>  
 <span data-ttu-id="41f3c-123">Výchozí chování zajišťována <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vypisuje příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="41f3c-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="41f3c-124">Pokud ne `type` je zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="41f3c-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="41f3c-125">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="41f3c-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="41f3c-126">Odvozené třídy může podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element tak, že přepíšete <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="41f3c-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="41f3c-127">Schéma definice pro podřízené prvky je až návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="41f3c-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="41f3c-128">`<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="41f3c-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f3c-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="41f3c-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
