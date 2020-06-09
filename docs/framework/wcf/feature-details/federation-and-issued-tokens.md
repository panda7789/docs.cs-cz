---
title: Federace a vystavené tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: aeffc1e2a7b61dfd9406b9f06678064533ea61ec
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595502"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="0e6dc-102">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0e6dc-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="0e6dc-103">Pomocí Windows Communication Foundation (WCF) můžete vytvořit klienty, kteří budou zabezpečeně komunikovat se službami, které implementují specifikace WS-Federation a WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="0e6dc-104">Specifikace používají XML, SOAP a Web Services Description Language (WSDL) k poskytování mechanismů, které umožňují ověřování a autorizaci napříč různými sférami vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e6dc-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0e6dc-105">In This Section</span></span>  
 [<span data-ttu-id="0e6dc-106">metadata</span><span class="sxs-lookup"><span data-stu-id="0e6dc-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="0e6dc-107">Poskytuje přehled federace.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="0e6dc-108">Federace a důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="0e6dc-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="0e6dc-109">Uvádí aspekty návrhu, které je potřeba znát při vytváření federovaných služeb nebo klientů.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="0e6dc-110">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="0e6dc-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="0e6dc-111">Popisuje základy vytvoření federovaného klienta pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="0e6dc-112">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="0e6dc-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="0e6dc-113">Popisuje kroky při vytváření federované služby.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="0e6dc-114">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0e6dc-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="0e6dc-115">V této části najdete popis postupu konfigurace klientů a služeb, které používají `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="0e6dc-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="0e6dc-116">Postupy: Vytvoření služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0e6dc-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="0e6dc-117">Popisuje kroky pro vytvoření služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="0e6dc-118">Tokeny a deklarace identity jazyka SAML (Security Assertions Markup Language)</span><span class="sxs-lookup"><span data-stu-id="0e6dc-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="0e6dc-119">Popisuje tokeny SAML (Security Assert Markup Language), které jsou rozšiřitelné a umožňují vytvářet bohatý typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="0e6dc-120">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="0e6dc-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="0e6dc-121">V této části najdete popis postupu vytvoření místního vystavitele tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="0e6dc-122">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0e6dc-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="0e6dc-123">Popisuje, jak zakázat zabezpečené relace na `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="0e6dc-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="0e6dc-124">Při vytváření webové farmy, která vyžaduje relaci pro každého klienta, je nutné zakázat zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="0e6dc-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0e6dc-125">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="0e6dc-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="0e6dc-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e6dc-126">See also</span></span>

- [<span data-ttu-id="0e6dc-127">Autorizace</span><span class="sxs-lookup"><span data-stu-id="0e6dc-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="0e6dc-128">Vlastní tokeny</span><span class="sxs-lookup"><span data-stu-id="0e6dc-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="0e6dc-129">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0e6dc-129">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
