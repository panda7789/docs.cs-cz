---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 994677904cada71dbc7cce4b6ca0de1d4dc65014
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085641"
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="152c5-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="152c5-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="152c5-103">Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="152c5-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="152c5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="152c5-104">\<system.identityModel></span></span>  
<span data-ttu-id="152c5-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="152c5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="152c5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="152c5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="152c5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="152c5-107">\<add></span></span>  
<span data-ttu-id="152c5-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="152c5-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="152c5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="152c5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="152c5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="152c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="152c5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="152c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="152c5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="152c5-112">Attributes</span></span>  
  
|<span data-ttu-id="152c5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="152c5-113">Attribute</span></span>|<span data-ttu-id="152c5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="152c5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="152c5-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="152c5-115">certificateValidationMode</span></span>|<span data-ttu-id="152c5-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="152c5-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="152c5-117">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="152c5-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="152c5-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="152c5-118">mapToWindows</span></span>|<span data-ttu-id="152c5-119">Určuje, zda obslužná rutina tokenů mělo mapovat ověřování tokenu účet Windows s použitím příchozí deklarace identity UPN.</span><span class="sxs-lookup"><span data-stu-id="152c5-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="152c5-120">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="152c5-120">The default is "false".</span></span>|  
|<span data-ttu-id="152c5-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="152c5-121">revocationMode</span></span>|<span data-ttu-id="152c5-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="152c5-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="152c5-123">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="152c5-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="152c5-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="152c5-124">trustedStoreLocation</span></span>|<span data-ttu-id="152c5-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="152c5-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="152c5-126">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="152c5-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="152c5-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="152c5-127">certificateValidator</span></span>|<span data-ttu-id="152c5-128">Vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="152c5-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="152c5-129">Pokud `certificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="152c5-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="152c5-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="152c5-130">Child Elements</span></span>  
 <span data-ttu-id="152c5-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="152c5-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="152c5-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="152c5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="152c5-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="152c5-133">Element</span></span>|<span data-ttu-id="152c5-134">Popis</span><span class="sxs-lookup"><span data-stu-id="152c5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="152c5-135">\<add></span><span class="sxs-lookup"><span data-stu-id="152c5-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="152c5-136">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="152c5-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="152c5-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="152c5-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
