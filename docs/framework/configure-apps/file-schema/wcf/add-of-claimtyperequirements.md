---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 7e7f0eac41e69e959aa6c4f8f3cfb488d4ea2917
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926797"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="aaf0c-102">\<add> of \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="aaf0c-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="aaf0c-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="aaf0c-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="aaf0c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aaf0c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="aaf0c-106">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="aaf0c-106">\<bindings></span></span>  
<span data-ttu-id="aaf0c-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aaf0c-107">\<customBinding></span></span>  
<span data-ttu-id="aaf0c-108">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="aaf0c-108">\<binding></span></span>  
<span data-ttu-id="aaf0c-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aaf0c-109">\<security></span></span>  
<span data-ttu-id="aaf0c-110">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="aaf0c-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="aaf0c-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="aaf0c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf0c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaf0c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaf0c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aaf0c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="aaf0c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaf0c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="aaf0c-115">Attributes</span></span>  
  
|<span data-ttu-id="aaf0c-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="aaf0c-116">Attribute</span></span>|<span data-ttu-id="aaf0c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="aaf0c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaf0c-118">claimType</span><span class="sxs-lookup"><span data-stu-id="aaf0c-118">claimType</span></span>|<span data-ttu-id="aaf0c-119">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="aaf0c-120">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="aaf0c-121">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="aaf0c-122">Přepínač</span><span class="sxs-lookup"><span data-stu-id="aaf0c-122">isOptional</span></span>|<span data-ttu-id="aaf0c-123">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="aaf0c-124">Nastavte tento atribut na `false` , pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="aaf0c-125">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="aaf0c-126">Pokud například požadujete, aby uživatel zadal své křestní jméno a příjmení, příjmení a adresu, ale rozhodne, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaf0c-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aaf0c-127">Child Elements</span></span>  
 <span data-ttu-id="aaf0c-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="aaf0c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaf0c-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aaf0c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="aaf0c-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="aaf0c-130">Element</span></span>|<span data-ttu-id="aaf0c-131">Popis</span><span class="sxs-lookup"><span data-stu-id="aaf0c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaf0c-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="aaf0c-132">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="aaf0c-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="aaf0c-134">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="aaf0c-135">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="aaf0c-136">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaf0c-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaf0c-137">Remarks</span></span>  
 <span data-ttu-id="aaf0c-138">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="aaf0c-139">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="aaf0c-140">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="aaf0c-141">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf0c-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="aaf0c-142">Example</span></span>  
 <span data-ttu-id="aaf0c-143">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="aaf0c-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aaf0c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaf0c-144">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="aaf0c-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="aaf0c-145">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="aaf0c-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="aaf0c-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aaf0c-147">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="aaf0c-147">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="aaf0c-148">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="aaf0c-148">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="aaf0c-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="aaf0c-149">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="aaf0c-150">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="aaf0c-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="aaf0c-151">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="aaf0c-151">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
