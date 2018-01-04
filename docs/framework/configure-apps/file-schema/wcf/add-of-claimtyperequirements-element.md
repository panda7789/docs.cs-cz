---
title: '&lt;add&gt; elementu &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a6a0cc78cad2ccbc8dca6097227ef22f45dbc63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="61a0b-102">&lt;add&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="61a0b-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="61a0b-103">Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="61a0b-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="61a0b-104">Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="61a0b-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="61a0b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="61a0b-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="61a0b-106">\<bindings></span></span>  
<span data-ttu-id="61a0b-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="61a0b-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="61a0b-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="61a0b-108">\<binding></span></span>  
<span data-ttu-id="61a0b-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="61a0b-109">\<security></span></span>  
<span data-ttu-id="61a0b-110">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="61a0b-110">\<message></span></span>  
<span data-ttu-id="61a0b-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="61a0b-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a0b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61a0b-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61a0b-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61a0b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="61a0b-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61a0b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61a0b-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="61a0b-115">Attributes</span></span>  
  
|<span data-ttu-id="61a0b-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="61a0b-116">Attribute</span></span>|<span data-ttu-id="61a0b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="61a0b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61a0b-118">Typ claimType</span><span class="sxs-lookup"><span data-stu-id="61a0b-118">claimType</span></span>|<span data-ttu-id="61a0b-119">Identifikátor URI, který definuje typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="61a0b-120">Například k nákupu produktu z webu, uživatel musí představovat platná platební karta úvěr dostatečná.</span><span class="sxs-lookup"><span data-stu-id="61a0b-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="61a0b-121">Typ deklarace by platební karty identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="61a0b-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="61a0b-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="61a0b-122">isOptional</span></span>|<span data-ttu-id="61a0b-123">Logická hodnota, která určuje, zda se pro volitelné deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="61a0b-124">Nastavte tento atribut `false` Pokud to není požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="61a0b-125">Tento atribut můžete použít při služby požádá o některé informace, ale není nutné.</span><span class="sxs-lookup"><span data-stu-id="61a0b-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="61a0b-126">Například pokud požadujete, aby uživatel zadal jejich křestní jméno, příjmení a adresa, ale rozhodnout, zda telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="61a0b-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61a0b-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61a0b-127">Child Elements</span></span>  
 <span data-ttu-id="61a0b-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="61a0b-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61a0b-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61a0b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="61a0b-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="61a0b-130">Element</span></span>|<span data-ttu-id="61a0b-131">Popis</span><span class="sxs-lookup"><span data-stu-id="61a0b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61a0b-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="61a0b-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="61a0b-133">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="61a0b-134">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="61a0b-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="61a0b-135">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="61a0b-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="61a0b-136">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="61a0b-137">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="61a0b-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61a0b-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61a0b-138">Remarks</span></span>  
 <span data-ttu-id="61a0b-139">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="61a0b-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="61a0b-140">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="61a0b-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="61a0b-141">Tento požadavek označované v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61a0b-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="61a0b-142">Pokud pověření klienta žádosti od federovaných služby (například CardSpace), vloží požadavků do (třída RequestSecurityToken) žádosti o token tak, aby federované služby můžete vydat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="61a0b-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a0b-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="61a0b-143">Example</span></span>  
 <span data-ttu-id="61a0b-144">Následující konfigurace přidá dva požadavky na typ deklarace identity do vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61a0b-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a0b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="61a0b-145">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
