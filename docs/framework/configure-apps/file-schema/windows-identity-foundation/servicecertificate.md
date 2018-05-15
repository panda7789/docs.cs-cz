---
title: '&lt;ServiceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af59562dbf6c13970526f1665a9ba2c57c4f32ee
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="03705-102">&lt;ServiceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="03705-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="03705-103">Nakonfiguruje certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="03705-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="03705-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="03705-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="03705-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="03705-105">\<federationConfiguration></span></span>  
<span data-ttu-id="03705-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="03705-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03705-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03705-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03705-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03705-108">Attributes and Elements</span></span>  
 <span data-ttu-id="03705-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03705-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03705-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="03705-110">Attributes</span></span>  
 <span data-ttu-id="03705-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="03705-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03705-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03705-112">Child Elements</span></span>  
  
|<span data-ttu-id="03705-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="03705-113">Element</span></span>|<span data-ttu-id="03705-114">Popis</span><span class="sxs-lookup"><span data-stu-id="03705-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03705-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="03705-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="03705-116">Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="03705-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03705-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03705-117">Parent Elements</span></span>  
  
|<span data-ttu-id="03705-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="03705-118">Element</span></span>|<span data-ttu-id="03705-119">Popis</span><span class="sxs-lookup"><span data-stu-id="03705-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03705-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="03705-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="03705-121">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="03705-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="03705-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="03705-122">Example</span></span>  
 <span data-ttu-id="03705-123">Následující kód XML ukazuje použití \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="03705-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="03705-124">Soubor XML je převzat ze `CustomToken` ukázka.</span><span class="sxs-lookup"><span data-stu-id="03705-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
