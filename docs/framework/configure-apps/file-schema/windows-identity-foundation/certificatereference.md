---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8acf4b6d6e6e8a0fcf7d73139a1d2c5ea03f063
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="bf6f3-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="bf6f3-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="bf6f3-103">Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="bf6f3-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="bf6f3-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="bf6f3-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf6f3-105">\<federationConfiguration></span></span>  
<span data-ttu-id="bf6f3-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bf6f3-106">\<serviceCertificate></span></span>  
<span data-ttu-id="bf6f3-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="bf6f3-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6f3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6f3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf6f3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf6f3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bf6f3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf6f3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf6f3-111">Attributes</span></span>  
  
|<span data-ttu-id="bf6f3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf6f3-112">Attribute</span></span>|<span data-ttu-id="bf6f3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bf6f3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf6f3-114">storeName</span><span class="sxs-lookup"><span data-stu-id="bf6f3-114">storeName</span></span>|<span data-ttu-id="bf6f3-115">Název úložiště certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="bf6f3-116">Výchozí hodnota je "Moje".</span><span class="sxs-lookup"><span data-stu-id="bf6f3-116">The default is "My".</span></span> <span data-ttu-id="bf6f3-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-117">Optional.</span></span>|  
|<span data-ttu-id="bf6f3-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="bf6f3-118">storeLocation</span></span>|<span data-ttu-id="bf6f3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje umístění úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="bf6f3-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="bf6f3-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="bf6f3-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-121">Optional.</span></span>|  
|<span data-ttu-id="bf6f3-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="bf6f3-122">x509FindType</span></span>|<span data-ttu-id="bf6f3-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ vyhledávání, která má být zpracována.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="bf6f3-124">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="bf6f3-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="bf6f3-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-125">Optional.</span></span>|  
|<span data-ttu-id="bf6f3-126">findValue</span><span class="sxs-lookup"><span data-stu-id="bf6f3-126">findValue</span></span>|<span data-ttu-id="bf6f3-127">Hodnota k vyhledání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="bf6f3-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-128">Optional.</span></span>|  
|<span data-ttu-id="bf6f3-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="bf6f3-129">isChainIncluded</span></span>|<span data-ttu-id="bf6f3-130">Určuje, zda má být provedena ověření pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="bf6f3-131">Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="bf6f3-132">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf6f3-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf6f3-133">Child Elements</span></span>  
 <span data-ttu-id="bf6f3-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf6f3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf6f3-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf6f3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="bf6f3-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf6f3-136">Element</span></span>|<span data-ttu-id="bf6f3-137">Popis</span><span class="sxs-lookup"><span data-stu-id="bf6f3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf6f3-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bf6f3-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="bf6f3-139">Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf6f3-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf6f3-140">Remarks</span></span>  
 <span data-ttu-id="bf6f3-141">`<certificateReference>` Element určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="bf6f3-142">Pokud je zadán jako podřízený element `<serviceCertficate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="bf6f3-143">`<certificateReference>` Element je reprezentována <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
