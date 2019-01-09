---
title: '&lt;add&gt; – &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 5d4f0cd71ab9bf69921704300018207c9f7af107
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145208"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="88d79-102">&lt;add&gt; – &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="88d79-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="88d79-103">Určuje typy požadovaných a volitelných deklarací, které se zobrazí ve federativním pověření.</span><span class="sxs-lookup"><span data-stu-id="88d79-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="88d79-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="88d79-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="88d79-105">\<system.serviceModel></span></span>  
<span data-ttu-id="88d79-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="88d79-106">\<bindings></span></span>  
<span data-ttu-id="88d79-107">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="88d79-107">\<customBinding></span></span>  
<span data-ttu-id="88d79-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="88d79-108">\<binding></span></span>  
<span data-ttu-id="88d79-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="88d79-109">\<security></span></span>  
<span data-ttu-id="88d79-110">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="88d79-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="88d79-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="88d79-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d79-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88d79-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88d79-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88d79-113">Attributes and Elements</span></span>  
 <span data-ttu-id="88d79-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88d79-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88d79-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="88d79-115">Attributes</span></span>  
  
|<span data-ttu-id="88d79-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="88d79-116">Attribute</span></span>|<span data-ttu-id="88d79-117">Popis</span><span class="sxs-lookup"><span data-stu-id="88d79-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88d79-118">Typ ClaimType</span><span class="sxs-lookup"><span data-stu-id="88d79-118">claimType</span></span>|<span data-ttu-id="88d79-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="88d79-120">Například k nákupu z webu produktu, uživatel musí poskytnout uvedenou platnou platební kartu s dostatečnou kreditního limitu.</span><span class="sxs-lookup"><span data-stu-id="88d79-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="88d79-121">Typ deklarace by platební karty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="88d79-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="88d79-122">Schedule</span><span class="sxs-lookup"><span data-stu-id="88d79-122">isOptional</span></span>|<span data-ttu-id="88d79-123">Logická hodnota určující, zda je pro volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="88d79-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="88d79-124">Tento atribut nastavte na `false` Pokud je požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="88d79-125">Tento atribut můžete použít, když služba vyzve k zadání některé informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="88d79-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="88d79-126">Například pokud vyžadujete, aby uživatel zadal své jméno, příjmení a adresu, ale rozhodnout, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="88d79-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88d79-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88d79-127">Child Elements</span></span>  
 <span data-ttu-id="88d79-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="88d79-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88d79-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88d79-129">Parent Elements</span></span>  
  
|<span data-ttu-id="88d79-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="88d79-130">Element</span></span>|<span data-ttu-id="88d79-131">Popis</span><span class="sxs-lookup"><span data-stu-id="88d79-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88d79-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="88d79-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="88d79-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="88d79-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="88d79-134">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="88d79-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="88d79-135">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="88d79-136">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="88d79-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88d79-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88d79-137">Remarks</span></span>  
 <span data-ttu-id="88d79-138">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="88d79-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="88d79-139">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="88d79-140">Tento požadavek je označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="88d79-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="88d79-141">Pokud pověření klienta žádosti od federovaných služby (například služba CardSpace), vloží požadavky na žádost o token (RequestSecurityToken) tak, aby federované služby může vydat přihlašovací údaje, které splňují požadavky na odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="88d79-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88d79-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="88d79-142">Example</span></span>  
 <span data-ttu-id="88d79-143">Následující konfigurace přidá do vazby zabezpečení požadavky na dva typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="88d79-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88d79-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="88d79-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="88d79-145">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="88d79-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="88d79-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="88d79-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="88d79-147">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="88d79-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="88d79-148">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="88d79-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="88d79-149">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="88d79-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="88d79-150">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="88d79-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="88d79-151">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="88d79-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
