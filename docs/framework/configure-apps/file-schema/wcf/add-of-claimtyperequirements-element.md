---
title: <add><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920212"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="e060a-102">\<Přidat > \<prvku > claimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="e060a-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="e060a-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="e060a-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="e060a-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="e060a-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="e060a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e060a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e060a-106">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="e060a-106">\<bindings></span></span>  
<span data-ttu-id="e060a-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="e060a-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="e060a-108">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e060a-108">\<binding></span></span>  
<span data-ttu-id="e060a-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e060a-109">\<security></span></span>  
<span data-ttu-id="e060a-110">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="e060a-110">\<message></span></span>  
<span data-ttu-id="e060a-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e060a-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e060a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e060a-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e060a-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e060a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e060a-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e060a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e060a-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="e060a-115">Attributes</span></span>  
  
|<span data-ttu-id="e060a-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="e060a-116">Attribute</span></span>|<span data-ttu-id="e060a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e060a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e060a-118">claimType</span><span class="sxs-lookup"><span data-stu-id="e060a-118">claimType</span></span>|<span data-ttu-id="e060a-119">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="e060a-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="e060a-120">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="e060a-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="e060a-121">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="e060a-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="e060a-122">Přepínač</span><span class="sxs-lookup"><span data-stu-id="e060a-122">isOptional</span></span>|<span data-ttu-id="e060a-123">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="e060a-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="e060a-124">Nastavte tento atribut na `false` , pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e060a-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="e060a-125">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e060a-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="e060a-126">Pokud například požadujete, aby uživatel zadal své křestní jméno a příjmení, příjmení a adresu, ale rozhodne, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="e060a-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e060a-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e060a-127">Child Elements</span></span>  
 <span data-ttu-id="e060a-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="e060a-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e060a-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e060a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e060a-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="e060a-130">Element</span></span>|<span data-ttu-id="e060a-131">Popis</span><span class="sxs-lookup"><span data-stu-id="e060a-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e060a-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e060a-132">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="e060a-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="e060a-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e060a-134">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e060a-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e060a-135">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e060a-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e060a-136">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="e060a-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e060a-137">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="e060a-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e060a-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e060a-138">Remarks</span></span>  
 <span data-ttu-id="e060a-139">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e060a-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e060a-140">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="e060a-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e060a-141">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e060a-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="e060a-142">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e060a-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e060a-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="e060a-143">Example</span></span>  
 <span data-ttu-id="e060a-144">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e060a-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e060a-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e060a-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
