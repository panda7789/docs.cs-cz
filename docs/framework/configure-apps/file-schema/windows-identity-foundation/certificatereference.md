---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152811"
---
# <a name="certificatereference"></a><span data-ttu-id="9bf73-101">\<certifikátReference></span><span class="sxs-lookup"><span data-stu-id="9bf73-101">\<certificateReference></span></span>
<span data-ttu-id="9bf73-102">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="9bf73-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9bf73-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9bf73-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="9bf73-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="9bf73-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9bf73-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="9bf73-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="9bf73-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="9bf73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span><span class="sxs-lookup"><span data-stu-id="9bf73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf73-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bf73-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bf73-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9bf73-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9bf73-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9bf73-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bf73-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9bf73-111">Attributes</span></span>  
  
|<span data-ttu-id="9bf73-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9bf73-112">Attribute</span></span>|<span data-ttu-id="9bf73-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9bf73-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bf73-114">Storename</span><span class="sxs-lookup"><span data-stu-id="9bf73-114">storeName</span></span>|<span data-ttu-id="9bf73-115">Název úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="9bf73-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="9bf73-116">Výchozí hodnota je "My".</span><span class="sxs-lookup"><span data-stu-id="9bf73-116">The default is "My".</span></span> <span data-ttu-id="9bf73-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9bf73-117">Optional.</span></span>|  
|<span data-ttu-id="9bf73-118">Storelocation</span><span class="sxs-lookup"><span data-stu-id="9bf73-118">storeLocation</span></span>|<span data-ttu-id="9bf73-119">Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje umístění úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="9bf73-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="9bf73-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="9bf73-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="9bf73-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9bf73-121">Optional.</span></span>|  
|<span data-ttu-id="9bf73-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="9bf73-122">x509FindType</span></span>|<span data-ttu-id="9bf73-123">Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509FindType> která určuje typ hledání, které má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="9bf73-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="9bf73-124">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="9bf73-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="9bf73-125">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9bf73-125">Optional.</span></span>|  
|<span data-ttu-id="9bf73-126">Findvalue</span><span class="sxs-lookup"><span data-stu-id="9bf73-126">findValue</span></span>|<span data-ttu-id="9bf73-127">Hodnota, kterou chcete vyhledat v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="9bf73-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="9bf73-128">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9bf73-128">Optional.</span></span>|  
|<span data-ttu-id="9bf73-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="9bf73-129">isChainIncluded</span></span>|<span data-ttu-id="9bf73-130">Určuje, zda má být ověření provedeno pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="9bf73-131">Výchozí hodnota je "true"; ověření se provádí pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="9bf73-132">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9bf73-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bf73-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9bf73-133">Child Elements</span></span>  
 <span data-ttu-id="9bf73-134">Žádný</span><span class="sxs-lookup"><span data-stu-id="9bf73-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bf73-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9bf73-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9bf73-136">Element</span><span class="sxs-lookup"><span data-stu-id="9bf73-136">Element</span></span>|<span data-ttu-id="9bf73-137">Popis</span><span class="sxs-lookup"><span data-stu-id="9bf73-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bf73-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="9bf73-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="9bf73-139">Konfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bf73-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bf73-140">Remarks</span></span>  
 <span data-ttu-id="9bf73-141">Prvek `<certificateReference>` určuje nastavení, které se používá k vyhledání a ověření certifikátu X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="9bf73-142">Pokud je zadán jako podřízený `<serviceCertificate>` prvek prvku, určuje umístění a nastavení ověření certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="9bf73-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="9bf73-143">Prvek `<certificateReference>` je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="9bf73-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
