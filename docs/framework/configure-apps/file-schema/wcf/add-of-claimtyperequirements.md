---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 97d3ecca369aeffb7b2e8464f385eeae13bd470f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168841"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="7f98c-102">\<add> of \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7f98c-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="7f98c-103">Určuje typy požadovaných a volitelných deklarací, které se zobrazí ve federativním pověření.</span><span class="sxs-lookup"><span data-stu-id="7f98c-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="7f98c-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="7f98c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f98c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7f98c-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7f98c-106">\<bindings></span></span>  
<span data-ttu-id="7f98c-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7f98c-107">\<customBinding></span></span>  
<span data-ttu-id="7f98c-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7f98c-108">\<binding></span></span>  
<span data-ttu-id="7f98c-109">\<security></span><span class="sxs-lookup"><span data-stu-id="7f98c-109">\<security></span></span>  
<span data-ttu-id="7f98c-110">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="7f98c-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="7f98c-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7f98c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f98c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f98c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f98c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f98c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7f98c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f98c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f98c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f98c-115">Attributes</span></span>  
  
|<span data-ttu-id="7f98c-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f98c-116">Attribute</span></span>|<span data-ttu-id="7f98c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7f98c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f98c-118">claimType</span><span class="sxs-lookup"><span data-stu-id="7f98c-118">claimType</span></span>|<span data-ttu-id="7f98c-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="7f98c-120">Například k nákupu z webu produktu, uživatel musí poskytnout uvedenou platnou platební kartu s dostatečnou kreditního limitu.</span><span class="sxs-lookup"><span data-stu-id="7f98c-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="7f98c-121">Typ deklarace by platební karty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7f98c-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="7f98c-122">Schedule</span><span class="sxs-lookup"><span data-stu-id="7f98c-122">isOptional</span></span>|<span data-ttu-id="7f98c-123">Logická hodnota určující, zda je pro volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7f98c-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="7f98c-124">Tento atribut nastavte na `false` Pokud je požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="7f98c-125">Tento atribut můžete použít, když služba vyzve k zadání některé informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7f98c-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="7f98c-126">Například pokud vyžadujete, aby uživatel zadal své jméno, příjmení a adresu, ale rozhodnout, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="7f98c-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f98c-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f98c-127">Child Elements</span></span>  
 <span data-ttu-id="7f98c-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f98c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f98c-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f98c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7f98c-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f98c-130">Element</span></span>|<span data-ttu-id="7f98c-131">Popis</span><span class="sxs-lookup"><span data-stu-id="7f98c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f98c-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7f98c-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="7f98c-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="7f98c-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="7f98c-134">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="7f98c-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7f98c-135">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7f98c-136">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="7f98c-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f98c-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f98c-137">Remarks</span></span>  
 <span data-ttu-id="7f98c-138">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="7f98c-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7f98c-139">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7f98c-140">Tento požadavek je označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7f98c-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="7f98c-141">Pokud pověření klienta žádosti od federovaných služby (například služba CardSpace), vloží požadavky na žádost o token (RequestSecurityToken) tak, aby federované služby může vydat přihlašovací údaje, které splňují požadavky na odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7f98c-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f98c-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f98c-142">Example</span></span>  
 <span data-ttu-id="7f98c-143">Následující konfigurace přidá do vazby zabezpečení požadavky na dva typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="7f98c-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f98c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f98c-144">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7f98c-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7f98c-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)
- [<span data-ttu-id="7f98c-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="7f98c-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7f98c-147">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7f98c-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7f98c-148">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7f98c-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7f98c-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7f98c-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="7f98c-150">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7f98c-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7f98c-151">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="7f98c-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
