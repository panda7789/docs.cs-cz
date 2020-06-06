---
title: <add><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153097"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="92579-102">\<add>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="92579-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="92579-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="92579-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="92579-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="92579-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="92579-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92579-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92579-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="92579-106">Attributes and Elements</span></span>  
 <span data-ttu-id="92579-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="92579-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92579-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="92579-108">Attributes</span></span>  
  
|<span data-ttu-id="92579-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="92579-109">Attribute</span></span>|<span data-ttu-id="92579-110">Popis</span><span class="sxs-lookup"><span data-stu-id="92579-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92579-111">claimType</span><span class="sxs-lookup"><span data-stu-id="92579-111">claimType</span></span>|<span data-ttu-id="92579-112">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="92579-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="92579-113">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="92579-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="92579-114">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="92579-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="92579-115">Přepínač</span><span class="sxs-lookup"><span data-stu-id="92579-115">isOptional</span></span>|<span data-ttu-id="92579-116">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="92579-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="92579-117">Nastavte tento atribut na, `false` Pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="92579-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="92579-118">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="92579-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="92579-119">Pokud například požadujete, aby uživatel zadal své křestní jméno, příjmení a adresu, ale rozhodnete se, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="92579-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92579-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="92579-120">Child Elements</span></span>  
 <span data-ttu-id="92579-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="92579-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92579-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="92579-122">Parent Elements</span></span>  
  
|<span data-ttu-id="92579-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="92579-123">Element</span></span>|<span data-ttu-id="92579-124">Description</span><span class="sxs-lookup"><span data-stu-id="92579-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="92579-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="92579-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="92579-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="92579-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="92579-127">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="92579-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="92579-128">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="92579-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="92579-129">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="92579-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92579-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92579-130">Remarks</span></span>  
 <span data-ttu-id="92579-131">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="92579-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="92579-132">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="92579-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="92579-133">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="92579-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="92579-134">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="92579-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92579-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="92579-135">Example</span></span>  
 <span data-ttu-id="92579-136">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="92579-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92579-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="92579-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
