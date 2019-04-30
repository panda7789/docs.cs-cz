---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793819"
---
# <a name="servicecertificate"></a><span data-ttu-id="4f534-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4f534-101">\<serviceCertificate></span></span>
<span data-ttu-id="4f534-102">Nakonfiguruje certifikát X.509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="4f534-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="4f534-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="4f534-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="4f534-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4f534-104">\<federationConfiguration></span></span>  
<span data-ttu-id="4f534-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4f534-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f534-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f534-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f534-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f534-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4f534-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f534-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f534-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f534-109">Attributes</span></span>  
 <span data-ttu-id="4f534-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f534-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f534-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f534-111">Child Elements</span></span>  
  
|<span data-ttu-id="4f534-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f534-112">Element</span></span>|<span data-ttu-id="4f534-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4f534-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f534-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="4f534-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="4f534-115">Určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4f534-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f534-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f534-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4f534-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f534-117">Element</span></span>|<span data-ttu-id="4f534-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4f534-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f534-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4f534-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="4f534-120">Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="4f534-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4f534-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f534-121">Example</span></span>  
 <span data-ttu-id="4f534-122">Následující kód XML ukazuje použití \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="4f534-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="4f534-123">XML je převzata z `CustomToken` vzorku.</span><span class="sxs-lookup"><span data-stu-id="4f534-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
