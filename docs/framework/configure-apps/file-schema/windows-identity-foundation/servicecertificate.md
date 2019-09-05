---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251861"
---
# <a name="servicecertificate"></a><span data-ttu-id="09913-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="09913-101">\<serviceCertificate></span></span>
<span data-ttu-id="09913-102">Nakonfiguruje certifikát X. 509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="09913-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="09913-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09913-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09913-104">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="09913-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="09913-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="09913-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="09913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="09913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09913-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09913-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09913-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09913-108">Attributes and Elements</span></span>  
 <span data-ttu-id="09913-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09913-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09913-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="09913-110">Attributes</span></span>  
 <span data-ttu-id="09913-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="09913-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="09913-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09913-112">Child Elements</span></span>  
  
|<span data-ttu-id="09913-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="09913-113">Element</span></span>|<span data-ttu-id="09913-114">Popis</span><span class="sxs-lookup"><span data-stu-id="09913-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09913-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="09913-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="09913-116">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="09913-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09913-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09913-117">Parent Elements</span></span>  
  
|<span data-ttu-id="09913-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="09913-118">Element</span></span>|<span data-ttu-id="09913-119">Popis</span><span class="sxs-lookup"><span data-stu-id="09913-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09913-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="09913-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="09913-121">Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM).</span><span class="sxs-lookup"><span data-stu-id="09913-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09913-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="09913-122">Example</span></span>  
 <span data-ttu-id="09913-123">Následující kód XML ukazuje použití \<prvku serviceCertificate >.</span><span class="sxs-lookup"><span data-stu-id="09913-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="09913-124">Kód XML je získán z `CustomToken` ukázky.</span><span class="sxs-lookup"><span data-stu-id="09913-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
