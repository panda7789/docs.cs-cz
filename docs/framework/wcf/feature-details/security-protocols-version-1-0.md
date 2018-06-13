---
title: Protokoly zabezpečení verze 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1b1e911b20ac8974dbc8cfa79e03fbd14f9beb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509174"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="ac7ae-102">Protokoly zabezpečení verze 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="ac7ae-103">Protokoly webových služeb zabezpečení zadejte mechanismy zabezpečení webové služby, které se týkají všech existujícího podnikového zasílání zpráv požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="ac7ae-104">Tato část popisuje podrobnosti Windows Communication Foundation (WCF) verze 1.0 (implementované v <xref:System.ServiceModel.Channels.SecurityBindingElement>) pro protokoly zabezpečení následující webových služeb.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="ac7ae-105">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-105">Specification/Document</span></span>|<span data-ttu-id="ac7ae-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ac7ae-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="ac7ae-107">WSS: Zabezpečení zpráv protokolu SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="ac7ae-108">WSS: Uživatelské jméno Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="ac7ae-109">WSS: X509 Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="ac7ae-110">WSS: SAML 1.1 Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="ac7ae-111">WSS: Zabezpečení zpráv SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="ac7ae-112">WSS uživatelské jméno tokenu Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="ac7ae-113">WSS: X.509 tokenu Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="ac7ae-114">WSS: Token protokolu Kerberos Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="ac7ae-115">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="ac7ae-116">WS zabezpečené konverzace</span><span class="sxs-lookup"><span data-stu-id="ac7ae-116">WS-Secure Conversation</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/|  
|<span data-ttu-id="ac7ae-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="ac7ae-117">WS-Trust</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-trust/|  
|<span data-ttu-id="ac7ae-118">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-118">Application Note:</span></span><br /><br /> <span data-ttu-id="ac7ae-119">Pomocí protokolu WS-Trust pro TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="ac7ae-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="ac7ae-120">K publikování</span><span class="sxs-lookup"><span data-stu-id="ac7ae-120">To be published</span></span>|  
|<span data-ttu-id="ac7ae-121">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-121">Application Note:</span></span><br /><br /> <span data-ttu-id="ac7ae-122">Pomocí protokolu WS-Trust pro SPNEGO</span><span class="sxs-lookup"><span data-stu-id="ac7ae-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="ac7ae-123">K publikování</span><span class="sxs-lookup"><span data-stu-id="ac7ae-123">To be published</span></span>|  
|<span data-ttu-id="ac7ae-124">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-124">Application Note:</span></span><br /><br /> <span data-ttu-id="ac7ae-125">Webové služby adresování odkazy na koncový bod a Identity</span><span class="sxs-lookup"><span data-stu-id="ac7ae-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="ac7ae-126">K publikování</span><span class="sxs-lookup"><span data-stu-id="ac7ae-126">To be published</span></span>|  
|<span data-ttu-id="ac7ae-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="ac7ae-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="ac7ae-128">(2005/07)</span></span>|http://msdn.microsoft.com/ws/2005/07/ws-security-policy/<br /><br /> <span data-ttu-id="ac7ae-129">ve znění chybující odeslána OASIS WS-SX technický výbor http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="ac7ae-129">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 <span data-ttu-id="ac7ae-130">WCF, verze 1, poskytuje 17 režimy ověřování, které lze použít jako základ pro konfigurace zabezpečení webové služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="ac7ae-131">Každý režimu je optimalizovaná pro společnou sadu požadavky na nasazení, jako například:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="ac7ae-132">Přihlašovací údaje použité k ověření klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="ac7ae-133">Zpráva nebo přenosu ochrany mechanismy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="ac7ae-134">Zpráva exchange vzory.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="ac7ae-135">Režim ověřování</span><span class="sxs-lookup"><span data-stu-id="ac7ae-135">Authentication Mode</span></span>|<span data-ttu-id="ac7ae-136">Ověření klienta</span><span class="sxs-lookup"><span data-stu-id="ac7ae-136">Client Authentication</span></span>|<span data-ttu-id="ac7ae-137">Ověření serveru</span><span class="sxs-lookup"><span data-stu-id="ac7ae-137">Server Authentication</span></span>|<span data-ttu-id="ac7ae-138">Režim</span><span class="sxs-lookup"><span data-stu-id="ac7ae-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="ac7ae-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-139">UserNameOverTransport</span></span>|<span data-ttu-id="ac7ae-140">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="ac7ae-140">User name/password</span></span>|<span data-ttu-id="ac7ae-141">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-141">X509</span></span>|<span data-ttu-id="ac7ae-142">Přenos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-142">Transport</span></span>|  
|<span data-ttu-id="ac7ae-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-143">CertificateOverTransport</span></span>|<span data-ttu-id="ac7ae-144">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-144">X509</span></span>|<span data-ttu-id="ac7ae-145">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-145">X509</span></span>|<span data-ttu-id="ac7ae-146">Přenos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-146">Transport</span></span>|  
|<span data-ttu-id="ac7ae-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-147">KerberosOverTransport</span></span>|<span data-ttu-id="ac7ae-148">Windows</span><span class="sxs-lookup"><span data-stu-id="ac7ae-148">Windows</span></span>|<span data-ttu-id="ac7ae-149">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-149">X509</span></span>|<span data-ttu-id="ac7ae-150">Přenos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-150">Transport</span></span>|  
|<span data-ttu-id="ac7ae-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="ac7ae-152">Federované</span><span class="sxs-lookup"><span data-stu-id="ac7ae-152">Federated</span></span>|<span data-ttu-id="ac7ae-153">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-153">X509</span></span>|<span data-ttu-id="ac7ae-154">Přenos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-154">Transport</span></span>|  
|<span data-ttu-id="ac7ae-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="ac7ae-156">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="ac7ae-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ac7ae-157">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="ac7ae-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ac7ae-158">Přenos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-158">Transport</span></span>|  
|<span data-ttu-id="ac7ae-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-159">AnonymousForCertificate</span></span>|<span data-ttu-id="ac7ae-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac7ae-160">None</span></span>|<span data-ttu-id="ac7ae-161">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-161">X509</span></span>|<span data-ttu-id="ac7ae-162">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-162">Message</span></span>|  
|<span data-ttu-id="ac7ae-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-163">UserNameForCertificate</span></span>|<span data-ttu-id="ac7ae-164">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="ac7ae-164">User name/password</span></span>|<span data-ttu-id="ac7ae-165">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-165">X509</span></span>|<span data-ttu-id="ac7ae-166">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-166">Message</span></span>|  
|<span data-ttu-id="ac7ae-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-167">MutualCertificate</span></span>|<span data-ttu-id="ac7ae-168">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-168">X509</span></span>|<span data-ttu-id="ac7ae-169">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-169">X509</span></span>|<span data-ttu-id="ac7ae-170">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-170">Message</span></span>|  
|<span data-ttu-id="ac7ae-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ac7ae-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="ac7ae-172">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-172">X509</span></span>|<span data-ttu-id="ac7ae-173">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-173">X509</span></span>|<span data-ttu-id="ac7ae-174">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-174">Message</span></span>|  
|<span data-ttu-id="ac7ae-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="ac7ae-176">Federované</span><span class="sxs-lookup"><span data-stu-id="ac7ae-176">Federated</span></span>|<span data-ttu-id="ac7ae-177">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-177">X509</span></span>|<span data-ttu-id="ac7ae-178">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-178">Message</span></span>|  
|<span data-ttu-id="ac7ae-179">Pomocí protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-179">Kerberos</span></span>|<span data-ttu-id="ac7ae-180">Windows</span><span class="sxs-lookup"><span data-stu-id="ac7ae-180">Windows</span></span>|<span data-ttu-id="ac7ae-181">Windows</span><span class="sxs-lookup"><span data-stu-id="ac7ae-181">Windows</span></span>|<span data-ttu-id="ac7ae-182">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-182">Message</span></span>|  
|<span data-ttu-id="ac7ae-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ac7ae-183">IssuedToken</span></span>|<span data-ttu-id="ac7ae-184">Federované</span><span class="sxs-lookup"><span data-stu-id="ac7ae-184">Federated</span></span>|<span data-ttu-id="ac7ae-185">Federované</span><span class="sxs-lookup"><span data-stu-id="ac7ae-185">Federated</span></span>|<span data-ttu-id="ac7ae-186">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-186">Message</span></span>|  
|<span data-ttu-id="ac7ae-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-187">SspiNegotiated</span></span>|<span data-ttu-id="ac7ae-188">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="ac7ae-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ac7ae-189">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="ac7ae-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ac7ae-190">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-190">Message</span></span>|  
|<span data-ttu-id="ac7ae-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="ac7ae-192">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac7ae-192">None</span></span>|<span data-ttu-id="ac7ae-193">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="ac7ae-193">X509, TLS-Nego</span></span>|<span data-ttu-id="ac7ae-194">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-194">Message</span></span>|  
|<span data-ttu-id="ac7ae-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="ac7ae-196">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="ac7ae-196">User name/password</span></span>|<span data-ttu-id="ac7ae-197">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="ac7ae-197">X509, TLS-Nego</span></span>|<span data-ttu-id="ac7ae-198">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-198">Message</span></span>|  
|<span data-ttu-id="ac7ae-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-199">MutualSslNegotiated</span></span>|<span data-ttu-id="ac7ae-200">X509</span><span class="sxs-lookup"><span data-stu-id="ac7ae-200">X509</span></span>|<span data-ttu-id="ac7ae-201">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="ac7ae-201">X509, TLS-Nego</span></span>|<span data-ttu-id="ac7ae-202">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-202">Message</span></span>|  
|<span data-ttu-id="ac7ae-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="ac7ae-204">Federované</span><span class="sxs-lookup"><span data-stu-id="ac7ae-204">Federated</span></span>|<span data-ttu-id="ac7ae-205">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="ac7ae-205">X509, TLS-Nego</span></span>|<span data-ttu-id="ac7ae-206">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac7ae-206">Message</span></span>|  
  
 <span data-ttu-id="ac7ae-207">Koncové body pomocí těchto režimech ověřování můžete express jejich požadavky na zabezpečení pomocí protokolu WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="ac7ae-208">Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a obsahuje příklady zásad a zprávy.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="ac7ae-209">WCF využívá WS-SecureConversation pro poskytování zabezpečených relací podpory k ochraně výměny více zpráv mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="ac7ae-210">Podrobné informace o nasazení naleznete v tématu "Zabezpečené relace" níže.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="ac7ae-211">Kromě režimy ověřování WCF nabízí nastavení, které řídí obecné ochrany mechanismy, které se vztahují na většinu režimy ověřování na základě zabezpečení zpráv, například: pořadí podpis a šifrování, algoritmus sady, odvození klíče a potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="ac7ae-212">V tomto dokumentu se používají následující předpony a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="ac7ae-213">Předpona</span><span class="sxs-lookup"><span data-stu-id="ac7ae-213">Prefix</span></span>|<span data-ttu-id="ac7ae-214">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ac7ae-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ac7ae-215">s</span><span class="sxs-lookup"><span data-stu-id="ac7ae-215">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="ac7ae-216">SP</span><span class="sxs-lookup"><span data-stu-id="ac7ae-216">sp</span></span>|http://schemas.xmlsoap.org/ws/2005/07/securitypolicy|  
|<span data-ttu-id="ac7ae-217">a</span><span class="sxs-lookup"><span data-stu-id="ac7ae-217">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="ac7ae-218">wsse</span><span class="sxs-lookup"><span data-stu-id="ac7ae-218">wsse</span></span>|<span data-ttu-id="ac7ae-219">BUDE URČENO – IDENTIFIKÁTOR URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="ac7ae-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="ac7ae-220">wsse11</span></span>|<span data-ttu-id="ac7ae-221">BUDE URČENO – IDENTIFIKÁTOR URI OASIS WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="ac7ae-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="ac7ae-222">týkajících</span><span class="sxs-lookup"><span data-stu-id="ac7ae-222">wsu</span></span>|<span data-ttu-id="ac7ae-223">Bude určeno – nástroj URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="ac7ae-224">DS</span><span class="sxs-lookup"><span data-stu-id="ac7ae-224">ds</span></span>|<span data-ttu-id="ac7ae-225">Bude určeno – identifikátor URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="ac7ae-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="ac7ae-226">WST</span><span class="sxs-lookup"><span data-stu-id="ac7ae-226">wst</span></span>|<span data-ttu-id="ac7ae-227">Bude určeno – WS-Trust 2005/02 identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="ac7ae-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="ac7ae-228">wssc</span><span class="sxs-lookup"><span data-stu-id="ac7ae-228">wssc</span></span>|<span data-ttu-id="ac7ae-229">Bude určeno – WS-SecureConversation 2005/02 identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="ac7ae-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="ac7ae-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="ac7ae-230">wsaw</span></span>|<span data-ttu-id="ac7ae-231">Bude určeno - WS-Addressing zásad obor názvů</span><span class="sxs-lookup"><span data-stu-id="ac7ae-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="ac7ae-232">WSP</span><span class="sxs-lookup"><span data-stu-id="ac7ae-232">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="ac7ae-233">mssp</span><span class="sxs-lookup"><span data-stu-id="ac7ae-233">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="ac7ae-234">1. Token profily</span><span class="sxs-lookup"><span data-stu-id="ac7ae-234">1. Token Profiles</span></span>  
 <span data-ttu-id="ac7ae-235">Webové služby zabezpečení specifikace představují přihlašovací údaje jako tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="ac7ae-236">WCF podporuje následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="ac7ae-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="ac7ae-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="ac7ae-238">WCF se skládá z UsernameToken10 a UsernameToken11 profily s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="ac7ae-239">Atribut R1101 PasswordType UsernameToken\Password elementu musí být buď vynechána, nebo musí mít hodnotu #PasswordText (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="ac7ae-240">Jeden můžete implementovat #PasswordDigest pomocí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="ac7ae-241">Bylo zjištěno, že byl #PasswordDigest často zaměněny být dostatečně zabezpečeného hesla ochranný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="ac7ae-242">Ale #PasswordDigest nemůže sloužit jako náhrada pro šifrování UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="ac7ae-243">Primární cílem #PasswordDigest je ochrana proti útoku formou opakovaného.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="ac7ae-244">V WCF režimy ověřování jsou zmírnit hrozby útoku formou opakovaného přehrávání použitím podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="ac7ae-245">B1102 WCF nikdy vysílá hodnotu Nonce a vytvořen dílčí prvky UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="ac7ae-246">Tyto prvky jsou určeny ke zjišťování opakování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="ac7ae-247">WCF použije podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="ac7ae-248">OASIS WSS protokolu SOAP zprávy zabezpečení UsernameToken Profile 1.1 (UsernameToken11) zavedla odvození klíče z funkce hesla.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="ac7ae-249">Heslo B1103 UsernameToken nesmí se používat pro odvození klíče a proto pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="ac7ae-250">Odůvodnění: hesla jsou obvykle považovány za příliš slabé má být použit pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="ac7ae-251">1.2 x 509 tokenu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="ac7ae-252">WCF podporuje certifikáty X509v3 jako typ přihlašovacích údajů a dodržuje X509TokenProfile1.0 a X509TokenProfile1.1 s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="ac7ae-253">Atribut R1201 The typ hodnoty v elementu BinarySecurityToken musí mít hodnotu #X509v3 obsahuje certifikát X509v3.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="ac7ae-254">WSS X509 tokenu profil 1.0 a 1.1 definovat také #X509PKIPathv1 a PKCS7 # jako typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="ac7ae-255">WCF nepodporuje tyto typy.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="ac7ae-256">R1202 Pokud rozšíření identifikátor klíče SubjectKeyIdentifier (subjektu) se nachází v X509 certifikát, by měl být wsse:KeyIdentifier používá pro externí odkazy na token, s typ hodnoty atributu jako #X509SubjectKeyIdentifier a jejího obsahu hodnota kódováním Base 64 rozšíření identifikátor klíče subjektu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="ac7ae-257">Identifikátor klíče subjektu odkazy jsou široce implementována a ověřené jako vysoce interoperabilní externí odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="ac7ae-258">R1203 Externího odkazu na X509 zabezpečení tokenu by MĚL používat ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="ac7ae-259">Pokud X509TokenProfile1.1 R1204 se používá, externí odkaz na X509 tokenu zabezpečení by MĚL použít kryptografický otisk zaváděné WS-zabezpečení 1.1.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="ac7ae-260">WCF podporuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="ac7ae-261">Problémy s interoperabilitou s X509IssuerSerial se však: WCF používá k porovnání dvou hodnot X509IssuerSerial řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="ac7ae-262">Proto pokud jeden změní součástí název předmětu a odesílá do služby WCF odkaz na certifikát, se nemusí být nalezen.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="ac7ae-263">1.3 Token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="ac7ae-264">WCF podporuje KerberosTokenProfile1.1 pro účely ověřování systému Windows s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="ac7ae-265">R1301 A protokolu Kerberos Token musí mít hodnotu GSS zabalená AP_REQ v4 protokolu Kerberos, jak jsou definovány v GSS_API a specifikace protokolu Kerberos a musí mít atribut ValueType s GSS_Kerberosv5_AP_REQ # hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="ac7ae-266">Používá WCF GSS zabalené AP protokolu Kerberos-REQ, není úplné Asie-požadavků</span><span class="sxs-lookup"><span data-stu-id="ac7ae-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="ac7ae-267">Toto je nejlepším postupem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="ac7ae-268">1.4 SAML v1.1 Token</span><span class="sxs-lookup"><span data-stu-id="ac7ae-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="ac7ae-269">WCF podporuje tokenu SAML WSS profily 1.0 a 1.1 pro tokeny SAML verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="ac7ae-270">Je možné implementovat jiných verzích formáty tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="ac7ae-271">1.5 Token kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="ac7ae-272">WCF podporuje zabezpečení kontextu tokenu (SCT) byla zavedená v WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="ac7ae-273">SCT se používá k reprezentování kontextu zabezpečení nastavené v SecureConversation také jako binární vyjednávání protokoly TLS a rozhraní SSPI, které jsou popsané dál.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ac7ae-274">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="ac7ae-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="ac7ae-275">2.1 časové razítko</span><span class="sxs-lookup"><span data-stu-id="ac7ae-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="ac7ae-276">Přítomnost časového razítka je řízena pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="ac7ae-277">WCF vždy serializuje wsse:TimeStamp s wsse: vytvoření a wsse: vyprší platnost pole.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="ac7ae-278">Při podepisování se používá, je vždy podepisován wsse:TimeStamp.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="ac7ae-279">2.2 ochrany pořadí</span><span class="sxs-lookup"><span data-stu-id="ac7ae-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="ac7ae-280">WCF podporuje pořadí ochrany zprávy "Přihlášení před šifrování" a "Šifrovat před přihlášení" (1.1 zásady zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="ac7ae-281">"Podepsat před šifrovat" se doporučuje důvodů včetně: zprávy chráněné pomocí šifrování před přihlašovacích jsou otevřené podpis nahrazení útoky, pokud se používá mechanismus SignatureConfirmation 1.1 WS-zabezpečení a umožňuje podpis přes šifrovaný obsah těžší auditování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="ac7ae-282">2.3 podpis ochrany</span><span class="sxs-lookup"><span data-stu-id="ac7ae-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="ac7ae-283">Pokud se používá šifrování před přihlášení, se doporučuje k ochraně podpis před útoky hrubou silou pro uhodnutí šifrovaný obsah nebo podpisový klíč (zejména při vlastního tokenu se používá s slabé materiál klíče).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="ac7ae-284">2.4 algoritmus Suite</span><span class="sxs-lookup"><span data-stu-id="ac7ae-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="ac7ae-285">WCF podporuje všechny sady algoritmus uvedené v 1.1 zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="ac7ae-286">2.5 odvození klíče</span><span class="sxs-lookup"><span data-stu-id="ac7ae-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="ac7ae-287">WCF používá "Klíč odvození symetrické klíče", jak je popsáno v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="ac7ae-288">2.6 potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="ac7ae-289">Potvrzení podpisu může být jako ochranu před útoky střední man k ochraně sadu podpisy.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="ac7ae-290">2.7 rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="ac7ae-291">Každý režim ověřování popisuje rozložení pro záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="ac7ae-292">Prvky v záhlaví zabezpečení jsou polovičním seřazené.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="ac7ae-293">Pokud chcete definovat pořadí podřízených elementů záhlaví zabezpečení, zásady zabezpečení WS definuje v následujících režimech rozložení záhlaví zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac7ae-294">Striktní</span><span class="sxs-lookup"><span data-stu-id="ac7ae-294">Strict</span></span>|<span data-ttu-id="ac7ae-295">Položky budou přidány do těchto záhlaví zabezpečení, že pravidla číslem rozložení popsané v zásadách zabezpečení části 7.7.1 podle obecné Princip "deklarovat před použitím".</span><span class="sxs-lookup"><span data-stu-id="ac7ae-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="ac7ae-296">Hodnotě lax</span><span class="sxs-lookup"><span data-stu-id="ac7ae-296">Lax</span></span>|<span data-ttu-id="ac7ae-297">Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, které vyhovuje WSS: zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="ac7ae-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="ac7ae-298">LaxTimestampFirst</span></span>|<span data-ttu-id="ac7ae-299">Stejné jako Lax s tím rozdílem, že první položky v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="ac7ae-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="ac7ae-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="ac7ae-300">LaxTimestampLast</span></span>|<span data-ttu-id="ac7ae-301">Stejné jako hodnotě lax s tím rozdílem, že poslední položky v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="ac7ae-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="ac7ae-302">WCF podporuje všechny čtyři režimy pro rozvržení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="ac7ae-303">Příklady strukturu a zpráva záhlaví zabezpečení pro režimy ověřování níže podle režim "Strict".</span><span class="sxs-lookup"><span data-stu-id="ac7ae-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ac7ae-304">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="ac7ae-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="ac7ae-305">Tato část obsahuje příklady zásad pro každý režim ověřování spolu s příklady zobrazující struktura záhlaví zabezpečení v zprávy vyměňují klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="ac7ae-306">6.1 přenosu ochrany</span><span class="sxs-lookup"><span data-stu-id="ac7ae-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="ac7ae-307">WCF obsahuje pět režimy ověřování, které používají zabezpečené přenos k ochraně zprávy; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="ac7ae-308">Tyto režimy ověřování jsou vytvářeny pomocí popsaných v SecurityPolicy vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="ac7ae-309">Režim ověřování UsernameToken UserNameOverTransport je podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="ac7ae-310">Pro další režimy ověřování tokenu zobrazí jako podepsaný token či identifikaci.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="ac7ae-311">Příloha C.1.2 a C.1.3 SecurityPolicy popisují rozvržení záhlaví zabezpečení podrobně.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="ac7ae-312">Následující příklad hlavičky zabezpečení zobrazit striktní rozložení pro režim daného ověřování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="ac7ae-313">Hodnota vlastnosti "Odvozené klíče" pro tokeny ve všech případech je "false".</span><span class="sxs-lookup"><span data-stu-id="ac7ae-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="ac7ae-314">Hodnoty různé vlastnosti vazby přenosu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="ac7ae-315">Časové razítko: true</span><span class="sxs-lookup"><span data-stu-id="ac7ae-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="ac7ae-316">Rozvržení záhlaví zabezpečení: striktní</span><span class="sxs-lookup"><span data-stu-id="ac7ae-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="ac7ae-317">Algoritmus Suite: Basic256</span><span class="sxs-lookup"><span data-stu-id="ac7ae-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="ac7ae-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="ac7ae-319">Tento režim ověřování klient se ověří uživatelské jméno tokenem, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token vždy odeslané ze iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ac7ae-320">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ac7ae-321">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ac7ae-322">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-323">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="ac7ae-324">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-324">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-325">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="ac7ae-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="ac7ae-327">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako či identifikaci podpůrné token, který se vždy odesílá z iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ac7ae-328">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ac7ae-329">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ac7ae-330">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-331">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="ac7ae-332">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-332">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-333">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="ac7ae-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="ac7ae-335">S Tento režim ověřování klienta služby, jako například neověřuje, ale místo uvede tokenem vydaným podle zabezpečení tokenu služby (STS) a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="ac7ae-336">Vystavený token se zobrazí ve vrstvě protokolu SOAP či identifikaci podpůrné token, který se vždy odesílá z iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ac7ae-337">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ac7ae-338">Vazba je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ac7ae-339">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-340">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="ac7ae-341">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-341">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-342">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="ac7ae-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="ac7ae-344">Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ac7ae-345">Token protokolu Kerberos se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ac7ae-346">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ac7ae-347">Vazba je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ac7ae-348">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-349">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="ac7ae-350">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-350">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-351">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="ac7ae-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ac7ae-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="ac7ae-353">Pomocí tohoto režimu vyjednávání protokolu slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ac7ae-354">Pokud je to možné, používá protokol Kerberos jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ac7ae-355">Výsledný SCT se zobrazí ve vrstvě protokolu SOAP či identifikaci token podpory, který se vždy odesílá z iniciátor k příjemce.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="ac7ae-356">Služba je kromě ověřit v přenosové vrstvě certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-357">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-357">The binding used is a transport binding.</span></span> <span data-ttu-id="ac7ae-358">"SPNEGO" (vyjednávání) popisuje, jak WCF používá rozhraní SSPI binární vyjednávání protokolu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="ac7ae-359">Příklady záhlaví zabezpečení v této části jsou po navázání SCT prostřednictvím SPNEGO handshake.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="ac7ae-360">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="ac7ae-361">Příklady záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ac7ae-361">Security Header Examples</span></span>  
 <span data-ttu-id="ac7ae-362">Jakmile tokenu kontextu zabezpečení vytvořeno prostřednictvím metody handshake SPNEGO binární vyjednání WS-Trust, zprávy aplikací mít záhlaví zabezpečení s následující strukturou.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="ac7ae-363">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-363">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-364">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="ac7ae-365">6.2 pomocí certifikátů X.509 pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ac7ae-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="ac7ae-366">Tato část popisuje následující režimy ověřování: MutualCertificate WSS1.0, vzájemné CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="ac7ae-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="ac7ae-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="ac7ae-368">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ac7ae-369">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ac7ae-370">Vazba použitá je asymetrické vazbu s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ac7ae-371">Token iniciátor: certifikát X.509 klienta, s zahrnutí režim nastavený na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ac7ae-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ac7ae-372">Příjemce Token: Server je certifikát X.509, s režimem zahrnutí nastavena .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ac7ae-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="ac7ae-373">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-374">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-375">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-376">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-377">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-378">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-379">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-379">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-380">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-380">Response</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-381">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="ac7ae-382">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-382">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-383">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="ac7ae-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ac7ae-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="ac7ae-385">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ac7ae-386">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ac7ae-387">Vazba použitá je asymetrické vazbu s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ac7ae-388">Token iniciátor: Klienta X509 certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ac7ae-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ac7ae-389">Příjemce Token: Serveru X509 certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="ac7ae-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="ac7ae-390">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-391">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-392">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-393">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-394">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-395">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-396">Žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="ac7ae-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-397">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-398">Žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="ac7ae-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="ac7ae-399">6.2.3 pomocí ověřování služby X.509 SymmetricBinding</span><span class="sxs-lookup"><span data-stu-id="ac7ae-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="ac7ae-400">"WSS10" k dispozici omezená podpora pro scénáře s X509 tokeny.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="ac7ae-401">Například se žádný způsob, jak zajistit ochranu podpis a šifrování zpráv pomocí pouze token služby X509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="ac7ae-402">"WSS11" uvedla využití EncryptedKey symetrický token.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="ac7ae-403">Nyní na dočasný klíč šifrována pro certifikát X.509 služby může být použita pro ochranu zprávy požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="ac7ae-404">Režimy ověřování, který je popsaný v části 6.4 níže pomocí tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="ac7ae-405">Popisuje tento vzor SymmetricBinding pomocí služby WS-SecurityPolicy X509 token jako token ochrany.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="ac7ae-406">Režimy ověřování AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používat podobné instance sp:SymmetricBinding s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="ac7ae-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="ac7ae-407">Ochrany Token: X509 serveru certifikát, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ac7ae-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ac7ae-408">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-409">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-410">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-411">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-412">Výše uvedené režimy ověřování podpůrné tokeny, které používají pouze lišit.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="ac7ae-413">AnonymousForCertificate nemá všechny podpůrné tokeny, MutualCertificate WSS 1.1 má klienta X509 certifikátu jako potvrzování podpora tokenů, UserNameForCertificate má Token uživatelské jméno jako podepsaný token a IssuedTokenForCertificate má vystavený token jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="ac7ae-414">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-414">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-415">Symetrické vazby</span><span class="sxs-lookup"><span data-stu-id="ac7ae-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="ac7ae-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="ac7ae-417">S Tento režim ověřování je anonymní klienta a služby je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-418">Vazba použitá instance symetrický vazby je, jak je popsáno v 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="ac7ae-419">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-419">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-420">Pro vytvoření vazby podrobnosti najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="ac7ae-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-421">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-422">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-422">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-423">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-424">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-425">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-425">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-426">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="ac7ae-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="ac7ae-428">Klient se ověří do služby pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ac7ae-429">Služba se ověřuje na klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-430">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ac7ae-431">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-431">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-432">Pro vytvoření vazby podrobnosti najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="ac7ae-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-433">Podepsaný Token podpory</span><span class="sxs-lookup"><span data-stu-id="ac7ae-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-434">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-435">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-435">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-436">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-437">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-438">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-438">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-439">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="ac7ae-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="ac7ae-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="ac7ae-441">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ac7ae-442">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-443">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ac7ae-444">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-444">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-445">Viz zásady v 6.2.3 pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac7ae-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-446">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-447">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-448">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-448">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-449">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-450">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-451">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-451">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-452">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="ac7ae-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ac7ae-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="ac7ae-454">Pomocí tohoto ověřování režim, který jako takový, ale místo toho se ke službě, neověřuje klient uvede tokenem vydaným službou tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ac7ae-455">Vystavený token se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ac7ae-456">Služba se ověřuje na klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-457">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ac7ae-458">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-458">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-459">Viz zásady v 6.2.3 výše podrobnosti vazby</span><span class="sxs-lookup"><span data-stu-id="ac7ae-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-460">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-461">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-462">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-462">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-463">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-464">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-465">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-465">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-466">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="ac7ae-467">6.3 protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ac7ae-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="ac7ae-468">Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ac7ae-469">Tento stejný lístek taky poskytuje ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="ac7ae-470">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="ac7ae-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ac7ae-471">Ochrana Token: Lístek protokolu Kerberos, zahrnutí režim je nastaven na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="ac7ae-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="ac7ae-472">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-473">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-474">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-475">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-476">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-477">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-478">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-478">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-479">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-480">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-481">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="ac7ae-482">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="ac7ae-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ac7ae-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="ac7ae-484">S Tento režim ověřování, které klient neověřuje ke službě jako například místo klienta uvede tokenem vydaným pomocí služby tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ac7ae-485">Služba není ověřen klientovi jako takový, místo toho šifruje Služba tokenů zabezpečení sdílený klíč jako součást vydaný token tak, aby pouze služby může dešifrovat klíč.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="ac7ae-486">Vazba použitá se jako symetrický vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="ac7ae-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ac7ae-487">Ochrana Token: Vydán Token, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ac7ae-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ac7ae-488">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-489">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-490">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-491">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-492">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-493">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-494">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-494">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-495">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-496">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-497">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-497">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-498">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="ac7ae-499">6.5 pomocí SslNegotiated pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ac7ae-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="ac7ae-500">Tato část popisuje režimy ověřování, které symetrický vazbu pomocí tokenu ochrany se kontextu zabezpečení tokenu za WS-SecureConversation (WS-SC), jehož hodnota klíče vyjedná spuštěním protokol TLS přes WS-Trust (WS-T) RVNÍ skupinu nebo RSTR zprávy.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="ac7ae-501">Podrobnosti o implementaci TLS handshake pomocí WS-Trust jsou popsané v TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="ac7ae-502">Zde v příkladech zpráva budeme předpokládat, SCT s kontextu zabezpečení je již navázáno prostřednictvím provádění metody handshake.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="ac7ae-503">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="ac7ae-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ac7ae-504">Ochrana Token: SslContextToken, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ac7ae-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ac7ae-505">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-506">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-507">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-508">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="ac7ae-509">6.5.1 zásady pro ověřování služby SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="ac7ae-510">Zásady pro všechny režimy ověřování v této části jsou podobné a liší pouze konkrétní podpora podepsaný držitelem nebo potvrdit správnost použití tokenů.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="ac7ae-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="ac7ae-512">S Tento režim ověřování je anonymní klienta a služby je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-513">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ac7ae-514">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-514">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-515">Viz zásady v bodu 6.5.1 výše podrobnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-516">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-517">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-517">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-518">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-519">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-520">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-520">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-521">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="ac7ae-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="ac7ae-523">Pomocí tohoto ověřování režim, který je klient ověřování pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ac7ae-524">Služba je ověřen pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-525">Vazba použitá instance symetrický vazby je, jak je popsáno v bodu 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="ac7ae-526">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-526">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-527">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac7ae-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-528">Podepsaný Token podpory</span><span class="sxs-lookup"><span data-stu-id="ac7ae-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-529">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-530">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-530">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-531">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-532">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-533">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-533">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-534">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="ac7ae-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="ac7ae-536">Pomocí tohoto ověřování režim, který jako takový, ale místo toho se ke službě, neověřuje klient uvede tokenem vydaným pomocí služby tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ac7ae-537">Vystavený token se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ac7ae-538">Služba je ověřen pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ac7ae-539">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ac7ae-540">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-540">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-541">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac7ae-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-542">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-543">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-544">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-544">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-545">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-546">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-547">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-547">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-548">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="ac7ae-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="ac7ae-550">S Tento režim ověřování klienta a služby je ověřování pomocí certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="ac7ae-551">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ac7ae-552">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-552">Policy</span></span>  
  
 <span data-ttu-id="ac7ae-553">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac7ae-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ac7ae-554">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="ac7ae-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-555">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-556">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-556">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-557">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-558">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-559">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-559">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-560">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="ac7ae-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ac7ae-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="ac7ae-562">S Tento režim ověřování vyjednávání protokolu slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ac7ae-563">Pokud je to možné, používá protokol Kerberos jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ac7ae-564">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="ac7ae-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ac7ae-565">Ochrana Token: SpnegoContextToken, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ac7ae-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ac7ae-566">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="ac7ae-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="ac7ae-567">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ac7ae-568">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ac7ae-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ac7ae-569">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="ac7ae-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ac7ae-570">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-571">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-572">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-572">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-573">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-574">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-575">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-575">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-576">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="ac7ae-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="ac7ae-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="ac7ae-578">Vazba použitá je symetrický vazbu s tokenem ochrany se SCT za WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="ac7ae-579">SCT vyjedná použití podle vnořené vazby, které je samo symetrický vazbu, která používá vyjednávání protokolu WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="ac7ae-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="ac7ae-580">Vyjednávání protokolu budou používat protokol Kerberos k provedení ověřování klienta a serveru, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="ac7ae-581">Pokud nemůžete používat Kerberos, ji budou vrátit k protokolu NTLM.</span><span class="sxs-lookup"><span data-stu-id="ac7ae-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="ac7ae-582">Zásady</span><span class="sxs-lookup"><span data-stu-id="ac7ae-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ac7ae-583">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ac7ae-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ac7ae-584">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-584">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-585">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ac7ae-586">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ac7ae-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ac7ae-587">Požadavek</span><span class="sxs-lookup"><span data-stu-id="ac7ae-587">Request</span></span>  
  
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
  
 <span data-ttu-id="ac7ae-588">Odpověď</span><span class="sxs-lookup"><span data-stu-id="ac7ae-588">Response</span></span>  
  
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
