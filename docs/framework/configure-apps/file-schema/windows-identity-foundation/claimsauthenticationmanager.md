---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b7d68c2fe89b5ca56319df2f24fadd51f329f5ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="27456-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="27456-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="27456-103">Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="27456-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="27456-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="27456-104">\<system.identityModel></span></span>  
<span data-ttu-id="27456-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="27456-105">\<identityConfiguration></span></span>  
<span data-ttu-id="27456-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="27456-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27456-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27456-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27456-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27456-108">Attributes and Elements</span></span>  
 <span data-ttu-id="27456-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27456-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27456-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="27456-110">Attributes</span></span>  
  
|<span data-ttu-id="27456-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="27456-111">Attribute</span></span>|<span data-ttu-id="27456-112">Popis</span><span class="sxs-lookup"><span data-stu-id="27456-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27456-113">– typ</span><span class="sxs-lookup"><span data-stu-id="27456-113">type</span></span>|<span data-ttu-id="27456-114">Určuje vlastního typu, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="27456-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="27456-115">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="27456-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27456-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27456-116">Child Elements</span></span>  
 <span data-ttu-id="27456-117">Pokud je žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené od <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="27456-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27456-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27456-118">Parent Elements</span></span>  
  
|<span data-ttu-id="27456-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="27456-119">Element</span></span>|<span data-ttu-id="27456-120">Popis</span><span class="sxs-lookup"><span data-stu-id="27456-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27456-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="27456-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="27456-122">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="27456-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27456-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27456-123">Remarks</span></span>  
 <span data-ttu-id="27456-124">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třída vrátí příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="27456-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="27456-125">Pokud žádné `type` zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nemusí provádět žádné podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="27456-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="27456-126">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="27456-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="27456-127">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="27456-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="27456-128">Schéma definované pro podřízené elementy závisí návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="27456-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="27456-129">`<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="27456-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27456-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="27456-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
