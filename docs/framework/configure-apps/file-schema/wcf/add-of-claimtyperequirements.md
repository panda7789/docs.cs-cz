---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153084"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="5b74c-102">\<přidat> \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5b74c-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="5b74c-103">Určuje typy požadovaných a volitelných deklarací, u kterých se má zobrazit ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="5b74c-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="5b74c-104">Služby například uvádějí požadavky na příchozí pověření, která musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="5b74c-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="5b74c-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5b74c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5b74c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5b74c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<vlastní vazba>**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5b74c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**</span><span class="sxs-lookup"><span data-stu-id="5b74c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5b74c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bezpečnostní>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="5b74c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="5b74c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b74c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="5b74c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="5b74c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b74c-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b74c-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b74c-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b74c-115">Attributes and Elements</span></span>  
 <span data-ttu-id="5b74c-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b74c-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b74c-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b74c-117">Attributes</span></span>  
  
|<span data-ttu-id="5b74c-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="5b74c-118">Attribute</span></span>|<span data-ttu-id="5b74c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5b74c-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b74c-120">claimType</span><span class="sxs-lookup"><span data-stu-id="5b74c-120">claimType</span></span>|<span data-ttu-id="5b74c-121">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="5b74c-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="5b74c-122">Chcete-li například zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným úvěrovým limitem.</span><span class="sxs-lookup"><span data-stu-id="5b74c-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="5b74c-123">Typ deklarace by byl identifikátor URI platební karty.</span><span class="sxs-lookup"><span data-stu-id="5b74c-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="5b74c-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="5b74c-124">isOptional</span></span>|<span data-ttu-id="5b74c-125">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="5b74c-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="5b74c-126">Nastavte tento `false` atribut, pokud se jedná o požadovanou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="5b74c-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="5b74c-127">Tento atribut můžete použít, když služba požádá o některé informace, ale nevyžaduje je.</span><span class="sxs-lookup"><span data-stu-id="5b74c-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="5b74c-128">Pokud například požadujete, aby uživatel zadá své jméno, příjmení a adresu, ale rozhodnete, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="5b74c-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b74c-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b74c-129">Child Elements</span></span>  
 <span data-ttu-id="5b74c-130">Žádné.</span><span class="sxs-lookup"><span data-stu-id="5b74c-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b74c-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b74c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5b74c-132">Element</span><span class="sxs-lookup"><span data-stu-id="5b74c-132">Element</span></span>|<span data-ttu-id="5b74c-133">Popis</span><span class="sxs-lookup"><span data-stu-id="5b74c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b74c-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5b74c-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="5b74c-135">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="5b74c-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="5b74c-136">Ve federovaném scénáři služby uvedou požadavky na příchozí pověření.</span><span class="sxs-lookup"><span data-stu-id="5b74c-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5b74c-137">Například příchozí pověření musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="5b74c-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5b74c-138">Každý prvek v této kolekci určuje typy povinných a volitelných deklarací, které se mají zobrazit ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="5b74c-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b74c-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b74c-139">Remarks</span></span>  
 <span data-ttu-id="5b74c-140">Ve federovaném scénáři služby uvedou požadavky na příchozí pověření.</span><span class="sxs-lookup"><span data-stu-id="5b74c-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5b74c-141">Například příchozí pověření musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="5b74c-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5b74c-142">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5b74c-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="5b74c-143">Když klient požaduje pověření z federované služby (například CardSpace), vloží požadavky do požadavku na token (RequestSecurityToken) tak, aby federovaná služba může vydat pověření, která splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="5b74c-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b74c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b74c-144">Example</span></span>  
 <span data-ttu-id="5b74c-145">Následující konfigurace přidá dva požadavky na typ deklarace deklarace zabezpečení do vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5b74c-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b74c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b74c-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5b74c-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5b74c-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="5b74c-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="5b74c-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5b74c-149">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5b74c-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5b74c-150">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5b74c-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5b74c-151">\<vlastní vazba></span><span class="sxs-lookup"><span data-stu-id="5b74c-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="5b74c-152">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5b74c-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="5b74c-153">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="5b74c-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
