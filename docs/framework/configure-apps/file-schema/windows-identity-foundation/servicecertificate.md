---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251861"
---
# \<serviceCertificate>
<span data-ttu-id="89316-101">Nakonfiguruje certifikát X. 509, který se používá k šifrování a dešifrování tokenů.</span><span class="sxs-lookup"><span data-stu-id="89316-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="89316-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89316-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89316-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="89316-103">Attributes and Elements</span></span>  
 <span data-ttu-id="89316-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="89316-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89316-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="89316-105">Attributes</span></span>  
 <span data-ttu-id="89316-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="89316-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89316-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="89316-107">Child Elements</span></span>  
  
|<span data-ttu-id="89316-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="89316-108">Element</span></span>|<span data-ttu-id="89316-109">Description</span><span class="sxs-lookup"><span data-stu-id="89316-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="89316-110">Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="89316-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89316-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="89316-111">Parent Elements</span></span>  
  
|<span data-ttu-id="89316-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="89316-112">Element</span></span>|<span data-ttu-id="89316-113">Description</span><span class="sxs-lookup"><span data-stu-id="89316-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="89316-114">Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="89316-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89316-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="89316-115">Example</span></span>  
 <span data-ttu-id="89316-116">Následující kód XML ukazuje použití \<serviceCertificate> prvku.</span><span class="sxs-lookup"><span data-stu-id="89316-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="89316-117">KÓD XML je získán z `CustomToken` ukázky.</span><span class="sxs-lookup"><span data-stu-id="89316-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
