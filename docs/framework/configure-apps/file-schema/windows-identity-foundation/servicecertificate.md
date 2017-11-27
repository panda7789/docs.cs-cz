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
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="cb38d-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="cb38d-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="cb38d-103">Nakonfiguruje certifikátu X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="cb38d-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="cb38d-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="cb38d-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="cb38d-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cb38d-105">\<federationConfiguration></span></span>  
<span data-ttu-id="cb38d-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="cb38d-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb38d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb38d-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb38d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cb38d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb38d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cb38d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb38d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="cb38d-110">Attributes</span></span>  
 <span data-ttu-id="cb38d-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="cb38d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb38d-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cb38d-112">Child Elements</span></span>  
  
|<span data-ttu-id="cb38d-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb38d-113">Element</span></span>|<span data-ttu-id="cb38d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cb38d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb38d-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="cb38d-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="cb38d-116">Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="cb38d-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb38d-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cb38d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cb38d-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb38d-118">Element</span></span>|<span data-ttu-id="cb38d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="cb38d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb38d-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cb38d-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="cb38d-121">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="cb38d-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb38d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb38d-122">Example</span></span>  
 <span data-ttu-id="cb38d-123">Následující kód XML ukazuje použití \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="cb38d-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="cb38d-124">Soubor XML je převzat ze `CustomToken` ukázka.</span><span class="sxs-lookup"><span data-stu-id="cb38d-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
