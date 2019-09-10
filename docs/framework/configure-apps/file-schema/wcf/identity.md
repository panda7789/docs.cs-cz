---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855151"
---
# <a name="identity"></a><span data-ttu-id="e68af-101">\<> identity</span><span class="sxs-lookup"><span data-stu-id="e68af-101">\<identity></span></span>
<span data-ttu-id="e68af-102">Prvek identita umožňuje vývojáři klienta zadat v době návrhu očekávanou identitu služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="e68af-103">V procesu handshake mezi klientem a službou infrastruktura Windows Communication Foundation (WCF) zajistí, že identita očekávané služby bude odpovídat hodnotám tohoto prvku, a proto může být ověřena.</span><span class="sxs-lookup"><span data-stu-id="e68af-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="e68af-104">Další informace najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e68af-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="e68af-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e68af-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e68af-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e68af-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e68af-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="e68af-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="e68af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="e68af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="e68af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> identity**</span><span class="sxs-lookup"><span data-stu-id="e68af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e68af-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e68af-110">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e68af-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e68af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e68af-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e68af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e68af-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e68af-113">Attributes</span></span>  
 <span data-ttu-id="e68af-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e68af-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e68af-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e68af-115">Child Elements</span></span>  
  
|<span data-ttu-id="e68af-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="e68af-116">Element</span></span>|<span data-ttu-id="e68af-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e68af-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e68af-118">certificate</span><span class="sxs-lookup"><span data-stu-id="e68af-118">certificate</span></span>|<span data-ttu-id="e68af-119">Určuje nastavení certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="e68af-119">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="e68af-120">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="e68af-120">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="e68af-121">Obsahuje atribut `encodedValue` , který je řetězec, který určuje hodnotu zakódovanou tímto certifikátem.</span><span class="sxs-lookup"><span data-stu-id="e68af-121">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="e68af-122">certificateReference</span><span class="sxs-lookup"><span data-stu-id="e68af-122">certificateReference</span></span>|<span data-ttu-id="e68af-123">Určuje nastavení pro ověřování certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="e68af-123">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="e68af-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="e68af-124">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="e68af-125">dns</span><span class="sxs-lookup"><span data-stu-id="e68af-125">dns</span></span>|<span data-ttu-id="e68af-126">Určuje DNS certifikátu X. 509, který se používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-126">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="e68af-127">Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="e68af-127">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="e68af-128">rsa</span><span class="sxs-lookup"><span data-stu-id="e68af-128">rsa</span></span>|<span data-ttu-id="e68af-129">Určuje hodnotu pole RSA certifikátu X. 509, která se používá k ověření služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="e68af-129">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="e68af-130">Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="e68af-130">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="e68af-131">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="e68af-131">servicePrincipalName</span></span>|<span data-ttu-id="e68af-132">Určuje identitu hlavního názvu serveru (SPN), což je hlavní název, který klient používá k jednoznačné identifikaci instance služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-132">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="e68af-133">Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="e68af-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="e68af-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="e68af-134">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="e68af-135">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e68af-135">userPrincipalName</span></span>|<span data-ttu-id="e68af-136">Určuje identitu hlavního názvu uživatele (UPN), což je typ přihlašovacího jména uživatele v síti.</span><span class="sxs-lookup"><span data-stu-id="e68af-136">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="e68af-137">Hlavní název uživatele se skládá z názvu uživatelského objektu používaného ve službě Active Directory, po kterém následuje symbol (\@) a pak obvykle nadřazená doména systému názvů domén.</span><span class="sxs-lookup"><span data-stu-id="e68af-137">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="e68af-138">Například Jan ve stromu domény Fabrikam.com může mít hlavní název [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="e68af-138">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="e68af-139">Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="e68af-139">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="e68af-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="e68af-140">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e68af-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e68af-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e68af-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="e68af-142">Element</span></span>|<span data-ttu-id="e68af-143">Popis</span><span class="sxs-lookup"><span data-stu-id="e68af-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e68af-144">\<custom></span><span class="sxs-lookup"><span data-stu-id="e68af-144">\<custom></span></span>](custom.md)|<span data-ttu-id="e68af-145">Určuje vlastní překladač rovnocenných uzlů pro netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="e68af-145">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="e68af-146">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e68af-146">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="e68af-147">Nakonfiguruje koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-147">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="e68af-148">\<koncový bod > \<> klienta</span><span class="sxs-lookup"><span data-stu-id="e68af-148">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="e68af-149">Nakonfiguruje koncové body kanálu.</span><span class="sxs-lookup"><span data-stu-id="e68af-149">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="e68af-150">\<issuer></span><span class="sxs-lookup"><span data-stu-id="e68af-150">\<issuer></span></span>](issuer.md)|<span data-ttu-id="e68af-151">Určuje službu tokenů zabezpečení (STS) pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-151">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="e68af-152">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="e68af-152">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="e68af-153">Určuje koncový bod metadat pro službu tokenů zabezpečení (STS) federované služby.</span><span class="sxs-lookup"><span data-stu-id="e68af-153">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="e68af-154">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="e68af-154">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="e68af-155">Definuje parametry pro vydaný token ve vlastní vazbě.</span><span class="sxs-lookup"><span data-stu-id="e68af-155">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="e68af-156">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="e68af-156">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="e68af-157">Určuje místní službu tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="e68af-157">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e68af-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e68af-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="e68af-159">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e68af-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e68af-160">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="e68af-160">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
