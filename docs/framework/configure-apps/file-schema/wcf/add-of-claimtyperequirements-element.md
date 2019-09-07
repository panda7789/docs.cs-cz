---
title: <add><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 9c56cccd7a6f72a701e4b8652afecc2361e6218a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400678"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="7c203-102">\<Přidat > \<prvku > claimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="7c203-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="7c203-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="7c203-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="7c203-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="7c203-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="7c203-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c203-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7c203-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7c203-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="7c203-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="7c203-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7c203-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="7c203-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="7c203-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="7c203-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="7c203-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="7c203-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="7c203-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c203-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c203-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c203-115">Attributes and Elements</span></span>  
 <span data-ttu-id="7c203-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c203-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c203-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c203-117">Attributes</span></span>  
  
|<span data-ttu-id="7c203-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c203-118">Attribute</span></span>|<span data-ttu-id="7c203-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7c203-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c203-120">claimType</span><span class="sxs-lookup"><span data-stu-id="7c203-120">claimType</span></span>|<span data-ttu-id="7c203-121">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="7c203-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="7c203-122">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="7c203-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="7c203-123">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="7c203-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="7c203-124">Přepínač</span><span class="sxs-lookup"><span data-stu-id="7c203-124">isOptional</span></span>|<span data-ttu-id="7c203-125">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="7c203-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="7c203-126">Nastavte tento atribut na `false` , pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="7c203-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="7c203-127">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7c203-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="7c203-128">Pokud například požadujete, aby uživatel zadal své křestní jméno a příjmení, příjmení a adresu, ale rozhodne, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="7c203-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c203-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c203-129">Child Elements</span></span>  
 <span data-ttu-id="7c203-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c203-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c203-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c203-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7c203-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c203-132">Element</span></span>|<span data-ttu-id="7c203-133">Popis</span><span class="sxs-lookup"><span data-stu-id="7c203-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c203-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7c203-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="7c203-135">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="7c203-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="7c203-136">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7c203-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="7c203-137">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="7c203-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7c203-138">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="7c203-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7c203-139">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="7c203-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c203-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c203-140">Remarks</span></span>  
 <span data-ttu-id="7c203-141">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="7c203-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7c203-142">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="7c203-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7c203-143">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c203-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="7c203-144">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7c203-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c203-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c203-145">Example</span></span>  
 <span data-ttu-id="7c203-146">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="7c203-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c203-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c203-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
