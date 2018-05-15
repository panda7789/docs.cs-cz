---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="625dc-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="625dc-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="625dc-103">Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="625dc-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="625dc-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="625dc-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="625dc-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="625dc-105">\<federationConfiguration></span></span>  
<span data-ttu-id="625dc-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="625dc-106">\<serviceCertificate></span></span>  
<span data-ttu-id="625dc-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="625dc-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="625dc-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="625dc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="625dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="625dc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="625dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="625dc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="625dc-111">Attributes</span></span>  
  
|<span data-ttu-id="625dc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="625dc-112">Attribute</span></span>|<span data-ttu-id="625dc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="625dc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="625dc-114">storeName</span><span class="sxs-lookup"><span data-stu-id="625dc-114">storeName</span></span>|<span data-ttu-id="625dc-115">Název úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="625dc-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="625dc-116">Výchozí hodnota je "Moje".</span><span class="sxs-lookup"><span data-stu-id="625dc-116">The default is "My".</span></span> <span data-ttu-id="625dc-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="625dc-117">Optional.</span></span>|  
|<span data-ttu-id="625dc-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="625dc-118">storeLocation</span></span>|<span data-ttu-id="625dc-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje umístění úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="625dc-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="625dc-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="625dc-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="625dc-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="625dc-121">Optional.</span></span>|  
|<span data-ttu-id="625dc-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="625dc-122">x509FindType</span></span>|<span data-ttu-id="625dc-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ vyhledávání, která má být zpracována.</span><span class="sxs-lookup"><span data-stu-id="625dc-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="625dc-124">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="625dc-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="625dc-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="625dc-125">Optional.</span></span>|  
|<span data-ttu-id="625dc-126">findValue</span><span class="sxs-lookup"><span data-stu-id="625dc-126">findValue</span></span>|<span data-ttu-id="625dc-127">Hodnota k vyhledání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="625dc-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="625dc-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="625dc-128">Optional.</span></span>|  
|<span data-ttu-id="625dc-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="625dc-129">isChainIncluded</span></span>|<span data-ttu-id="625dc-130">Určuje, zda má být provedena ověření pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="625dc-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="625dc-131">Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="625dc-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="625dc-132">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="625dc-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="625dc-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="625dc-133">Child Elements</span></span>  
 <span data-ttu-id="625dc-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="625dc-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="625dc-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="625dc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="625dc-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="625dc-136">Element</span></span>|<span data-ttu-id="625dc-137">Popis</span><span class="sxs-lookup"><span data-stu-id="625dc-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="625dc-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="625dc-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="625dc-139">Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="625dc-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="625dc-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="625dc-140">Remarks</span></span>  
 <span data-ttu-id="625dc-141">`<certificateReference>` Element určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="625dc-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="625dc-142">Pokud je zadán jako podřízený element `<serviceCertficate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="625dc-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="625dc-143">`<certificateReference>` Element je reprezentována <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="625dc-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
