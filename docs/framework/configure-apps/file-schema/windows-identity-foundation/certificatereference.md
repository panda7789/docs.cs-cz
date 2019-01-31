---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269338"
---
# <a name="certificatereference"></a><span data-ttu-id="e4a79-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="e4a79-101">\<certificateReference></span></span>
<span data-ttu-id="e4a79-102">Určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="e4a79-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="e4a79-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="e4a79-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="e4a79-104">\<federationConfiguration></span></span>  
<span data-ttu-id="e4a79-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e4a79-105">\<serviceCertificate></span></span>  
<span data-ttu-id="e4a79-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="e4a79-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a79-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a79-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4a79-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4a79-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4a79-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4a79-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4a79-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4a79-110">Attributes</span></span>  
  
|<span data-ttu-id="e4a79-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4a79-111">Attribute</span></span>|<span data-ttu-id="e4a79-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e4a79-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4a79-113">storeName</span><span class="sxs-lookup"><span data-stu-id="e4a79-113">storeName</span></span>|<span data-ttu-id="e4a79-114">Název úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="e4a79-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="e4a79-115">Výchozí hodnota je "Moje".</span><span class="sxs-lookup"><span data-stu-id="e4a79-115">The default is "My".</span></span> <span data-ttu-id="e4a79-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4a79-116">Optional.</span></span>|  
|<span data-ttu-id="e4a79-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="e4a79-117">storeLocation</span></span>|<span data-ttu-id="e4a79-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje umístění úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="e4a79-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="e4a79-119">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="e4a79-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="e4a79-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4a79-120">Optional.</span></span>|  
|<span data-ttu-id="e4a79-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="e4a79-121">x509FindType</span></span>|<span data-ttu-id="e4a79-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ hledání, které má být provedena.</span><span class="sxs-lookup"><span data-stu-id="e4a79-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="e4a79-123">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="e4a79-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="e4a79-124">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4a79-124">Optional.</span></span>|  
|<span data-ttu-id="e4a79-125">findValue</span><span class="sxs-lookup"><span data-stu-id="e4a79-125">findValue</span></span>|<span data-ttu-id="e4a79-126">Hodnotu vyhledávání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="e4a79-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e4a79-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4a79-127">Optional.</span></span>|  
|<span data-ttu-id="e4a79-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="e4a79-128">isChainIncluded</span></span>|<span data-ttu-id="e4a79-129">Určuje, zda by měl provádět ověření pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="e4a79-130">Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="e4a79-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4a79-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4a79-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4a79-132">Child Elements</span></span>  
 <span data-ttu-id="e4a79-133">Žádná</span><span class="sxs-lookup"><span data-stu-id="e4a79-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4a79-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4a79-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e4a79-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4a79-135">Element</span></span>|<span data-ttu-id="e4a79-136">Popis</span><span class="sxs-lookup"><span data-stu-id="e4a79-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4a79-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e4a79-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="e4a79-138">Nakonfiguruje certifikát používaný k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4a79-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4a79-139">Remarks</span></span>  
 <span data-ttu-id="e4a79-140">`<certificateReference>` Prvek určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="e4a79-141">Pokud je zadán jako podřízený prvek `<serviceCertficate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-141">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="e4a79-142">`<certificateReference>` Prvek je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="e4a79-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
