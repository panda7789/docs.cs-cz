---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855151"
---
# \<identity>
<span data-ttu-id="3db41-101">Prvek identita umožňuje vývojáři klienta zadat v době návrhu očekávanou identitu služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="3db41-102">V procesu handshake mezi klientem a službou infrastruktura Windows Communication Foundation (WCF) zajistí, že identita očekávané služby bude odpovídat hodnotám tohoto prvku, a proto může být ověřena.</span><span class="sxs-lookup"><span data-stu-id="3db41-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="3db41-103">Další informace najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3db41-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="3db41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3db41-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3db41-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3db41-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3db41-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3db41-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3db41-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3db41-107">Attributes</span></span>  
 <span data-ttu-id="3db41-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3db41-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3db41-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3db41-109">Child Elements</span></span>  
  
|<span data-ttu-id="3db41-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="3db41-110">Element</span></span>|<span data-ttu-id="3db41-111">Description</span><span class="sxs-lookup"><span data-stu-id="3db41-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3db41-112">certifikát</span><span class="sxs-lookup"><span data-stu-id="3db41-112">certificate</span></span>|<span data-ttu-id="3db41-113">Určuje nastavení certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="3db41-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="3db41-114">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="3db41-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="3db41-115">Obsahuje atribut, `encodedValue` který je řetězec, který určuje hodnotu zakódovanou tímto certifikátem.</span><span class="sxs-lookup"><span data-stu-id="3db41-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="3db41-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="3db41-116">certificateReference</span></span>|<span data-ttu-id="3db41-117">Určuje nastavení pro ověřování certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="3db41-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="3db41-118">Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="3db41-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="3db41-119">dns</span><span class="sxs-lookup"><span data-stu-id="3db41-119">dns</span></span>|<span data-ttu-id="3db41-120">Určuje DNS certifikátu X. 509, který se používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="3db41-121">Tento element obsahuje atribut, `value` který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="3db41-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="3db41-122">rsa</span><span class="sxs-lookup"><span data-stu-id="3db41-122">rsa</span></span>|<span data-ttu-id="3db41-123">Určuje hodnotu pole RSA certifikátu X. 509, která se používá k ověření služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="3db41-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="3db41-124">Tento element obsahuje atribut, `value` který je řetězec, a obsahuje skutečnou identitu.</span><span class="sxs-lookup"><span data-stu-id="3db41-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="3db41-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="3db41-125">servicePrincipalName</span></span>|<span data-ttu-id="3db41-126">Určuje identitu hlavního názvu serveru (SPN), což je hlavní název, který klient používá k jednoznačné identifikaci instance služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="3db41-127">Tento prvek obsahuje atribut, `value` který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="3db41-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="3db41-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="3db41-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="3db41-129">userPrincipalName (Hlavní název uživatele)</span><span class="sxs-lookup"><span data-stu-id="3db41-129">userPrincipalName</span></span>|<span data-ttu-id="3db41-130">Určuje identitu hlavního názvu uživatele (UPN), což je typ přihlašovacího jména uživatele v síti.</span><span class="sxs-lookup"><span data-stu-id="3db41-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="3db41-131">Hlavní název uživatele se skládá z názvu uživatelského objektu používaného ve službě Active Directory, po kterém následuje symbol ( \@ ) a pak obvykle nadřazená doména systému názvů domén.</span><span class="sxs-lookup"><span data-stu-id="3db41-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="3db41-132">Například Jan ve stromu domény Fabrikam.com může mít hlavní název uživatele (UPN) [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="3db41-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="3db41-133">Tento prvek obsahuje atribut, `value` který je řetězec, a obsahuje skutečný hlavní název.</span><span class="sxs-lookup"><span data-stu-id="3db41-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="3db41-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="3db41-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3db41-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3db41-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3db41-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="3db41-136">Element</span></span>|<span data-ttu-id="3db41-137">Description</span><span class="sxs-lookup"><span data-stu-id="3db41-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="3db41-138">Určuje vlastní překladač rovnocenných uzlů pro netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="3db41-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="3db41-139">Nakonfiguruje koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="3db41-140">\<endpoint>tohoto\<client></span><span class="sxs-lookup"><span data-stu-id="3db41-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="3db41-141">Nakonfiguruje koncové body kanálu.</span><span class="sxs-lookup"><span data-stu-id="3db41-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="3db41-142">Určuje službu tokenů zabezpečení (STS) pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="3db41-143">Určuje koncový bod metadat pro službu tokenů zabezpečení (STS) federované služby.</span><span class="sxs-lookup"><span data-stu-id="3db41-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="3db41-144">Definuje parametry pro vydaný token ve vlastní vazbě.</span><span class="sxs-lookup"><span data-stu-id="3db41-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="3db41-145">Určuje místní službu tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="3db41-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3db41-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="3db41-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="3db41-147">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="3db41-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3db41-148">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="3db41-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
