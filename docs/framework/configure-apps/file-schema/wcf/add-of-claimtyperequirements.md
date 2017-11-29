---
title: "&lt;add&gt; – &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dea76ab05c92c009cbb959b8fdba57fd79e2967c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="19ccf-102">&lt;add&gt; – &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="19ccf-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="19ccf-103">Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="19ccf-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="19ccf-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="19ccf-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="19ccf-105">\<system.serviceModel></span></span>  
<span data-ttu-id="19ccf-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="19ccf-106">\<bindings></span></span>  
<span data-ttu-id="19ccf-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="19ccf-107">\<customBinding></span></span>  
<span data-ttu-id="19ccf-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="19ccf-108">\<binding></span></span>  
<span data-ttu-id="19ccf-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="19ccf-109">\<security></span></span>  
<span data-ttu-id="19ccf-110">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="19ccf-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="19ccf-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="19ccf-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ccf-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19ccf-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19ccf-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19ccf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="19ccf-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19ccf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19ccf-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="19ccf-115">Attributes</span></span>  
  
|<span data-ttu-id="19ccf-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="19ccf-116">Attribute</span></span>|<span data-ttu-id="19ccf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="19ccf-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19ccf-118">Typ claimType</span><span class="sxs-lookup"><span data-stu-id="19ccf-118">claimType</span></span>|<span data-ttu-id="19ccf-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="19ccf-120">Například k nákupu produktu z webu, uživatel musí představovat platná platební karta úvěr dostatečná.</span><span class="sxs-lookup"><span data-stu-id="19ccf-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="19ccf-121">Typ deklarace by platební karty identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="19ccf-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="19ccf-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="19ccf-122">isOptional</span></span>|<span data-ttu-id="19ccf-123">Logická hodnota, která určuje, zda se pro volitelné deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="19ccf-124">Nastavte tento atribut `false` Pokud to není požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="19ccf-125">Tento atribut můžete použít při služby požádá o některé informace, ale není nutné.</span><span class="sxs-lookup"><span data-stu-id="19ccf-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="19ccf-126">Například pokud požadujete, aby uživatel zadal jejich křestní jméno, příjmení a adresa, ale rozhodnout, zda telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="19ccf-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19ccf-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19ccf-127">Child Elements</span></span>  
 <span data-ttu-id="19ccf-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="19ccf-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19ccf-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19ccf-129">Parent Elements</span></span>  
  
|<span data-ttu-id="19ccf-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="19ccf-130">Element</span></span>|<span data-ttu-id="19ccf-131">Popis</span><span class="sxs-lookup"><span data-stu-id="19ccf-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19ccf-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="19ccf-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="19ccf-133">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="19ccf-134">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="19ccf-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="19ccf-135">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="19ccf-136">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="19ccf-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19ccf-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19ccf-137">Remarks</span></span>  
 <span data-ttu-id="19ccf-138">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="19ccf-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="19ccf-139">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="19ccf-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="19ccf-140">Tento požadavek označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="19ccf-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="19ccf-141">Pokud pověření klienta žádosti od federovaných služby (například CardSpace), vloží požadavků do (třída RequestSecurityToken) žádosti o token tak, aby federované služby můžete vydat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="19ccf-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19ccf-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="19ccf-142">Example</span></span>  
 <span data-ttu-id="19ccf-143">Následující konfigurace přidá dva požadavky na typ deklarace identity do vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="19ccf-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19ccf-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="19ccf-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="19ccf-145">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="19ccf-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="19ccf-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="19ccf-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="19ccf-147">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="19ccf-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="19ccf-148">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="19ccf-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="19ccf-149">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="19ccf-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="19ccf-150">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19ccf-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="19ccf-151">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="19ccf-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
