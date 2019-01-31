---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6a8c96fb2cb2050cac7b8853b84caecc883449d7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268779"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="72c25-102">\<add> of \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="72c25-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="72c25-103">Určuje typy požadovaných a volitelných deklarací, které se zobrazí ve federativním pověření.</span><span class="sxs-lookup"><span data-stu-id="72c25-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="72c25-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="72c25-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="72c25-105">\<system.serviceModel></span></span>  
<span data-ttu-id="72c25-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="72c25-106">\<bindings></span></span>  
<span data-ttu-id="72c25-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="72c25-107">\<customBinding></span></span>  
<span data-ttu-id="72c25-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="72c25-108">\<binding></span></span>  
<span data-ttu-id="72c25-109">\<security></span><span class="sxs-lookup"><span data-stu-id="72c25-109">\<security></span></span>  
<span data-ttu-id="72c25-110">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="72c25-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="72c25-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="72c25-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c25-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72c25-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72c25-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72c25-113">Attributes and Elements</span></span>  
 <span data-ttu-id="72c25-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72c25-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72c25-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="72c25-115">Attributes</span></span>  
  
|<span data-ttu-id="72c25-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="72c25-116">Attribute</span></span>|<span data-ttu-id="72c25-117">Popis</span><span class="sxs-lookup"><span data-stu-id="72c25-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72c25-118">claimType</span><span class="sxs-lookup"><span data-stu-id="72c25-118">claimType</span></span>|<span data-ttu-id="72c25-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="72c25-120">Například k nákupu z webu produktu, uživatel musí poskytnout uvedenou platnou platební kartu s dostatečnou kreditního limitu.</span><span class="sxs-lookup"><span data-stu-id="72c25-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="72c25-121">Typ deklarace by platební karty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="72c25-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="72c25-122">Schedule</span><span class="sxs-lookup"><span data-stu-id="72c25-122">isOptional</span></span>|<span data-ttu-id="72c25-123">Logická hodnota určující, zda je pro volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="72c25-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="72c25-124">Tento atribut nastavte na `false` Pokud je požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="72c25-125">Tento atribut můžete použít, když služba vyzve k zadání některé informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="72c25-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="72c25-126">Například pokud vyžadujete, aby uživatel zadal své jméno, příjmení a adresu, ale rozhodnout, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="72c25-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72c25-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72c25-127">Child Elements</span></span>  
 <span data-ttu-id="72c25-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="72c25-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72c25-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72c25-129">Parent Elements</span></span>  
  
|<span data-ttu-id="72c25-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="72c25-130">Element</span></span>|<span data-ttu-id="72c25-131">Popis</span><span class="sxs-lookup"><span data-stu-id="72c25-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72c25-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="72c25-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="72c25-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="72c25-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="72c25-134">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="72c25-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="72c25-135">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="72c25-136">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="72c25-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72c25-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72c25-137">Remarks</span></span>  
 <span data-ttu-id="72c25-138">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="72c25-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="72c25-139">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="72c25-140">Tento požadavek je označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="72c25-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="72c25-141">Pokud pověření klienta žádosti od federovaných služby (například služba CardSpace), vloží požadavky na žádost o token (RequestSecurityToken) tak, aby federované služby může vydat přihlašovací údaje, které splňují požadavky na odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="72c25-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c25-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="72c25-142">Example</span></span>  
 <span data-ttu-id="72c25-143">Následující konfigurace přidá do vazby zabezpečení požadavky na dva typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="72c25-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="72c25-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72c25-144">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="72c25-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="72c25-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)
- [<span data-ttu-id="72c25-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="72c25-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="72c25-147">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="72c25-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="72c25-148">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="72c25-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="72c25-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="72c25-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="72c25-150">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="72c25-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="72c25-151">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="72c25-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
