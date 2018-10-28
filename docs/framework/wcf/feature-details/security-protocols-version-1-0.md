---
title: Protokoly zabezpečení verze 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 684ab50b6dab4b97577acf7673ed14c53e5af13e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183942"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="54f08-102">Protokoly zabezpečení verze 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="54f08-103">Protokoly webových služeb zabezpečení poskytují webové služby bezpečnostní mechanismy, které pokrývají všechny stávající Podnikové zasílání zpráv požadavků na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="54f08-104">Tato část popisuje podrobnosti Windows Communication Foundation (WCF) verze 1.0 (implementované v <xref:System.ServiceModel.Channels.SecurityBindingElement>) pro protokoly zabezpečení následujících webových služeb.</span><span class="sxs-lookup"><span data-stu-id="54f08-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="54f08-105">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="54f08-105">Specification/Document</span></span>|<span data-ttu-id="54f08-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="54f08-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="54f08-107">WSS: Zabezpečení zpráv SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="54f08-108">Doplněk WSS: Token uživatelského jména profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="54f08-109">Doplněk WSS: X509 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="54f08-110">Doplněk WSS: SAML 1.1 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="54f08-111">Doplněk WSS: Zabezpečení zpráv SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="54f08-112">Doplněk WSS uživatelské jméno Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="54f08-113">Doplněk WSS: X.509 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="54f08-114">Doplněk WSS: Token protokolu Kerberos Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="54f08-115">Doplněk WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="54f08-116">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="54f08-116">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="54f08-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="54f08-117">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="54f08-118">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="54f08-118">Application Note:</span></span><br /><br /> <span data-ttu-id="54f08-119">Pomocí WS-Trust pro TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="54f08-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="54f08-120">K publikování</span><span class="sxs-lookup"><span data-stu-id="54f08-120">To be published</span></span>|  
|<span data-ttu-id="54f08-121">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="54f08-121">Application Note:</span></span><br /><br /> <span data-ttu-id="54f08-122">Pomocí WS-Trust pro SPNEGO</span><span class="sxs-lookup"><span data-stu-id="54f08-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="54f08-123">K publikování</span><span class="sxs-lookup"><span data-stu-id="54f08-123">To be published</span></span>|  
|<span data-ttu-id="54f08-124">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="54f08-124">Application Note:</span></span><br /><br /> <span data-ttu-id="54f08-125">Webové služby adresování Reference koncového bodu a Identity</span><span class="sxs-lookup"><span data-stu-id="54f08-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="54f08-126">K publikování</span><span class="sxs-lookup"><span data-stu-id="54f08-126">To be published</span></span>|  
|<span data-ttu-id="54f08-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="54f08-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="54f08-128">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="54f08-129">ve znění [chyby](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) odeslané do technického výboru OASIS WS-SX</span><span class="sxs-lookup"><span data-stu-id="54f08-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="54f08-130">WCF, verze 1, poskytuje 17 režimy ověřování, které můžete použít jako základ pro konfigurace zabezpečení webové služby.</span><span class="sxs-lookup"><span data-stu-id="54f08-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="54f08-131">Každý režim je optimalizovaný pro sadu běžných požadavků na nasazení, jako například:</span><span class="sxs-lookup"><span data-stu-id="54f08-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="54f08-132">Pověření pro ověření klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="54f08-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="54f08-133">Zpráva nebo přenos mechanismy ochrany zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="54f08-134">Vzorky serveru exchange zprávu.</span><span class="sxs-lookup"><span data-stu-id="54f08-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="54f08-135">Režim ověřování</span><span class="sxs-lookup"><span data-stu-id="54f08-135">Authentication Mode</span></span>|<span data-ttu-id="54f08-136">Ověření klienta</span><span class="sxs-lookup"><span data-stu-id="54f08-136">Client Authentication</span></span>|<span data-ttu-id="54f08-137">Ověřování serveru</span><span class="sxs-lookup"><span data-stu-id="54f08-137">Server Authentication</span></span>|<span data-ttu-id="54f08-138">Režim</span><span class="sxs-lookup"><span data-stu-id="54f08-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="54f08-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-139">UserNameOverTransport</span></span>|<span data-ttu-id="54f08-140">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="54f08-140">User name/password</span></span>|<span data-ttu-id="54f08-141">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-141">X509</span></span>|<span data-ttu-id="54f08-142">Přenos</span><span class="sxs-lookup"><span data-stu-id="54f08-142">Transport</span></span>|  
|<span data-ttu-id="54f08-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-143">CertificateOverTransport</span></span>|<span data-ttu-id="54f08-144">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-144">X509</span></span>|<span data-ttu-id="54f08-145">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-145">X509</span></span>|<span data-ttu-id="54f08-146">Přenos</span><span class="sxs-lookup"><span data-stu-id="54f08-146">Transport</span></span>|  
|<span data-ttu-id="54f08-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-147">KerberosOverTransport</span></span>|<span data-ttu-id="54f08-148">Windows</span><span class="sxs-lookup"><span data-stu-id="54f08-148">Windows</span></span>|<span data-ttu-id="54f08-149">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-149">X509</span></span>|<span data-ttu-id="54f08-150">Přenos</span><span class="sxs-lookup"><span data-stu-id="54f08-150">Transport</span></span>|  
|<span data-ttu-id="54f08-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="54f08-152">Federované</span><span class="sxs-lookup"><span data-stu-id="54f08-152">Federated</span></span>|<span data-ttu-id="54f08-153">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-153">X509</span></span>|<span data-ttu-id="54f08-154">Přenos</span><span class="sxs-lookup"><span data-stu-id="54f08-154">Transport</span></span>|  
|<span data-ttu-id="54f08-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="54f08-156">Windows Sspi vyjedná</span><span class="sxs-lookup"><span data-stu-id="54f08-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="54f08-157">Windows Sspi vyjedná</span><span class="sxs-lookup"><span data-stu-id="54f08-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="54f08-158">Přenos</span><span class="sxs-lookup"><span data-stu-id="54f08-158">Transport</span></span>|  
|<span data-ttu-id="54f08-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-159">AnonymousForCertificate</span></span>|<span data-ttu-id="54f08-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="54f08-160">None</span></span>|<span data-ttu-id="54f08-161">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-161">X509</span></span>|<span data-ttu-id="54f08-162">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-162">Message</span></span>|  
|<span data-ttu-id="54f08-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-163">UserNameForCertificate</span></span>|<span data-ttu-id="54f08-164">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="54f08-164">User name/password</span></span>|<span data-ttu-id="54f08-165">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-165">X509</span></span>|<span data-ttu-id="54f08-166">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-166">Message</span></span>|  
|<span data-ttu-id="54f08-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-167">MutualCertificate</span></span>|<span data-ttu-id="54f08-168">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-168">X509</span></span>|<span data-ttu-id="54f08-169">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-169">X509</span></span>|<span data-ttu-id="54f08-170">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-170">Message</span></span>|  
|<span data-ttu-id="54f08-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="54f08-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="54f08-172">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-172">X509</span></span>|<span data-ttu-id="54f08-173">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-173">X509</span></span>|<span data-ttu-id="54f08-174">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-174">Message</span></span>|  
|<span data-ttu-id="54f08-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="54f08-176">Federované</span><span class="sxs-lookup"><span data-stu-id="54f08-176">Federated</span></span>|<span data-ttu-id="54f08-177">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-177">X509</span></span>|<span data-ttu-id="54f08-178">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-178">Message</span></span>|  
|<span data-ttu-id="54f08-179">Protokol Kerberos</span><span class="sxs-lookup"><span data-stu-id="54f08-179">Kerberos</span></span>|<span data-ttu-id="54f08-180">Windows</span><span class="sxs-lookup"><span data-stu-id="54f08-180">Windows</span></span>|<span data-ttu-id="54f08-181">Windows</span><span class="sxs-lookup"><span data-stu-id="54f08-181">Windows</span></span>|<span data-ttu-id="54f08-182">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-182">Message</span></span>|  
|<span data-ttu-id="54f08-183">Třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="54f08-183">IssuedToken</span></span>|<span data-ttu-id="54f08-184">Federované</span><span class="sxs-lookup"><span data-stu-id="54f08-184">Federated</span></span>|<span data-ttu-id="54f08-185">Federované</span><span class="sxs-lookup"><span data-stu-id="54f08-185">Federated</span></span>|<span data-ttu-id="54f08-186">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-186">Message</span></span>|  
|<span data-ttu-id="54f08-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-187">SspiNegotiated</span></span>|<span data-ttu-id="54f08-188">Windows Sspi vyjedná</span><span class="sxs-lookup"><span data-stu-id="54f08-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="54f08-189">Windows Sspi vyjedná</span><span class="sxs-lookup"><span data-stu-id="54f08-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="54f08-190">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-190">Message</span></span>|  
|<span data-ttu-id="54f08-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="54f08-192">Žádné</span><span class="sxs-lookup"><span data-stu-id="54f08-192">None</span></span>|<span data-ttu-id="54f08-193">X509 TLS Nego</span><span class="sxs-lookup"><span data-stu-id="54f08-193">X509, TLS-Nego</span></span>|<span data-ttu-id="54f08-194">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-194">Message</span></span>|  
|<span data-ttu-id="54f08-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="54f08-196">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="54f08-196">User name/password</span></span>|<span data-ttu-id="54f08-197">X509 TLS Nego</span><span class="sxs-lookup"><span data-stu-id="54f08-197">X509, TLS-Nego</span></span>|<span data-ttu-id="54f08-198">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-198">Message</span></span>|  
|<span data-ttu-id="54f08-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-199">MutualSslNegotiated</span></span>|<span data-ttu-id="54f08-200">X509</span><span class="sxs-lookup"><span data-stu-id="54f08-200">X509</span></span>|<span data-ttu-id="54f08-201">X509 TLS Nego</span><span class="sxs-lookup"><span data-stu-id="54f08-201">X509, TLS-Nego</span></span>|<span data-ttu-id="54f08-202">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-202">Message</span></span>|  
|<span data-ttu-id="54f08-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="54f08-204">Federované</span><span class="sxs-lookup"><span data-stu-id="54f08-204">Federated</span></span>|<span data-ttu-id="54f08-205">X509 TLS Nego</span><span class="sxs-lookup"><span data-stu-id="54f08-205">X509, TLS-Nego</span></span>|<span data-ttu-id="54f08-206">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54f08-206">Message</span></span>|  
  
 <span data-ttu-id="54f08-207">Pomocí těchto režimů ověřování koncových bodů můžete vyjádřit svoje požadavky na zabezpečení pomocí WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="54f08-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="54f08-208">Tento dokument popisuje strukturu záhlaví zabezpečení a zprávy infrastruktury pro oba režimy ověřování a poskytuje příklady zásad a zprávy.</span><span class="sxs-lookup"><span data-stu-id="54f08-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="54f08-209">WCF využívá WS-SecureConversation zajištění zabezpečených relací podpory k ochraně výměny více zpráv mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="54f08-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="54f08-210">Podrobnosti o implementaci najdete v článku "Zabezpečené relace" níže.</span><span class="sxs-lookup"><span data-stu-id="54f08-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="54f08-211">Kromě režimů ověřování WCF obsahuje nastavení, které řídí běžné mechanismy ochrany, které se vztahují na většinu režimy ověřování na základě zabezpečení zpráv, například: pořadí podpisu a operace šifrování, algoritmus sad, odvození klíče a potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="54f08-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="54f08-212">V tomto dokumentu se používají následující předpony a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="54f08-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="54f08-213">Předpona</span><span class="sxs-lookup"><span data-stu-id="54f08-213">Prefix</span></span>|<span data-ttu-id="54f08-214">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="54f08-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="54f08-215">s</span><span class="sxs-lookup"><span data-stu-id="54f08-215">s</span></span>|<https://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="54f08-216">SP</span><span class="sxs-lookup"><span data-stu-id="54f08-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="54f08-217">a</span><span class="sxs-lookup"><span data-stu-id="54f08-217">a</span></span>|<https://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="54f08-218">wsse</span><span class="sxs-lookup"><span data-stu-id="54f08-218">wsse</span></span>|<span data-ttu-id="54f08-219">DEFINUJE – IDENTIFIKÁTOR URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="54f08-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="54f08-220">wsse11</span></span>|<span data-ttu-id="54f08-221">DEFINUJE – IDENTIFIKÁTOR URI OASIS WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="54f08-222">areálu</span><span class="sxs-lookup"><span data-stu-id="54f08-222">wsu</span></span>|<span data-ttu-id="54f08-223">Definuje – nástroj URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="54f08-224">adresářové služby</span><span class="sxs-lookup"><span data-stu-id="54f08-224">ds</span></span>|<span data-ttu-id="54f08-225">Definuje – identifikátor URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="54f08-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="54f08-226">WST</span><span class="sxs-lookup"><span data-stu-id="54f08-226">wst</span></span>|<span data-ttu-id="54f08-227">Definuje – WS-Trust 2005/02 identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="54f08-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="54f08-228">wssc</span><span class="sxs-lookup"><span data-stu-id="54f08-228">wssc</span></span>|<span data-ttu-id="54f08-229">Definuje – WS-SecureConversation 2005/02 identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="54f08-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="54f08-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="54f08-230">wsaw</span></span>|<span data-ttu-id="54f08-231">Definuje – obor názvů WS-Addressing zásad</span><span class="sxs-lookup"><span data-stu-id="54f08-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="54f08-232">soubor WSP</span><span class="sxs-lookup"><span data-stu-id="54f08-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="54f08-233">mssp</span><span class="sxs-lookup"><span data-stu-id="54f08-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="54f08-234">1. Token profily</span><span class="sxs-lookup"><span data-stu-id="54f08-234">1. Token Profiles</span></span>  
 <span data-ttu-id="54f08-235">Webové služby zabezpečení specifikace představují přihlašovací údaje jako tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="54f08-236">WCF podporuje následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="54f08-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="54f08-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="54f08-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="54f08-238">WCF následující UsernameToken10 a UsernameToken11 profily s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="54f08-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="54f08-239">Atribut R1101 PasswordType UsernameToken\Password elementu musí být vynechána, nebo mít hodnotu #PasswordText (výchozí).</span><span class="sxs-lookup"><span data-stu-id="54f08-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="54f08-240">Jeden můžete implementovat #PasswordDigest pomocí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="54f08-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="54f08-241">Bylo zjištěno, že byl #PasswordDigest často zaměněny být dostatečně zabezpečené heslo ochranný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="54f08-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="54f08-242">Ale #PasswordDigest nemůže sloužit jako náhradu šifrování UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="54f08-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="54f08-243">Hlavním cílem #PasswordDigest je ochrana proti opakované útoky.</span><span class="sxs-lookup"><span data-stu-id="54f08-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="54f08-244">V režimech ověřování WCF přehrajte útoku, které jsou pomocí podpisy zpráv zmírnit hrozby.</span><span class="sxs-lookup"><span data-stu-id="54f08-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="54f08-245">B1102 WCF nikdy vysílá Nonce and Created dílčím prvkům UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="54f08-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="54f08-246">Tyto prvky jsou určeny ke zjišťování opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="54f08-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="54f08-247">WCF použije podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="54f08-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="54f08-248">OASIS WSS protokolu SOAP zprávy zabezpečení UsernameToken Profile 1.1 (UsernameToken11) zavedla odvození klíče z funkce hesla.</span><span class="sxs-lookup"><span data-stu-id="54f08-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="54f08-249">Heslo B1103 UsernameToken nesmí se používat pro odvození klíče a proto pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="54f08-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="54f08-250">Důvody: hesla se obecně považují za příliš slabé má být použit pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="54f08-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="54f08-251">1.2 x 509 Token</span><span class="sxs-lookup"><span data-stu-id="54f08-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="54f08-252">WCF podporuje certifikáty na X509v3 jako typ přihlašovacích údajů a následuje X509TokenProfile1.0 a X509TokenProfile1.1 s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="54f08-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="54f08-253">Obsahuje certifikát X509v3 musí mít atribut R1201 The ValueType elementu BinarySecurityToken X509v3 # hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54f08-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="54f08-254">Doplněk WSS X509 Token profilu 1.0 a 1.1 definovat také #X509PKIPathv1 a PKCS7 # jako typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="54f08-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="54f08-255">WCF nepodporuje tyto typy.</span><span class="sxs-lookup"><span data-stu-id="54f08-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="54f08-256">R1202 Pokud rozšíření identifikátor klíče SubjectKeyIdentifier (subjektu) se nachází v x X509 wsse:KeyIdentifier certifikát, by měl být použit pro externí odkazy do tokenu, s typ hodnoty jako #X509SubjectKeyIdentifier a jeho obsah s kódováním base64 hodnotu atributu rozšíření identifikátor klíče subjektu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="54f08-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="54f08-257">Odkazy na identifikátor klíče subjektu jsou široce implementovat a ověřené na typ vysoce interoperabilní externího odkazu.</span><span class="sxs-lookup"><span data-stu-id="54f08-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="54f08-258">R1203 Externího odkazu na X509 ds:X509IssuerSerial zabezpečení tokenu by neměl používat.</span><span class="sxs-lookup"><span data-stu-id="54f08-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="54f08-259">Pokud X509TokenProfile1.1 R1204 se používá, externího odkazu na X509 Token zabezpečení by MĚL používat kryptografický otisk zavedené 1.1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="54f08-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="54f08-260">WCF podporuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="54f08-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="54f08-261">Nicméně existují problémy s interoperabilitou s X509IssuerSerial: WCF používá řetězec k porovnání dvou hodnot X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="54f08-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="54f08-262">Proto pokud jeden změní pořadí součástí v názvu subjektu a odesílá do služby WCF odkaz na certifikát, je nemusejí být nalezeny.</span><span class="sxs-lookup"><span data-stu-id="54f08-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="54f08-263">1.3 Token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="54f08-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="54f08-264">WCF podporuje KerberosTokenProfile1.1 za účelem ověření Windows s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="54f08-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="54f08-265">R1301 A protokolu Kerberos Token musí mít hodnotu GSS zabalené AP_REQ v4 protokolu Kerberos, jak jsou definovány v GSS_API a specifikaci protokolu Kerberos a musí mít atribut ValueType s GSS_Kerberosv5_AP_REQ # hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54f08-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="54f08-266">Použití WCF GSS zabalené AP protokolu Kerberos-REQ, není úplné Asie a Tichomoří – požadavků</span><span class="sxs-lookup"><span data-stu-id="54f08-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="54f08-267">Toto je z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="54f08-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="54f08-268">1.4 Token SAML verze 1.1</span><span class="sxs-lookup"><span data-stu-id="54f08-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="54f08-269">WCF podporuje tokenu SAML WSS profily 1.0 a 1.1 pro tokeny SAML verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="54f08-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="54f08-270">Je možné provádět další verze tokenu SAML formátů.</span><span class="sxs-lookup"><span data-stu-id="54f08-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="54f08-271">1.5 Token kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="54f08-272">WCF podporuje zabezpečení kontextu Token (SCT) počínaje WS SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="54f08-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="54f08-273">SCT se používá k reprezentování kontextu zabezpečení podle SecureConversation stejně jako binární vyjednávání protokoly TLS a SSPI, je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="54f08-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="54f08-274">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="54f08-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="54f08-275">2.1 časové razítko</span><span class="sxs-lookup"><span data-stu-id="54f08-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="54f08-276">Přítomnost časového razítka je řízen pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="54f08-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="54f08-277">WCF vždy serializuje wsse:TimeStamp s wsse: vytvořené a wsse: vypršení platnosti pole.</span><span class="sxs-lookup"><span data-stu-id="54f08-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="54f08-278">Wsse:TimeStamp je vždy podepisován při podepisování se používá.</span><span class="sxs-lookup"><span data-stu-id="54f08-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="54f08-279">2.2 pořadí ochrany</span><span class="sxs-lookup"><span data-stu-id="54f08-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="54f08-280">WCF podporuje pořadí ochrany zprávy "Znaménko před šifrování" a "Šifrovat před znak" (1.1 zásada zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="54f08-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="54f08-281">"Podepsat před šifrovat" se doporučuje důvodů včetně: zprávy chráněné pomocí šifrování před jsou otevřené vůči útokům podpis nahrazení, pokud se používá mechanismus SignatureConfirmation 1.1 WS-Security, a díky podpis přes zašifrovaný obsah auditování obtížnější.</span><span class="sxs-lookup"><span data-stu-id="54f08-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="54f08-282">2.3 podpis ochrany</span><span class="sxs-lookup"><span data-stu-id="54f08-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="54f08-283">Šifrovat před znak se používá, se doporučuje pro ochranu podpis prevenci proti útokům hrubou silou pro opakovaně uhodnout šifrovaný obsah nebo podpisový klíč (zejména při vlastní token se používá s slabé materiál klíče).</span><span class="sxs-lookup"><span data-stu-id="54f08-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="54f08-284">2.4 sada algoritmů</span><span class="sxs-lookup"><span data-stu-id="54f08-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="54f08-285">WCF podporuje všechny sady algoritmus uvedený v 1.1 zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="54f08-286">2.5 odvození klíče</span><span class="sxs-lookup"><span data-stu-id="54f08-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="54f08-287">WCF používá "Odvození klíče pro symetrické klíče", jak je popsáno v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="54f08-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="54f08-288">2.6 potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="54f08-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="54f08-289">Jako ochranu před útoky man střední k ochraně sadu podpisy může být potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="54f08-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="54f08-290">2.7 rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="54f08-291">Oba režimy ověřování popisuje rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="54f08-292">Prvky v záhlaví zabezpečení jsou částečně seřazených.</span><span class="sxs-lookup"><span data-stu-id="54f08-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="54f08-293">K definování pořadí podřízené prvky záhlaví zabezpečení, WS-Security Policy definuje následující režimy rozložení záhlaví zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="54f08-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54f08-294">Striktní</span><span class="sxs-lookup"><span data-stu-id="54f08-294">Strict</span></span>|<span data-ttu-id="54f08-295">Položky se přidají do následující záhlaví zabezpečení, že pravidla číselného rozložení popsané v zásadách zabezpečení části 7.7.1 podle obecné zásady "deklarovat před použitím".</span><span class="sxs-lookup"><span data-stu-id="54f08-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="54f08-296">Lax</span><span class="sxs-lookup"><span data-stu-id="54f08-296">Lax</span></span>|<span data-ttu-id="54f08-297">Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, který odpovídá skupině WSS: zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="54f08-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="54f08-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="54f08-298">LaxTimestampFirst</span></span>|<span data-ttu-id="54f08-299">Stejné jako Lax s tím rozdílem, že první položku v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="54f08-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="54f08-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="54f08-300">LaxTimestampLast</span></span>|<span data-ttu-id="54f08-301">Stejné jako lax s tím rozdílem, že poslední položka v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="54f08-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="54f08-302">WCF podporuje všechny čtyři režimy pro rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="54f08-303">Příklady strukturu a zpráva záhlaví zabezpečení pro režimy ověřování níže podle režimu "Strict".</span><span class="sxs-lookup"><span data-stu-id="54f08-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="54f08-304">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="54f08-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="54f08-305">Tato část poskytuje příklad zásady pro oba režimy ověřování spolu s příklady znázorňující struktura záhlaví zabezpečení zpráv mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="54f08-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="54f08-306">6.1 přenosu ochrany</span><span class="sxs-lookup"><span data-stu-id="54f08-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="54f08-307">Poskytuje pět režimy ověřování, které používají k ochraně zprávy; zabezpečeného přenosu WCF UserNameOverTransport CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="54f08-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="54f08-308">Tyto režimy ověřování jsou vytvářeny pomocí vazby přenosu je popsáno v SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="54f08-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="54f08-309">Režim ověřování UsernameToken pro UserNameOverTransport je podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="54f08-310">Token se zobrazí jako podepsaný token potvrzující pro jiné režimy ověřování.</span><span class="sxs-lookup"><span data-stu-id="54f08-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="54f08-311">Příloha C.1.2 a C.1.3 SecurityPolicy popisují podrobně rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="54f08-312">Následující příklad záhlaví zabezpečení zobrazit striktní rozložení pro režim daného ověřování.</span><span class="sxs-lookup"><span data-stu-id="54f08-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="54f08-313">Hodnota vlastnosti "Odvozené klíče" pro tokeny ve všech případech je "false".</span><span class="sxs-lookup"><span data-stu-id="54f08-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="54f08-314">Hodnoty různé vlastnosti objektu vazby přenosu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="54f08-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="54f08-315">Časové razítko: true</span><span class="sxs-lookup"><span data-stu-id="54f08-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="54f08-316">Rozložení záhlaví zabezpečení: Strict</span><span class="sxs-lookup"><span data-stu-id="54f08-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="54f08-317">Sada algoritmů: Basic256</span><span class="sxs-lookup"><span data-stu-id="54f08-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="54f08-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="54f08-319">S tímto režimem ověřování klient se ověří pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný podpůrný token, který je vždy odesílat iniciátor příjemce.</span><span class="sxs-lookup"><span data-stu-id="54f08-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="54f08-320">Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="54f08-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="54f08-321">Vazba použitá je vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="54f08-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="54f08-322">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-322">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="54f08-323">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="54f08-324">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-325">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="54f08-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="54f08-327">S tímto režimem ověřování, které klient se ověří pomocí certifikát X.509 certifikátu, která se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token, který je vždy odesílat iniciátor příjemce.</span><span class="sxs-lookup"><span data-stu-id="54f08-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="54f08-328">Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="54f08-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="54f08-329">Vazba použitá je vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="54f08-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="54f08-330">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="54f08-331">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="54f08-332">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-332">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-333">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="54f08-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="54f08-335">Tento režim ověřování klienta ověření ke službě, jako například, ale spíše uvede tokenem vydaným službou tokenů zabezpečení služby (STS) a ukáže znalost sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="54f08-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="54f08-336">Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token, který je vždy odesílat iniciátor příjemce.</span><span class="sxs-lookup"><span data-stu-id="54f08-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="54f08-337">Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="54f08-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="54f08-338">Vazba je vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="54f08-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="54f08-339">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="54f08-340">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="54f08-341">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-342">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="54f08-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="54f08-344">S tímto režimem ověřování klienta ověřuje ke službě pomocí lístek protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="54f08-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="54f08-345">Token protokolu Kerberos se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="54f08-346">Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="54f08-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="54f08-347">Vazba je vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="54f08-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="54f08-348">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="54f08-349">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="54f08-350">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-350">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-351">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="54f08-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="54f08-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="54f08-353">S tímto režimem vyjednávání protokolu slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="54f08-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="54f08-354">Protokol Kerberos se používá v případě je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="54f08-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="54f08-355">Výsledný SCT se zobrazí ve vrstvě protokolu SOAP jako podporujícími podpůrný token, který je vždy odesílat iniciátoru příjemce.</span><span class="sxs-lookup"><span data-stu-id="54f08-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="54f08-356">Služba je kromě ověřit na transportní vrstvě pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="54f08-357">Vazba použitá je vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="54f08-357">The binding used is a transport binding.</span></span> <span data-ttu-id="54f08-358">"SPNEGO" (vyjednávání) popisuje, jak WCF SSPI binární vyjednávání službou pomocí protokolu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="54f08-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="54f08-359">Příklady záhlaví zabezpečení v této části jsou po SCT se vytvořilo pomocí metody handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="54f08-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="54f08-360">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="54f08-361">Příklady záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54f08-361">Security Header Examples</span></span>  
 <span data-ttu-id="54f08-362">Jakmile Token kontextu zabezpečení se naváže prostřednictvím metody handshake SPNEGO pomocí binární vyjednávání WS-Trust, zprávy aplikace mít záhlaví zabezpečení s následující strukturou.</span><span class="sxs-lookup"><span data-stu-id="54f08-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="54f08-363">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-363">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-364">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="54f08-365">6.2 pomocí certifikátů X.509 pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="54f08-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="54f08-366">Tato část popisuje následující režimy ověřování: MutualCertificate WSS1.0, vzájemné CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="54f08-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="54f08-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="54f08-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="54f08-368">S tímto režimem ověřování, které klient se ověří pomocí certifikát X.509 certifikátu, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="54f08-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="54f08-369">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="54f08-370">Vazba použitá je asymetrický vazbu s použitím následujících hodnot vlastností:</span><span class="sxs-lookup"><span data-stu-id="54f08-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="54f08-371">Iniciátor Token: certifikát X.509 klienta, se režim zahrnutí nastavený na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="54f08-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="54f08-372">Příjemce Token: Server je certifikát X.509, režim zahrnutí je nastavena .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="54f08-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="54f08-373">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-374">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-375">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-376">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-377">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-378">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-379">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-379">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-380">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-380">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-381">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="54f08-382">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-382">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-383">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-383">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="54f08-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="54f08-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="54f08-385">S tímto režimem ověřování, které klient se ověří pomocí certifikát X.509 certifikátu, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="54f08-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="54f08-386">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="54f08-387">Vazba použitá je asymetrický vazbu s použitím následujících hodnot vlastností:</span><span class="sxs-lookup"><span data-stu-id="54f08-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="54f08-388">Iniciátor Token: Klienta X509 certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="54f08-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="54f08-389">Příjemce Token: X509 serveru certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="54f08-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="54f08-390">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-391">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-392">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-393">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-394">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-395">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-396">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-396">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-397">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-398">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-398">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="54f08-399">6.2.3 pomocí ověřování služby X.509 SymmetricBinding</span><span class="sxs-lookup"><span data-stu-id="54f08-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="54f08-400">"WSS10" poskytuje omezenou podporu pro scénáře s X509 tokeny.</span><span class="sxs-lookup"><span data-stu-id="54f08-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="54f08-401">Například neexistoval způsob, jak zajistit ochranu podpis a šifrování zpráv pomocí pouze služby X509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="54f08-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="54f08-402">"WSS11" zavedené využití EncryptedKey jako symetrický token.</span><span class="sxs-lookup"><span data-stu-id="54f08-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="54f08-403">Nyní dočasný klíč šifrována pro certifikát X.509 služby může být použita pro ochranu zprávy požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="54f08-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="54f08-404">Tento model použijte režimů ověřování je popsáno v části 6.4 níže.</span><span class="sxs-lookup"><span data-stu-id="54f08-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="54f08-405">Popisuje tento model SymmetricBinding pomocí služby WS-SecurityPolicy X509 token jako token ochrany.</span><span class="sxs-lookup"><span data-stu-id="54f08-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="54f08-406">Režimy ověřování AnonymousForCertificate UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používat podobné instance systému sp:SymmetricBinding s použitím následujících hodnot vlastností:</span><span class="sxs-lookup"><span data-stu-id="54f08-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="54f08-407">Ochrany Token: X509 serveru certifikát, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="54f08-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="54f08-408">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-409">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-410">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-411">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-412">Výše uvedené režimů ověřování se liší jenom tak podpůrných tokenů, které používají.</span><span class="sxs-lookup"><span data-stu-id="54f08-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="54f08-413">AnonymousForCertificate nemá žádné podpůrných tokenů, MutualCertificate WSS 1.1 má klienta X509 certifikátu jako podporujících podpůrnými tokeny, UserNameForCertificate má Token uživatelské jméno jako podepsaný podpůrný token a IssuedTokenForCertificate vydaný token má jako potvrzující podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="54f08-414">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-414">Policy</span></span>  
  
 <span data-ttu-id="54f08-415">Symetrický vazby</span><span class="sxs-lookup"><span data-stu-id="54f08-415">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="54f08-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="54f08-417">Klient se tento režim ověřování je anonymní a ověření služby pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="54f08-418">Vazba použitá je instancí symetrický vazbu, jak je popsáno v 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="54f08-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="54f08-419">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-419">Policy</span></span>  
  
 <span data-ttu-id="54f08-420">Viz "Zásady" v 6.2.3 výše pro podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-421">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-422">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-422">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-423">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-423">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-424">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-425">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-425">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-426">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-426">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="54f08-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="54f08-428">S tímto režimem ověřování klienta ověřuje služby pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="54f08-429">Služba se ověřuje klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="54f08-430">Vazba použitá je symetrický vazby s tokenem ochrany se klíč generované klientem zašifrován pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="54f08-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="54f08-431">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-431">Policy</span></span>  
  
 <span data-ttu-id="54f08-432">Viz "Zásady" v 6.2.3 výše pro podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="54f08-433">Podepsaný podpůrný Token</span><span class="sxs-lookup"><span data-stu-id="54f08-433">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-434">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-435">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-435">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-436">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-436">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-437">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-438">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-438">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-439">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-439">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="54f08-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="54f08-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="54f08-441">S tímto režimem ověřování, které klient se ověří pomocí certifikát X.509 certifikátu, která se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="54f08-442">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="54f08-443">Vazba použitá je symetrický vazby s tokenem ochrany se klíč generované klientem zašifrován pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="54f08-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="54f08-444">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-444">Policy</span></span>  
  
 <span data-ttu-id="54f08-445">Viz zásady v 6.2.3 pro podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="54f08-446">Potvrdit podporu Token</span><span class="sxs-lookup"><span data-stu-id="54f08-446">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-447">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-448">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-448">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-449">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-449">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-450">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-451">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-451">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-452">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-452">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="54f08-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="54f08-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="54f08-454">Pomocí tohoto ověřování režimu, který jako takové, ale místo toho se klient neověřuje ke službě, uvede tokenem vydaným službou STS a ukáže znalost sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="54f08-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="54f08-455">Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="54f08-456">Služba se ověřuje klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="54f08-457">Vazba použitá je symetrický vazby s tokenem ochrany se klíč generované klientem zašifrován pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="54f08-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="54f08-458">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-458">Policy</span></span>  
  
 <span data-ttu-id="54f08-459">Viz zásady v 6.2.3 nad podrobnosti vazby</span><span class="sxs-lookup"><span data-stu-id="54f08-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="54f08-460">Potvrdit podporu Token</span><span class="sxs-lookup"><span data-stu-id="54f08-460">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-461">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-462">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-462">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-463">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-463">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-464">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-465">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-466">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="54f08-467">6.3 protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="54f08-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="54f08-468">S tímto režimem ověřování klienta ověřuje ke službě pomocí lístek protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="54f08-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="54f08-469">Tento lístek stejné také poskytuje ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="54f08-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="54f08-470">Vazba použitá je symetrický vazby s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="54f08-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="54f08-471">Ochrana Token: Lístek protokolu Kerberos, zahrnutí režim je nastaven na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="54f08-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="54f08-472">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-473">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-474">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-475">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-476">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-476">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-477">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-478">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-478">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-479">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-479">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-480">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-481">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-482">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="54f08-483">6.4 třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="54f08-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="54f08-484">Tento režim ověřování, které klient neověřuje ke službě v důsledku toho spíše klienta uvede u tokenu vydaného službou STS a ukáže znalost sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="54f08-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="54f08-485">Služba není ověřen klientovi jako takové, místo toho šifruje Služba tokenů zabezpečení sdílený klíč jako součást vydaný token tak, aby pouze službu může dešifrovat klíč.</span><span class="sxs-lookup"><span data-stu-id="54f08-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="54f08-486">Vazba použitá se jako symetrický vazby s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="54f08-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="54f08-487">.../IncludeToken/AlwaysToRecipient ochrany Token: Vydaný Token, je nastavit režim zahrnutí</span><span class="sxs-lookup"><span data-stu-id="54f08-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="54f08-488">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-489">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-490">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-491">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-492">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-493">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-494">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-494">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-495">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-495">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-496">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-497">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-497">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-498">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-498">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="54f08-499">6.5 pomocí SslNegotiated pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="54f08-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="54f08-500">Tato část popisuje skupinu režimy ověřování, které používají symetrický vazbu s tokenem ochrany se kontext zabezpečení Token za WS-SecureConversation (WS-SC), jehož hodnota klíče se vyjedná spuštěním protokol TLS přes WS-Trust (WS-T) RVNÍ / RSTR zprávy.</span><span class="sxs-lookup"><span data-stu-id="54f08-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="54f08-501">Podrobnosti o implementaci metody handshake TLS pomocí WS-Trust jsou popsány v TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="54f08-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="54f08-502">Tady v příkladech zpráva budeme předpokládat, že je prostřednictvím ověřování metodou handshake už navázalo SCT s objekt context přidružený zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="54f08-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="54f08-503">Vazba použitá je symetrický vazby s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="54f08-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="54f08-504">Ochrana Token: SslContextToken, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="54f08-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="54f08-505">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-506">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-507">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-508">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="54f08-509">6.5.1 zásady ověřování SslNegotiated služba</span><span class="sxs-lookup"><span data-stu-id="54f08-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="54f08-510">Zásady pro všechny režimy ověřování v této části jsou podobné a liší jenom konkrétních podepsaných podpory nebo podporujících tokeny používané.</span><span class="sxs-lookup"><span data-stu-id="54f08-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="54f08-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="54f08-512">Klient se tento režim ověřování je anonymní a ověření služby pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="54f08-513">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="54f08-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="54f08-514">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-514">Policy</span></span>  
  
 <span data-ttu-id="54f08-515">V bodu 6.5.1 nad vazby podrobnosti naleznete v tématu zásady.</span><span class="sxs-lookup"><span data-stu-id="54f08-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-516">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-517">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-517">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-518">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-518">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-519">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-520">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-520">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-521">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-521">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="54f08-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="54f08-523">Pomocí tohoto ověřování režimu, který se klient ověřuje pomocí Token uživatelského jména, které se zobrazí ve vrstvě protokolu SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="54f08-524">Služba je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="54f08-525">Vazba použitá je instancí symetrický vazbu, jak je popsáno v bodu 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="54f08-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="54f08-526">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-526">Policy</span></span>  
  
 <span data-ttu-id="54f08-527">V části bodu 6.5.1 výše uvedené podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="54f08-528">Podepsaný podpůrný Token</span><span class="sxs-lookup"><span data-stu-id="54f08-528">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-529">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-530">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-530">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-531">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-531">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-532">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-533">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-533">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-534">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-534">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="54f08-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="54f08-536">Pomocí tohoto ověřování režimu, který jako takové, ale místo toho se klient neověřuje ke službě, uvede u tokenu vydaného službou STS a ukáže znalost sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="54f08-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="54f08-537">Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="54f08-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="54f08-538">Služba je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="54f08-539">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="54f08-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="54f08-540">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-540">Policy</span></span>  
  
 <span data-ttu-id="54f08-541">V části bodu 6.5.1 výše uvedené podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="54f08-542">Potvrdit podporu Token</span><span class="sxs-lookup"><span data-stu-id="54f08-542">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-543">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-544">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-544">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-545">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-545">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-546">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-547">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-547">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-548">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-548">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="54f08-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="54f08-550">S tímto režimem ověřování ověření klienta a služby pomocí certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="54f08-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="54f08-551">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="54f08-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="54f08-552">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-552">Policy</span></span>  
  
 <span data-ttu-id="54f08-553">V části bodu 6.5.1 výše uvedené podrobnosti o vazbě</span><span class="sxs-lookup"><span data-stu-id="54f08-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="54f08-554">Potvrdit podporu Token</span><span class="sxs-lookup"><span data-stu-id="54f08-554">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-555">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-556">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-556">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-557">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-557">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-558">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-559">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-559">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-560">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-560">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="54f08-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="54f08-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="54f08-562">S tímto režimem ověřování protokolu vyjednávání slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="54f08-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="54f08-563">Protokol Kerberos se používá v případě je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="54f08-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="54f08-564">Vazba použitá je symetrický vazby s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="54f08-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="54f08-565">Ochrana Token: SpnegoContextToken, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="54f08-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="54f08-566">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="54f08-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="54f08-567">Celý záhlaví a text podpisy: True</span><span class="sxs-lookup"><span data-stu-id="54f08-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="54f08-568">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="54f08-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="54f08-569">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="54f08-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="54f08-570">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-570">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-571">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-572">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-572">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-573">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-573">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-574">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-575">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-575">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-576">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-576">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="54f08-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="54f08-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="54f08-578">Vazba použitá je symetrický vazby s tokenem ochrany se SCT za WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="54f08-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="54f08-579">SCT vyjedná použití (WS-Trust) WS-Trust a WS-SecureConversation (WS-SC) podle vnořená vazba, která sama o sobě symetrický vazbu, která pomocí protokolu vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="54f08-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="54f08-580">Vyjednávání protokolu se použití protokolu Kerberos a prováděl ověřování klienta a serveru Pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="54f08-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="54f08-581">Pokud se nedá použít protokol Kerberos, ji budou přejdou na NTLM.</span><span class="sxs-lookup"><span data-stu-id="54f08-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="54f08-582">Zásady</span><span class="sxs-lookup"><span data-stu-id="54f08-582">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="54f08-583">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="54f08-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="54f08-584">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-584">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-585">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-585">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="54f08-586">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="54f08-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="54f08-587">Požadavek</span><span class="sxs-lookup"><span data-stu-id="54f08-587">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="54f08-588">Odpověď</span><span class="sxs-lookup"><span data-stu-id="54f08-588">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
