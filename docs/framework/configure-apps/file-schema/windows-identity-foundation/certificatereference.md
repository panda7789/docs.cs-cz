---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941934"
---
# <a name="certificatereference"></a><span data-ttu-id="1c3df-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="1c3df-101">\<certificateReference></span></span>
<span data-ttu-id="1c3df-102">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="1c3df-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="1c3df-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="1c3df-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="1c3df-104">\<federationConfiguration></span></span>  
<span data-ttu-id="1c3df-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1c3df-105">\<serviceCertificate></span></span>  
<span data-ttu-id="1c3df-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="1c3df-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c3df-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c3df-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c3df-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c3df-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1c3df-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c3df-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c3df-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c3df-110">Attributes</span></span>  
  
|<span data-ttu-id="1c3df-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c3df-111">Attribute</span></span>|<span data-ttu-id="1c3df-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1c3df-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c3df-113">storeName</span><span class="sxs-lookup"><span data-stu-id="1c3df-113">storeName</span></span>|<span data-ttu-id="1c3df-114">Název úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="1c3df-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="1c3df-115">Výchozí hodnota je my.</span><span class="sxs-lookup"><span data-stu-id="1c3df-115">The default is "My".</span></span> <span data-ttu-id="1c3df-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c3df-116">Optional.</span></span>|  
|<span data-ttu-id="1c3df-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1c3df-117">storeLocation</span></span>|<span data-ttu-id="1c3df-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje umístění úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="1c3df-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="1c3df-119">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1c3df-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="1c3df-120">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c3df-120">Optional.</span></span>|  
|<span data-ttu-id="1c3df-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1c3df-121">x509FindType</span></span>|<span data-ttu-id="1c3df-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnota, která určuje typ hledání, které má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="1c3df-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="1c3df-123">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="1c3df-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="1c3df-124">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c3df-124">Optional.</span></span>|  
|<span data-ttu-id="1c3df-125">findValue</span><span class="sxs-lookup"><span data-stu-id="1c3df-125">findValue</span></span>|<span data-ttu-id="1c3df-126">Hodnota, která se má vyhledat v úložišti certifikátů X. 509</span><span class="sxs-lookup"><span data-stu-id="1c3df-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="1c3df-127">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c3df-127">Optional.</span></span>|  
|<span data-ttu-id="1c3df-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="1c3df-128">isChainIncluded</span></span>|<span data-ttu-id="1c3df-129">Určuje, zda má být ověřování provedeno pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="1c3df-130">Výchozí hodnota je "true"; ověřování se provádí pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="1c3df-131">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c3df-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c3df-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c3df-132">Child Elements</span></span>  
 <span data-ttu-id="1c3df-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="1c3df-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c3df-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c3df-134">Parent Elements</span></span>  
  
|<span data-ttu-id="1c3df-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c3df-135">Element</span></span>|<span data-ttu-id="1c3df-136">Popis</span><span class="sxs-lookup"><span data-stu-id="1c3df-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c3df-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1c3df-137">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="1c3df-138">Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c3df-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c3df-139">Remarks</span></span>  
 <span data-ttu-id="1c3df-140">`<certificateReference>` Element určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="1c3df-141">Pokud je zadána jako podřízený element `<serviceCertificate>` elementu, určuje umístění a nastavení ověřování certifikátu X. 509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c3df-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="1c3df-142">Element je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement>třídou. `<certificateReference>`</span><span class="sxs-lookup"><span data-stu-id="1c3df-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
