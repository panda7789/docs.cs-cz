---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252147"
---
# <a name="certificatereference"></a><span data-ttu-id="947c2-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="947c2-101">\<certificateReference></span></span>
<span data-ttu-id="947c2-102">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="947c2-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="947c2-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="947c2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="947c2-104">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="947c2-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="947c2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="947c2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="947c2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="947c2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="947c2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**</span><span class="sxs-lookup"><span data-stu-id="947c2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="947c2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="947c2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="947c2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="947c2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="947c2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="947c2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="947c2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="947c2-111">Attributes</span></span>  
  
|<span data-ttu-id="947c2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="947c2-112">Attribute</span></span>|<span data-ttu-id="947c2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="947c2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="947c2-114">storeName</span><span class="sxs-lookup"><span data-stu-id="947c2-114">storeName</span></span>|<span data-ttu-id="947c2-115">Název úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="947c2-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="947c2-116">Výchozí hodnota je my.</span><span class="sxs-lookup"><span data-stu-id="947c2-116">The default is "My".</span></span> <span data-ttu-id="947c2-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="947c2-117">Optional.</span></span>|  
|<span data-ttu-id="947c2-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="947c2-118">storeLocation</span></span>|<span data-ttu-id="947c2-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje umístění úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="947c2-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="947c2-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="947c2-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="947c2-121">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="947c2-121">Optional.</span></span>|  
|<span data-ttu-id="947c2-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="947c2-122">x509FindType</span></span>|<span data-ttu-id="947c2-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnota, která určuje typ hledání, které má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="947c2-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="947c2-124">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="947c2-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="947c2-125">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="947c2-125">Optional.</span></span>|  
|<span data-ttu-id="947c2-126">findValue</span><span class="sxs-lookup"><span data-stu-id="947c2-126">findValue</span></span>|<span data-ttu-id="947c2-127">Hodnota, která se má vyhledat v úložišti certifikátů X. 509</span><span class="sxs-lookup"><span data-stu-id="947c2-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="947c2-128">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="947c2-128">Optional.</span></span>|  
|<span data-ttu-id="947c2-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="947c2-129">isChainIncluded</span></span>|<span data-ttu-id="947c2-130">Určuje, zda má být ověřování provedeno pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="947c2-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="947c2-131">Výchozí hodnota je "true"; ověřování se provádí pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="947c2-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="947c2-132">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="947c2-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="947c2-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="947c2-133">Child Elements</span></span>  
 <span data-ttu-id="947c2-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="947c2-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="947c2-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="947c2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="947c2-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="947c2-136">Element</span></span>|<span data-ttu-id="947c2-137">Popis</span><span class="sxs-lookup"><span data-stu-id="947c2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="947c2-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="947c2-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="947c2-139">Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="947c2-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="947c2-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="947c2-140">Remarks</span></span>  
 <span data-ttu-id="947c2-141">`<certificateReference>` Element určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="947c2-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="947c2-142">Pokud je zadána jako podřízený element `<serviceCertificate>` elementu, určuje umístění a nastavení ověřování certifikátu X. 509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="947c2-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="947c2-143">Element je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement>třídou. `<certificateReference>`</span><span class="sxs-lookup"><span data-stu-id="947c2-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
