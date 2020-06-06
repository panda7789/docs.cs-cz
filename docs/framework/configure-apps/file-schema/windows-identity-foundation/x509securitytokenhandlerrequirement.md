---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152447"
---
# \<x509SecurityTokenHandlerRequirement>
<span data-ttu-id="419aa-101">Poskytuje volitelnou konfiguraci pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="419aa-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="419aa-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="419aa-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="419aa-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="419aa-103">Attributes and Elements</span></span>  
 <span data-ttu-id="419aa-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="419aa-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="419aa-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="419aa-105">Attributes</span></span>  
  
|<span data-ttu-id="419aa-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="419aa-106">Attribute</span></span>|<span data-ttu-id="419aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="419aa-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="419aa-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="419aa-108">certificateValidationMode</span></span>|<span data-ttu-id="419aa-109"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="419aa-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="419aa-110">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="419aa-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="419aa-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="419aa-111">mapToWindows</span></span>|<span data-ttu-id="419aa-112">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="419aa-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="419aa-113">Výchozí hodnota je false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="419aa-113">The default is "false".</span></span>|  
|<span data-ttu-id="419aa-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="419aa-114">revocationMode</span></span>|<span data-ttu-id="419aa-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="419aa-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="419aa-116">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="419aa-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="419aa-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="419aa-117">trustedStoreLocation</span></span>|<span data-ttu-id="419aa-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="419aa-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="419aa-119">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="419aa-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="419aa-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="419aa-120">certificateValidator</span></span>|<span data-ttu-id="419aa-121">Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="419aa-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="419aa-122">Pokud `certificateValidationMode` je atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="419aa-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="419aa-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="419aa-123">Child Elements</span></span>  
 <span data-ttu-id="419aa-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="419aa-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="419aa-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="419aa-125">Parent Elements</span></span>  
  
|<span data-ttu-id="419aa-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="419aa-126">Element</span></span>|<span data-ttu-id="419aa-127">Description</span><span class="sxs-lookup"><span data-stu-id="419aa-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="419aa-128">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="419aa-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="419aa-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="419aa-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
