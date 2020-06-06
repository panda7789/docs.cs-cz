---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397865"
---
# \<localIssuer>
<span data-ttu-id="bcc24-101">Určuje adresu a vazbu místního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bcc24-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="bcc24-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcc24-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcc24-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bcc24-103">Attributes and Elements</span></span>  
 <span data-ttu-id="bcc24-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bcc24-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcc24-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="bcc24-105">Attributes</span></span>  
  
|<span data-ttu-id="bcc24-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="bcc24-106">Attribute</span></span>|<span data-ttu-id="bcc24-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bcc24-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcc24-108">adresa</span><span class="sxs-lookup"><span data-stu-id="bcc24-108">address</span></span>|<span data-ttu-id="bcc24-109">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="bcc24-109">Required string.</span></span> <span data-ttu-id="bcc24-110">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="bcc24-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="bcc24-111">vazba</span><span class="sxs-lookup"><span data-stu-id="bcc24-111">binding</span></span>|<span data-ttu-id="bcc24-112">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="bcc24-112">Optional string.</span></span> <span data-ttu-id="bcc24-113">Jedna z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="bcc24-113">One of the system-provided bindings.</span></span> <span data-ttu-id="bcc24-114">Seznam najdete v tématu [vazby poskytované systémem](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="bcc24-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="bcc24-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcc24-115">bindingConfiguration</span></span>|<span data-ttu-id="bcc24-116">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="bcc24-116">Optional string.</span></span> <span data-ttu-id="bcc24-117">Určuje konfiguraci vazby nalezenou v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="bcc24-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcc24-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bcc24-118">Child Elements</span></span>  
  
|<span data-ttu-id="bcc24-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="bcc24-119">Element</span></span>|<span data-ttu-id="bcc24-120">Description</span><span class="sxs-lookup"><span data-stu-id="bcc24-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="bcc24-121">Určuje informace o identitě místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="bcc24-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="bcc24-122">Kolekce hlaviček adres, které jsou požadovány pro správné adresování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="bcc24-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="bcc24-123">K `add` Přidání záhlaví do této kolekce můžete použít klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="bcc24-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcc24-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bcc24-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bcc24-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="bcc24-125">Element</span></span>|<span data-ttu-id="bcc24-126">Description</span><span class="sxs-lookup"><span data-stu-id="bcc24-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="bcc24-127">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="bcc24-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc24-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcc24-128">Remarks</span></span>  
 <span data-ttu-id="bcc24-129">Při získávání vystaveného tokenu ze služby tokenu zabezpečení (STS) musí být klientská aplikace nakonfigurovaná s adresou a vazbou, která se má použít ke komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="bcc24-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="bcc24-130">Pokud neposkytuje <xref:System.ServiceModel.WSFederationHttpBinding> adresu URL pro službu tokenu zabezpečení, nebo pokud je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null` , kanál Windows Communication Foundation (WCF) klienta používá hodnoty určené nástrojem `address` a `binding` ke komunikaci se službou STS za účelem získání vydaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="bcc24-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="bcc24-131">Další informace o konfiguraci místního vystavitele najdete v tématu [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="bcc24-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc24-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc24-132">Example</span></span>  
 <span data-ttu-id="bcc24-133">V následujícím příkladu jsou nastaveny `address` `binding` atributy, a `bindingConfiguration` `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="bcc24-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="bcc24-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcc24-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="bcc24-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bcc24-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bcc24-136">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="bcc24-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="bcc24-137">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="bcc24-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bcc24-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bcc24-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bcc24-139">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="bcc24-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bcc24-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bcc24-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bcc24-141">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="bcc24-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="bcc24-142">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="bcc24-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="bcc24-143">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="bcc24-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
