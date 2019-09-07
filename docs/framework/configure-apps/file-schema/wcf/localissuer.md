---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397865"
---
# <a name="localissuer"></a><span data-ttu-id="34917-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="34917-101">\<localIssuer></span></span>
<span data-ttu-id="34917-102">Určuje adresu a vazbu místního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="34917-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="34917-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34917-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34917-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="34917-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="34917-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34917-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="34917-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34917-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="34917-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="34917-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="34917-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="34917-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="34917-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Třídy IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="34917-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="34917-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localIssuer >**</span><span class="sxs-lookup"><span data-stu-id="34917-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34917-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34917-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34917-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34917-112">Attributes and Elements</span></span>  
 <span data-ttu-id="34917-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34917-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34917-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="34917-114">Attributes</span></span>  
  
|<span data-ttu-id="34917-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="34917-115">Attribute</span></span>|<span data-ttu-id="34917-116">Popis</span><span class="sxs-lookup"><span data-stu-id="34917-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34917-117">adresa</span><span class="sxs-lookup"><span data-stu-id="34917-117">address</span></span>|<span data-ttu-id="34917-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="34917-118">Required string.</span></span> <span data-ttu-id="34917-119">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="34917-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="34917-120">vazba</span><span class="sxs-lookup"><span data-stu-id="34917-120">binding</span></span>|<span data-ttu-id="34917-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="34917-121">Optional string.</span></span> <span data-ttu-id="34917-122">Jedna z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="34917-122">One of the system-provided bindings.</span></span> <span data-ttu-id="34917-123">Seznam najdete v tématu [vazby poskytované systémem](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="34917-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="34917-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="34917-124">bindingConfiguration</span></span>|<span data-ttu-id="34917-125">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="34917-125">Optional string.</span></span> <span data-ttu-id="34917-126">Určuje konfiguraci vazby nalezenou v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="34917-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34917-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34917-127">Child Elements</span></span>  
  
|<span data-ttu-id="34917-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="34917-128">Element</span></span>|<span data-ttu-id="34917-129">Popis</span><span class="sxs-lookup"><span data-stu-id="34917-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34917-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="34917-130">\<identity></span></span>](identity.md)|<span data-ttu-id="34917-131">Určuje informace o identitě místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="34917-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="34917-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="34917-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="34917-133">Kolekce hlaviček adres, které jsou požadovány pro správné adresování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="34917-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="34917-134">K přidání záhlaví do `add` této kolekce můžete použít klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34917-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34917-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34917-135">Parent Elements</span></span>  
  
|<span data-ttu-id="34917-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="34917-136">Element</span></span>|<span data-ttu-id="34917-137">Popis</span><span class="sxs-lookup"><span data-stu-id="34917-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34917-138">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="34917-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="34917-139">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="34917-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34917-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34917-140">Remarks</span></span>  
 <span data-ttu-id="34917-141">Při získávání vystaveného tokenu ze služby tokenu zabezpečení (STS) musí být klientská aplikace nakonfigurovaná s adresou a vazbou, která se má použít ke komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="34917-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="34917-142">Pokud neposkytuje adresu URL pro službu tokenu zabezpečení, nebo pokud je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` adresa vystavitele federované vazby nebo `null`, kanál Windows Communication Foundation (WCF) klienta používá hodnoty určené parametrem <xref:System.ServiceModel.WSFederationHttpBinding> `address` a`binding` ke komunikaci se službou STS pro získání vydaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="34917-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="34917-143">Další informace o konfiguraci místního vystavitele najdete v [tématu Postup: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="34917-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34917-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="34917-144">Example</span></span>  
 <span data-ttu-id="34917-145">V následujícím příkladu jsou nastaveny `address`atributy `binding` `bindingConfiguration` , a elementu. `localIssuer`</span><span class="sxs-lookup"><span data-stu-id="34917-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34917-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34917-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="34917-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="34917-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="34917-148">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="34917-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="34917-149">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="34917-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="34917-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="34917-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="34917-151">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="34917-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="34917-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="34917-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="34917-153">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="34917-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="34917-154">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="34917-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="34917-155">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="34917-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
