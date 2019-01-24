---
title: '&lt;add&gt; elementu &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: fb5e723f6cff9f6e573a45a1dabe008beb9399e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687310"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="6b3ad-102">&lt;add&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="6b3ad-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="6b3ad-103">Určuje typy požadovaných a volitelných deklarací, které se zobrazí ve federativním pověření.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="6b3ad-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="6b3ad-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b3ad-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b3ad-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6b3ad-106">\<bindings></span></span>  
<span data-ttu-id="6b3ad-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="6b3ad-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="6b3ad-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6b3ad-108">\<binding></span></span>  
<span data-ttu-id="6b3ad-109">\<security></span><span class="sxs-lookup"><span data-stu-id="6b3ad-109">\<security></span></span>  
<span data-ttu-id="6b3ad-110">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="6b3ad-110">\<message></span></span>  
<span data-ttu-id="6b3ad-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="6b3ad-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3ad-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b3ad-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b3ad-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b3ad-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6b3ad-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b3ad-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b3ad-115">Attributes</span></span>  
  
|<span data-ttu-id="6b3ad-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b3ad-116">Attribute</span></span>|<span data-ttu-id="6b3ad-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6b3ad-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b3ad-118">claimType</span><span class="sxs-lookup"><span data-stu-id="6b3ad-118">claimType</span></span>|<span data-ttu-id="6b3ad-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="6b3ad-120">Například k nákupu z webu produktu, uživatel musí poskytnout uvedenou platnou platební kartu s dostatečnou kreditního limitu.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="6b3ad-121">Typ deklarace by platební karty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="6b3ad-122">Schedule</span><span class="sxs-lookup"><span data-stu-id="6b3ad-122">isOptional</span></span>|<span data-ttu-id="6b3ad-123">Logická hodnota určující, zda je pro volitelnou deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="6b3ad-124">Tento atribut nastavte na `false` Pokud je požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="6b3ad-125">Tento atribut můžete použít, když služba vyzve k zadání některé informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="6b3ad-126">Například pokud vyžadujete, aby uživatel zadal své jméno, příjmení a adresu, ale rozhodnout, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b3ad-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b3ad-127">Child Elements</span></span>  
 <span data-ttu-id="6b3ad-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="6b3ad-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b3ad-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b3ad-129">Parent Elements</span></span>  
  
|<span data-ttu-id="6b3ad-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b3ad-130">Element</span></span>|<span data-ttu-id="6b3ad-131">Popis</span><span class="sxs-lookup"><span data-stu-id="6b3ad-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b3ad-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="6b3ad-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="6b3ad-133">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="6b3ad-134">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="6b3ad-135">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6b3ad-136">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6b3ad-137">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b3ad-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b3ad-138">Remarks</span></span>  
 <span data-ttu-id="6b3ad-139">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6b3ad-140">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6b3ad-141">Tento požadavek je označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="6b3ad-142">Pokud pověření klienta žádosti od federovaných služby (například služba CardSpace), vloží požadavky na žádost o token (RequestSecurityToken) tak, aby federované služby může vydat přihlašovací údaje, které splňují požadavky na odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b3ad-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b3ad-143">Example</span></span>  
 <span data-ttu-id="6b3ad-144">Následující konfigurace přidá do vazby zabezpečení požadavky na dva typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b3ad-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b3ad-145">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
