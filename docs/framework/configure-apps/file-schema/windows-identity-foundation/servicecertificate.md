---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084303"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="a6f31-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="a6f31-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="a6f31-103">Nakonfiguruje certifikát X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="a6f31-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="a6f31-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="a6f31-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="a6f31-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a6f31-105">\<federationConfiguration></span></span>  
<span data-ttu-id="a6f31-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a6f31-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f31-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6f31-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6f31-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6f31-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6f31-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6f31-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6f31-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6f31-110">Attributes</span></span>  
 <span data-ttu-id="a6f31-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6f31-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6f31-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6f31-112">Child Elements</span></span>  
  
|<span data-ttu-id="a6f31-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6f31-113">Element</span></span>|<span data-ttu-id="a6f31-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a6f31-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6f31-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="a6f31-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="a6f31-116">Určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="a6f31-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6f31-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6f31-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a6f31-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6f31-118">Element</span></span>|<span data-ttu-id="a6f31-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a6f31-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6f31-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a6f31-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="a6f31-121">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="a6f31-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a6f31-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6f31-122">Example</span></span>  
 <span data-ttu-id="a6f31-123">Následující kód XML ukazuje použití \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="a6f31-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a6f31-124">XML je převzata z `CustomToken` vzorku.</span><span class="sxs-lookup"><span data-stu-id="a6f31-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
