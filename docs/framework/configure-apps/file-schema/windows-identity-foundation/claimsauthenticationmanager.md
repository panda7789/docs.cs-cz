---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="8ffa9-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="8ffa9-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="8ffa9-103">Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="8ffa9-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8ffa9-104">\<system.identityModel></span></span>  
<span data-ttu-id="8ffa9-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8ffa9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8ffa9-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8ffa9-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ffa9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ffa9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ffa9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ffa9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ffa9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ffa9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ffa9-110">Attributes</span></span>  
  
|<span data-ttu-id="8ffa9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ffa9-111">Attribute</span></span>|<span data-ttu-id="8ffa9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8ffa9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ffa9-113">– typ</span><span class="sxs-lookup"><span data-stu-id="8ffa9-113">type</span></span>|<span data-ttu-id="8ffa9-114">Určuje vlastního typu, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="8ffa9-115">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="8ffa9-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ffa9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ffa9-116">Child Elements</span></span>  
 <span data-ttu-id="8ffa9-117">Pokud je žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené od <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ffa9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ffa9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8ffa9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ffa9-119">Element</span></span>|<span data-ttu-id="8ffa9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="8ffa9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ffa9-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8ffa9-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="8ffa9-122">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ffa9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ffa9-123">Remarks</span></span>  
 <span data-ttu-id="8ffa9-124">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třída vrátí příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="8ffa9-125">Pokud žádné `type` zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nemusí provádět žádné podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="8ffa9-126">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="8ffa9-127">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="8ffa9-128">Schéma definované pro podřízené elementy závisí návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="8ffa9-129">`<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8ffa9-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ffa9-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ffa9-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
