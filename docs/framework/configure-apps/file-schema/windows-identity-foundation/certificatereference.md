---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075080"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="96b85-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="96b85-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="96b85-103">Určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="96b85-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="96b85-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="96b85-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="96b85-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="96b85-105">\<federationConfiguration></span></span>  
<span data-ttu-id="96b85-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="96b85-106">\<serviceCertificate></span></span>  
<span data-ttu-id="96b85-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="96b85-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b85-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b85-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96b85-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96b85-109">Attributes and Elements</span></span>  
 <span data-ttu-id="96b85-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96b85-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96b85-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="96b85-111">Attributes</span></span>  
  
|<span data-ttu-id="96b85-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="96b85-112">Attribute</span></span>|<span data-ttu-id="96b85-113">Popis</span><span class="sxs-lookup"><span data-stu-id="96b85-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96b85-114">storeName</span><span class="sxs-lookup"><span data-stu-id="96b85-114">storeName</span></span>|<span data-ttu-id="96b85-115">Název úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="96b85-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="96b85-116">Výchozí hodnota je "Moje".</span><span class="sxs-lookup"><span data-stu-id="96b85-116">The default is "My".</span></span> <span data-ttu-id="96b85-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="96b85-117">Optional.</span></span>|  
|<span data-ttu-id="96b85-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="96b85-118">storeLocation</span></span>|<span data-ttu-id="96b85-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje umístění úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="96b85-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="96b85-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="96b85-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="96b85-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="96b85-121">Optional.</span></span>|  
|<span data-ttu-id="96b85-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="96b85-122">x509FindType</span></span>|<span data-ttu-id="96b85-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ hledání, které má být provedena.</span><span class="sxs-lookup"><span data-stu-id="96b85-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="96b85-124">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="96b85-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="96b85-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="96b85-125">Optional.</span></span>|  
|<span data-ttu-id="96b85-126">findValue</span><span class="sxs-lookup"><span data-stu-id="96b85-126">findValue</span></span>|<span data-ttu-id="96b85-127">Hodnotu vyhledávání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="96b85-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="96b85-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="96b85-128">Optional.</span></span>|  
|<span data-ttu-id="96b85-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="96b85-129">isChainIncluded</span></span>|<span data-ttu-id="96b85-130">Určuje, zda by měl provádět ověření pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="96b85-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="96b85-131">Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="96b85-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="96b85-132">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="96b85-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96b85-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96b85-133">Child Elements</span></span>  
 <span data-ttu-id="96b85-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="96b85-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96b85-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96b85-135">Parent Elements</span></span>  
  
|<span data-ttu-id="96b85-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="96b85-136">Element</span></span>|<span data-ttu-id="96b85-137">Popis</span><span class="sxs-lookup"><span data-stu-id="96b85-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96b85-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="96b85-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="96b85-139">Nakonfiguruje certifikát používaný k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="96b85-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b85-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b85-140">Remarks</span></span>  
 <span data-ttu-id="96b85-141">`<certificateReference>` Prvek určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="96b85-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="96b85-142">Pokud je zadán jako podřízený prvek `<serviceCertficate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="96b85-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="96b85-143">`<certificateReference>` Prvek je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="96b85-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
