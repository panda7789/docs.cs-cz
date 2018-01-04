---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1373d1e95a0e569f5e5cf433d305d008b4daf838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="bc619-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="bc619-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="bc619-103">Nakonfiguruje certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="bc619-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="bc619-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="bc619-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="bc619-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bc619-105">\<federationConfiguration></span></span>  
<span data-ttu-id="bc619-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bc619-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc619-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc619-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc619-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc619-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bc619-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc619-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc619-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc619-110">Attributes</span></span>  
 <span data-ttu-id="bc619-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc619-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc619-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc619-112">Child Elements</span></span>  
  
|<span data-ttu-id="bc619-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc619-113">Element</span></span>|<span data-ttu-id="bc619-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bc619-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc619-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="bc619-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="bc619-116">Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bc619-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc619-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc619-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bc619-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc619-118">Element</span></span>|<span data-ttu-id="bc619-119">Popis</span><span class="sxs-lookup"><span data-stu-id="bc619-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc619-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bc619-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="bc619-121">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="bc619-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bc619-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc619-122">Example</span></span>  
 <span data-ttu-id="bc619-123">Následující kód XML ukazuje použití \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="bc619-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="bc619-124">Soubor XML je převzat ze `CustomToken` ukázka.</span><span class="sxs-lookup"><span data-stu-id="bc619-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
