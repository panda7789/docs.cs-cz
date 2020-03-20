---
title: <add><claimTypeRequirements> prvku
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153097"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="9325d-102">\<přidat> \<prvku claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9325d-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="9325d-103">Určuje typy požadovaných a volitelných deklarací, u kterých se má zobrazit ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="9325d-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="9325d-104">Služby například uvádějí požadavky na příchozí pověření, která musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="9325d-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="9325d-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9325d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9325d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9325d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="9325d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**</span><span class="sxs-lookup"><span data-stu-id="9325d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9325d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bezpečnostní>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="9325d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zpráv**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="9325d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="9325d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="9325d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="9325d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9325d-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9325d-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9325d-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9325d-115">Attributes and Elements</span></span>  
 <span data-ttu-id="9325d-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9325d-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9325d-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="9325d-117">Attributes</span></span>  
  
|<span data-ttu-id="9325d-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="9325d-118">Attribute</span></span>|<span data-ttu-id="9325d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9325d-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9325d-120">claimType</span><span class="sxs-lookup"><span data-stu-id="9325d-120">claimType</span></span>|<span data-ttu-id="9325d-121">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="9325d-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="9325d-122">Chcete-li například zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným úvěrovým limitem.</span><span class="sxs-lookup"><span data-stu-id="9325d-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="9325d-123">Typ deklarace by byl identifikátor URI platební karty.</span><span class="sxs-lookup"><span data-stu-id="9325d-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="9325d-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="9325d-124">isOptional</span></span>|<span data-ttu-id="9325d-125">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="9325d-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="9325d-126">Nastavte tento `false` atribut, pokud se jedná o požadovanou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="9325d-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="9325d-127">Tento atribut můžete použít, když služba požádá o některé informace, ale nevyžaduje je.</span><span class="sxs-lookup"><span data-stu-id="9325d-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="9325d-128">Pokud například požadujete, aby uživatel zadá své jméno, příjmení a adresu, ale rozhodnete, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="9325d-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9325d-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9325d-129">Child Elements</span></span>  
 <span data-ttu-id="9325d-130">Žádné.</span><span class="sxs-lookup"><span data-stu-id="9325d-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9325d-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9325d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9325d-132">Element</span><span class="sxs-lookup"><span data-stu-id="9325d-132">Element</span></span>|<span data-ttu-id="9325d-133">Popis</span><span class="sxs-lookup"><span data-stu-id="9325d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9325d-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9325d-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="9325d-135">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="9325d-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="9325d-136">Každý prvek je <xref:System.ServiceModel.Configuration.ClaimTypeElement>typu .</span><span class="sxs-lookup"><span data-stu-id="9325d-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="9325d-137">Ve federovaném scénáři služby uvedou požadavky na příchozí pověření.</span><span class="sxs-lookup"><span data-stu-id="9325d-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9325d-138">Například příchozí pověření musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="9325d-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9325d-139">Každý prvek v této kolekci určuje typy povinných a volitelných deklarací, které se mají zobrazit ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="9325d-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9325d-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9325d-140">Remarks</span></span>  
 <span data-ttu-id="9325d-141">Ve federovaném scénáři služby uvedou požadavky na příchozí pověření.</span><span class="sxs-lookup"><span data-stu-id="9325d-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9325d-142">Například příchozí pověření musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="9325d-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9325d-143">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9325d-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="9325d-144">Když klient požaduje pověření z federované služby (například CardSpace), vloží požadavky do požadavku na token (RequestSecurityToken) tak, aby federovaná služba může vydat pověření, která splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9325d-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9325d-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="9325d-145">Example</span></span>  
 <span data-ttu-id="9325d-146">Následující konfigurace přidá dva požadavky na typ deklarace deklarace zabezpečení do vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9325d-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9325d-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="9325d-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
