---
title: "Federace a vystavené tokeny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017d3e51022ad9980dc8f058415697c80a2a6b35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="5c3ad-102">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5c3ad-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="5c3ad-103">S [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], můžete vytvořit klientů komunikujících bezpečně s služby, které implementují specifikace WS-Federation a WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-103">With [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="5c3ad-104">Specifikace poskytnout mechanismy, které umožňují ověřování a autorizace mezi různé důvěryhodnosti sfér pomocí XML, protokolu SOAP a webové služby popis Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="5c3ad-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c3ad-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5c3ad-105">In This Section</span></span>  
 [<span data-ttu-id="5c3ad-106">Federace</span><span class="sxs-lookup"><span data-stu-id="5c3ad-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="5c3ad-107">Obsahuje přehled federace.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="5c3ad-108">Federace a důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="5c3ad-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="5c3ad-109">Jsou uvedené problémy návrhu znát při vytvoření federovaného služby nebo klientů.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="5c3ad-110">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="5c3ad-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="5c3ad-111">Popisuje základní informace o vytvoření federovaného klienta s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c3ad-111">Describes the basics of creating a federated client with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="5c3ad-112">Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="5c3ad-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="5c3ad-113">Popisuje kroky k vytvoření federované služby.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="5c3ad-114">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5c3ad-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="5c3ad-115">Popisuje postup konfigurace klientů a služeb, které používají `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="5c3ad-116">Postupy: Vytvoření služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c3ad-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="5c3ad-117">Popisuje kroky k vytvoření služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="5c3ad-118">Tokeny a deklarace identity jazyka SAML (Security Assertions Markup Language)</span><span class="sxs-lookup"><span data-stu-id="5c3ad-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="5c3ad-119">Popisuje tokeny zabezpečení kontrolní výrazy Markup Language (SAML), které jsou rozšiřitelný a povolit vytvářet bohaté typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="5c3ad-120">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="5c3ad-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="5c3ad-121">Popisuje postup vytvoření místního vystavitele tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="5c3ad-122">Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5c3ad-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="5c3ad-123">Popisuje postup zakázání zabezpečených relací na `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="5c3ad-124">Zakázání zabezpečených relací je nezbytné, při vytváření webové farmy, která vyžaduje relaci pro každého klienta.</span><span class="sxs-lookup"><span data-stu-id="5c3ad-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5c3ad-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5c3ad-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="5c3ad-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c3ad-126">See Also</span></span>  
 [<span data-ttu-id="5c3ad-127">Autorizace</span><span class="sxs-lookup"><span data-stu-id="5c3ad-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="5c3ad-128">Vlastní tokeny</span><span class="sxs-lookup"><span data-stu-id="5c3ad-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="5c3ad-129">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5c3ad-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
