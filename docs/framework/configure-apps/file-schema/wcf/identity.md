---
title: '&lt;Identity&gt;'
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 9cfd1d6cc7c278fd7e95c13df0a6f801cfabbc33
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749163"
---
# <a name="ltidentitygt"></a><span data-ttu-id="d067d-102">&lt;Identity&gt;</span><span class="sxs-lookup"><span data-stu-id="d067d-102">&lt;identity&gt;</span></span>
<span data-ttu-id="d067d-103">Prvek identity umožňuje vývojáři klienta zadejte v době návrhu očekávaný identitu služby.</span><span class="sxs-lookup"><span data-stu-id="d067d-103">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="d067d-104">V procesu mezi klientem a službou infrastrukturu Windows Communication Foundation (WCF) zajistí, že identita očekávanou službu shody hodnoty tohoto elementu a proto může být ověřen.</span><span class="sxs-lookup"><span data-stu-id="d067d-104">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="d067d-105">Další informace najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d067d-105">For more information, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="d067d-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d067d-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="d067d-107">\<klient ></span><span class="sxs-lookup"><span data-stu-id="d067d-107">\<client></span></span>  
<span data-ttu-id="d067d-108">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="d067d-108">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d067d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d067d-109">Syntax</span></span>  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d067d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d067d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d067d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d067d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d067d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d067d-112">Attributes</span></span>  
 <span data-ttu-id="d067d-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="d067d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d067d-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d067d-114">Child Elements</span></span>  
  
|<span data-ttu-id="d067d-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="d067d-115">Element</span></span>|<span data-ttu-id="d067d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d067d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d067d-117">certificate</span><span class="sxs-lookup"><span data-stu-id="d067d-117">certificate</span></span>|<span data-ttu-id="d067d-118">Určuje nastavení certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="d067d-118">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="d067d-119">Tento element je typu <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="d067d-119">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="d067d-120">Obsahuje atribut `encodedValue` tedy řetězec, který určuje hodnotu kódovaný tímto certifikátem.</span><span class="sxs-lookup"><span data-stu-id="d067d-120">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="d067d-121">certificateReference</span><span class="sxs-lookup"><span data-stu-id="d067d-121">certificateReference</span></span>|<span data-ttu-id="d067d-122">Určuje nastavení pro ověření certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="d067d-122">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="d067d-123">Tento element je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="d067d-123">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="d067d-124">dns</span><span class="sxs-lookup"><span data-stu-id="d067d-124">dns</span></span>|<span data-ttu-id="d067d-125">Určuje certifikátu X.509. certifikát použitý k ověření služby DNS.</span><span class="sxs-lookup"><span data-stu-id="d067d-125">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="d067d-126">Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné identitu.</span><span class="sxs-lookup"><span data-stu-id="d067d-126">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="d067d-127">rsa</span><span class="sxs-lookup"><span data-stu-id="d067d-127">rsa</span></span>|<span data-ttu-id="d067d-128">Určuje hodnotu pole RSA certifikátu X.509. certifikát použitý k ověření služby klienta.</span><span class="sxs-lookup"><span data-stu-id="d067d-128">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="d067d-129">Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné identity</span><span class="sxs-lookup"><span data-stu-id="d067d-129">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="d067d-130">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="d067d-130">servicePrincipalName</span></span>|<span data-ttu-id="d067d-131">Určuje identitu serveru hlavní název (SPN), což je hlavní název klient používá k jedinečné identifikaci instance služby.</span><span class="sxs-lookup"><span data-stu-id="d067d-131">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="d067d-132">Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné hlavní název.</span><span class="sxs-lookup"><span data-stu-id="d067d-132">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="d067d-133">Tento element je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="d067d-133">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="d067d-134">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="d067d-134">userPrincipalName</span></span>|<span data-ttu-id="d067d-135">Určuje identitu hlavní název (UPN) uživatele, což je typ názvu přihlášení uživatele v síti.</span><span class="sxs-lookup"><span data-stu-id="d067d-135">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="d067d-136">Hlavní název uživatele se skládá z názvu objektu uživatele ve službě Active Directory, za nímž následuje použít v symbolu (@) a potom obvykle Domain Name System nadřazené domény.</span><span class="sxs-lookup"><span data-stu-id="d067d-136">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="d067d-137">Například Jeff v stromu domény Fabrikam.com může mít hlavní název uživatele [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné hlavní název.</span><span class="sxs-lookup"><span data-stu-id="d067d-137">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).  This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="d067d-138">Tento element je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="d067d-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d067d-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d067d-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d067d-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="d067d-140">Element</span></span>|<span data-ttu-id="d067d-141">Popis</span><span class="sxs-lookup"><span data-stu-id="d067d-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d067d-142">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="d067d-142">\<custom></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|<span data-ttu-id="d067d-143">Určuje vlastní sdílené překladač pro netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="d067d-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="d067d-144">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d067d-144">\<endpoint></span></span>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|<span data-ttu-id="d067d-145">Konfiguruje různé typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d067d-145">Configures different types of endpoints.</span></span>|  
|[<span data-ttu-id="d067d-146">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="d067d-146">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="d067d-147">Určuje Security Token Service (Služba tokenů zabezpečení) pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="d067d-147">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="d067d-148">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d067d-148">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="d067d-149">Určuje koncový bod metadat pro Security Token Service (Služba tokenů zabezpečení) federované služby.</span><span class="sxs-lookup"><span data-stu-id="d067d-149">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="d067d-150">\<– issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="d067d-150">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="d067d-151">Definuje parametry pro token vydaných v vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d067d-151">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="d067d-152">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="d067d-152">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="d067d-153">Určuje místní Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="d067d-153">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d067d-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="d067d-154">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [<span data-ttu-id="d067d-155">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d067d-155">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d067d-156">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="d067d-156">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
