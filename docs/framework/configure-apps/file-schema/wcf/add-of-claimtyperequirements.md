---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 53da9dacbd3277bd8b608296a1515e3da7296f1c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398373"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="506d9-102">\<add> of \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="506d9-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="506d9-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="506d9-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="506d9-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="506d9-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="506d9-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="506d9-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="506d9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="506d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="506d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="506d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="506d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="506d9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="506d9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="506d9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="506d9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="506d9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506d9-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="506d9-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="506d9-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="506d9-115">Attributes and Elements</span></span>  
 <span data-ttu-id="506d9-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="506d9-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="506d9-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="506d9-117">Attributes</span></span>  
  
|<span data-ttu-id="506d9-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="506d9-118">Attribute</span></span>|<span data-ttu-id="506d9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="506d9-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="506d9-120">claimType</span><span class="sxs-lookup"><span data-stu-id="506d9-120">claimType</span></span>|<span data-ttu-id="506d9-121">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="506d9-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="506d9-122">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="506d9-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="506d9-123">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="506d9-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="506d9-124">Přepínač</span><span class="sxs-lookup"><span data-stu-id="506d9-124">isOptional</span></span>|<span data-ttu-id="506d9-125">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="506d9-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="506d9-126">Nastavte tento atribut na `false` , pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="506d9-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="506d9-127">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="506d9-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="506d9-128">Pokud například požadujete, aby uživatel zadal své křestní jméno a příjmení, příjmení a adresu, ale rozhodne, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="506d9-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="506d9-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="506d9-129">Child Elements</span></span>  
 <span data-ttu-id="506d9-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="506d9-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="506d9-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="506d9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="506d9-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="506d9-132">Element</span></span>|<span data-ttu-id="506d9-133">Popis</span><span class="sxs-lookup"><span data-stu-id="506d9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="506d9-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="506d9-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="506d9-135">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="506d9-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="506d9-136">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="506d9-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="506d9-137">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="506d9-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="506d9-138">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="506d9-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="506d9-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="506d9-139">Remarks</span></span>  
 <span data-ttu-id="506d9-140">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="506d9-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="506d9-141">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="506d9-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="506d9-142">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="506d9-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="506d9-143">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="506d9-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="506d9-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="506d9-144">Example</span></span>  
 <span data-ttu-id="506d9-145">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="506d9-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="506d9-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="506d9-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="506d9-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="506d9-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="506d9-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="506d9-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="506d9-149">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="506d9-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="506d9-150">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="506d9-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="506d9-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="506d9-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="506d9-152">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="506d9-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="506d9-153">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="506d9-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
