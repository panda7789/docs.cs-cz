---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988383"
---
# <a name="identity"></a><span data-ttu-id="2714b-101">\<> identity</span><span class="sxs-lookup"><span data-stu-id="2714b-101">\<identity></span></span>
<span data-ttu-id="2714b-102">Prvek identita umožňuje vývojáři klienta zadat v době návrhu očekávanou identitu služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="2714b-103">V procesu handshake mezi klientem a službou infrastruktura Windows Communication Foundation (WCF) zajistí, že identita očekávané služby bude odpovídat hodnotám tohoto prvku, a proto může být ověřena.</span><span class="sxs-lookup"><span data-stu-id="2714b-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="2714b-104">Další informace najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2714b-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2714b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2714b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2714b-106">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="2714b-106">\<client></span></span>  
<span data-ttu-id="2714b-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2714b-107">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2714b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2714b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2714b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2714b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2714b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2714b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2714b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2714b-111">Attributes</span></span>  
 <span data-ttu-id="2714b-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="2714b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2714b-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2714b-113">Child Elements</span></span>  
  
|<span data-ttu-id="2714b-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="2714b-114">Element</span></span>|<span data-ttu-id="2714b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2714b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2714b-116">certificate</span><span class="sxs-lookup"><span data-stu-id="2714b-116">certificate</span></span>|<span data-ttu-id="2714b-117">Určuje nastavení certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="2714b-117">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="2714b-118">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="2714b-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="2714b-119">Obsahuje atribut `encodedValue` , který je řetězec, který určuje hodnotu zakódovanou tímto certifikátem.</span><span class="sxs-lookup"><span data-stu-id="2714b-119">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="2714b-120">certificateReference</span><span class="sxs-lookup"><span data-stu-id="2714b-120">certificateReference</span></span>|<span data-ttu-id="2714b-121">Určuje nastavení pro ověřování certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="2714b-121">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="2714b-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="2714b-122">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="2714b-123">dns</span><span class="sxs-lookup"><span data-stu-id="2714b-123">dns</span></span>|<span data-ttu-id="2714b-124">Určuje DNS certifikátu X. 509, který se používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-124">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="2714b-125">Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="2714b-125">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="2714b-126">rsa</span><span class="sxs-lookup"><span data-stu-id="2714b-126">rsa</span></span>|<span data-ttu-id="2714b-127">Určuje hodnotu pole RSA certifikátu X. 509, která se používá k ověření služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="2714b-127">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="2714b-128">Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="2714b-128">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="2714b-129">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="2714b-129">servicePrincipalName</span></span>|<span data-ttu-id="2714b-130">Určuje identitu hlavního názvu serveru (SPN), což je hlavní název, který klient používá k jednoznačné identifikaci instance služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-130">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="2714b-131">Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="2714b-131">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="2714b-132">Tento prvek je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="2714b-132">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="2714b-133">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="2714b-133">userPrincipalName</span></span>|<span data-ttu-id="2714b-134">Určuje identitu hlavního názvu uživatele (UPN), což je typ přihlašovacího jména uživatele v síti.</span><span class="sxs-lookup"><span data-stu-id="2714b-134">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="2714b-135">Hlavní název uživatele se skládá z názvu uživatelského objektu používaného ve službě Active Directory, po kterém následuje symbol (\@) a pak obvykle nadřazená doména systému názvů domén.</span><span class="sxs-lookup"><span data-stu-id="2714b-135">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="2714b-136">Například Jan ve stromu domény Fabrikam.com může mít hlavní název [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="2714b-136">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="2714b-137">Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="2714b-137">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="2714b-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="2714b-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2714b-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2714b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2714b-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="2714b-140">Element</span></span>|<span data-ttu-id="2714b-141">Popis</span><span class="sxs-lookup"><span data-stu-id="2714b-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2714b-142">\<custom></span><span class="sxs-lookup"><span data-stu-id="2714b-142">\<custom></span></span>](custom.md)|<span data-ttu-id="2714b-143">Určuje vlastní překladač rovnocenných uzlů pro netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="2714b-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="2714b-144">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2714b-144">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="2714b-145">Nakonfiguruje koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-145">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="2714b-146">\<koncový bod > \<> klienta</span><span class="sxs-lookup"><span data-stu-id="2714b-146">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="2714b-147">Nakonfiguruje koncové body kanálu.</span><span class="sxs-lookup"><span data-stu-id="2714b-147">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="2714b-148">\<issuer></span><span class="sxs-lookup"><span data-stu-id="2714b-148">\<issuer></span></span>](issuer.md)|<span data-ttu-id="2714b-149">Určuje službu tokenů zabezpečení (STS) pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-149">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="2714b-150">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="2714b-150">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="2714b-151">Určuje koncový bod metadat pro službu tokenů zabezpečení (STS) federované služby.</span><span class="sxs-lookup"><span data-stu-id="2714b-151">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="2714b-152">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="2714b-152">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="2714b-153">Definuje parametry pro vydaný token ve vlastní vazbě.</span><span class="sxs-lookup"><span data-stu-id="2714b-153">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="2714b-154">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="2714b-154">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="2714b-155">Určuje místní službu tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="2714b-155">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2714b-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2714b-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="2714b-157">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="2714b-157">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2714b-158">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="2714b-158">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
