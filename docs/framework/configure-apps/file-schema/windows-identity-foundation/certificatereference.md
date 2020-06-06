---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152811"
---
# \<certificateReference>
<span data-ttu-id="f3bc1-101">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="f3bc1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3bc1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3bc1-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3bc1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f3bc1-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3bc1-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3bc1-105">Attributes</span></span>  
  
|<span data-ttu-id="f3bc1-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3bc1-106">Attribute</span></span>|<span data-ttu-id="f3bc1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f3bc1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3bc1-108">storeName</span><span class="sxs-lookup"><span data-stu-id="f3bc1-108">storeName</span></span>|<span data-ttu-id="f3bc1-109">Název úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="f3bc1-110">Výchozí hodnota je my.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-110">The default is "My".</span></span> <span data-ttu-id="f3bc1-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-111">Optional.</span></span>|  
|<span data-ttu-id="f3bc1-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="f3bc1-112">storeLocation</span></span>|<span data-ttu-id="f3bc1-113"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje umístění úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="f3bc1-114">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="f3bc1-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="f3bc1-115">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-115">Optional.</span></span>|  
|<span data-ttu-id="f3bc1-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="f3bc1-116">x509FindType</span></span>|<span data-ttu-id="f3bc1-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType>Hodnota, která určuje typ hledání, které má být provedeno.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="f3bc1-118">Výchozí hodnota je "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="f3bc1-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="f3bc1-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-119">Optional.</span></span>|  
|<span data-ttu-id="f3bc1-120">findValue</span><span class="sxs-lookup"><span data-stu-id="f3bc1-120">findValue</span></span>|<span data-ttu-id="f3bc1-121">Hodnota, která se má vyhledat v úložišti certifikátů X. 509</span><span class="sxs-lookup"><span data-stu-id="f3bc1-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="f3bc1-122">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-122">Optional.</span></span>|  
|<span data-ttu-id="f3bc1-123">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="f3bc1-123">isChainIncluded</span></span>|<span data-ttu-id="f3bc1-124">Určuje, zda má být ověřování provedeno pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="f3bc1-125">Výchozí hodnota je "true"; ověřování se provádí pomocí řetězu certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="f3bc1-126">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3bc1-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3bc1-127">Child Elements</span></span>  
 <span data-ttu-id="f3bc1-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3bc1-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3bc1-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3bc1-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f3bc1-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3bc1-130">Element</span></span>|<span data-ttu-id="f3bc1-131">Description</span><span class="sxs-lookup"><span data-stu-id="f3bc1-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="f3bc1-132">Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bc1-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3bc1-133">Remarks</span></span>  
 <span data-ttu-id="f3bc1-134">`<certificateReference>`Element určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="f3bc1-135">Pokud je zadána jako podřízený element `<serviceCertificate>` elementu, určuje umístění a nastavení ověřování certifikátu X. 509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="f3bc1-136">`<certificateReference>`Element je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="f3bc1-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
