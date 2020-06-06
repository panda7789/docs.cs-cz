---
title: <add> z <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153084"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="33381-102">\<add> z \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="33381-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="33381-103">Určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="33381-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="33381-104">Například služby stavují požadavky na příchozí přihlašovací údaje, které musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="33381-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="33381-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33381-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33381-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33381-106">Attributes and Elements</span></span>  
 <span data-ttu-id="33381-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33381-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33381-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="33381-108">Attributes</span></span>  
  
|<span data-ttu-id="33381-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="33381-109">Attribute</span></span>|<span data-ttu-id="33381-110">Popis</span><span class="sxs-lookup"><span data-stu-id="33381-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33381-111">claimType</span><span class="sxs-lookup"><span data-stu-id="33381-111">claimType</span></span>|<span data-ttu-id="33381-112">Identifikátor URI, který definuje typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="33381-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="33381-113">Pokud například chcete zakoupit produkt z webu, musí uživatel předložit platnou platební kartu s dostatečným limitem úvěru.</span><span class="sxs-lookup"><span data-stu-id="33381-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="33381-114">Typ deklarace by byl identifikátor URI pro platební kartu.</span><span class="sxs-lookup"><span data-stu-id="33381-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="33381-115">Přepínač</span><span class="sxs-lookup"><span data-stu-id="33381-115">isOptional</span></span>|<span data-ttu-id="33381-116">Logická hodnota, která určuje, zda se jedná o volitelnou deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="33381-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="33381-117">Nastavte tento atribut na, `false` Pokud je to požadovaná deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="33381-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="33381-118">Tento atribut můžete použít, pokud se služba zeptá na nějaké informace, ale nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="33381-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="33381-119">Pokud například požadujete, aby uživatel zadal své křestní jméno, příjmení a adresu, ale rozhodnete se, že telefonní číslo je volitelné.</span><span class="sxs-lookup"><span data-stu-id="33381-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33381-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33381-120">Child Elements</span></span>  
 <span data-ttu-id="33381-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="33381-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33381-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33381-122">Parent Elements</span></span>  
  
|<span data-ttu-id="33381-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="33381-123">Element</span></span>|<span data-ttu-id="33381-124">Description</span><span class="sxs-lookup"><span data-stu-id="33381-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="33381-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="33381-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="33381-126">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="33381-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="33381-127">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="33381-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="33381-128">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="33381-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33381-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33381-129">Remarks</span></span>  
 <span data-ttu-id="33381-130">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="33381-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="33381-131">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="33381-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="33381-132">Tento požadavek se projevuje v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="33381-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="33381-133">Když klient požádá o přihlašovací údaje od federované služby (například služby CardSpace), uloží požadavky do žádosti o token (RequestSecurityToken), aby mohla federační služba vystavovat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="33381-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33381-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="33381-134">Example</span></span>  
 <span data-ttu-id="33381-135">Následující konfigurace přidá do vazby zabezpečení dva požadavky typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="33381-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33381-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="33381-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="33381-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="33381-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33381-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="33381-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="33381-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="33381-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="33381-140">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="33381-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="33381-141">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="33381-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
