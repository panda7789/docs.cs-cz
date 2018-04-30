---
title: '&lt;serviceCertificate&gt; – &lt;serviceCredentials&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16c5c065e805cb672f85dd9ff28f5b5d82d1ffba
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="0db66-102">&lt;serviceCertificate&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="0db66-102">&lt;serviceCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="0db66-103">Zadejte certifikát X.509, který se použije k ověřování klientů pomocí režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="0db66-103">Specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span>  
  
 <span data-ttu-id="0db66-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0db66-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0db66-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0db66-105">\<behaviors></span></span>  
<span data-ttu-id="0db66-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0db66-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0db66-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0db66-107">\<behavior></span></span>  
<span data-ttu-id="0db66-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0db66-108">\<serviceCredentials></span></span>  
<span data-ttu-id="0db66-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="0db66-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db66-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0db66-110">Syntax</span></span>  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0db66-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0db66-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0db66-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0db66-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0db66-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0db66-113">Attributes</span></span>  
  
|<span data-ttu-id="0db66-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="0db66-114">Attribute</span></span>|<span data-ttu-id="0db66-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0db66-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="0db66-116">Řetězec, který obsahuje hodnotu k vyhledání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="0db66-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="0db66-117">Typ obsažený v atributu musí splňovat požadavky na zadaný X509FindType.</span><span class="sxs-lookup"><span data-stu-id="0db66-117">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="0db66-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0db66-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="0db66-119">Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu serveru proti.</span><span class="sxs-lookup"><span data-stu-id="0db66-119">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="0db66-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0db66-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0db66-121">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="0db66-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="0db66-122">-CurrentUser: úložiště certifikátů přiřazená aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="0db66-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="0db66-123">Výchozí hodnota je v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="0db66-123">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="0db66-124">Určuje název úložiště certifikátu X.509 otevřete.</span><span class="sxs-lookup"><span data-stu-id="0db66-124">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="0db66-125">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0db66-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0db66-126">-Adresáře: Úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="0db66-126">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="0db66-127">-AuthRoot: Certifikát úložiště pro třetí strany certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="0db66-127">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="0db66-128">-CertificatAuthority: Úložiště certifikátů pro zprostředkující certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="0db66-128">-   CertificatAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="0db66-129">-Nepovolené: Certifikát úložiště pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="0db66-129">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="0db66-130">-: Úložiště certifikátů my Pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="0db66-130">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="0db66-131">-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="0db66-131">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="0db66-132">-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.</span><span class="sxs-lookup"><span data-stu-id="0db66-132">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="0db66-133">-TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodné vydavatele.</span><span class="sxs-lookup"><span data-stu-id="0db66-133">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="0db66-134">Výchozí hodnota je můj.</span><span class="sxs-lookup"><span data-stu-id="0db66-134">The default is My.</span></span>|  
|`x509FindType`|<span data-ttu-id="0db66-135">Definuje typ vyhledávání X.509 provést.</span><span class="sxs-lookup"><span data-stu-id="0db66-135">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="0db66-136">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0db66-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0db66-137">-FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="0db66-137">-   FindByThumbprint</span></span><br /><span data-ttu-id="0db66-138">-FindBySubjectName.</span><span class="sxs-lookup"><span data-stu-id="0db66-138">-   FindBySubjectName</span></span><br /><span data-ttu-id="0db66-139">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="0db66-139">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="0db66-140">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="0db66-140">-   FindByIssuerName</span></span><br /><span data-ttu-id="0db66-141">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="0db66-141">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="0db66-142">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="0db66-142">-   FindBySerialNumber</span></span><br /><span data-ttu-id="0db66-143">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="0db66-143">-   FindByTimeValid</span></span><br /><span data-ttu-id="0db66-144">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="0db66-144">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="0db66-145">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="0db66-145">-   FindByTemplateName</span></span><br /><span data-ttu-id="0db66-146">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="0db66-146">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="0db66-147">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="0db66-147">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="0db66-148">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="0db66-148">-   FindByExtension</span></span><br /><span data-ttu-id="0db66-149">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="0db66-149">-   FindByKeyUsage</span></span><br /><span data-ttu-id="0db66-150">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="0db66-150">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="0db66-151">Typ obsažený v `findValue` atributu musí splňovat požadavky na zadaný X509FindType.</span><span class="sxs-lookup"><span data-stu-id="0db66-151">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="0db66-152">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="0db66-152">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0db66-153">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0db66-153">Child Elements</span></span>  
 <span data-ttu-id="0db66-154">Žádné</span><span class="sxs-lookup"><span data-stu-id="0db66-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0db66-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0db66-155">Parent Elements</span></span>  
  
|<span data-ttu-id="0db66-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="0db66-156">Element</span></span>|<span data-ttu-id="0db66-157">Popis</span><span class="sxs-lookup"><span data-stu-id="0db66-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0db66-158">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0db66-158">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="0db66-159">Určí pověření, které mají být použity v ověřování služby, a ověření přihlašovacích údajů klienta související nastavení.</span><span class="sxs-lookup"><span data-stu-id="0db66-159">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0db66-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0db66-160">Remarks</span></span>  
 <span data-ttu-id="0db66-161">Tento prvek slouží k určení certifikát X.509, který se použije k ověřování klientů pomocí režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="0db66-161">Use this element to specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="0db66-162">Pokud používáte certifikát, který se bude pravidelně obnovovat, se změní jeho kryptografický otisk.</span><span class="sxs-lookup"><span data-stu-id="0db66-162">If you are using a certificate that will be periodically renewed, then its thumbprint will change.</span></span> <span data-ttu-id="0db66-163">V takovém případě použijte název subjektu, jako `x509FindType` vzhledem k tomu, že certifikát můžete ho znova vydat se stejným názvem subjektu.</span><span class="sxs-lookup"><span data-stu-id="0db66-163">In that case, use the subject name as the `x509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="0db66-164">Další informace o použití elementu najdete v tématu [postupy: určení hodnot přihlašovacích údajů klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span><span class="sxs-lookup"><span data-stu-id="0db66-164">For more information about using the element, see [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db66-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="0db66-165">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [<span data-ttu-id="0db66-166">Postupy: Zadání hodnot přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="0db66-166">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="0db66-167">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0db66-167">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
