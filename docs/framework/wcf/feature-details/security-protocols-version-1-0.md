---
title: Protokoly zabezpečení verze 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 2014e1f6f8fefa89ed44bd820c3712617ff51470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184515"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="30633-102">Protokoly zabezpečení verze 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="30633-103">Protokoly zabezpečení webových služeb poskytují mechanismy zabezpečení webových služeb, které pokrývají všechny existující požadavky na zabezpečení podnikových zpráv.</span><span class="sxs-lookup"><span data-stu-id="30633-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="30633-104">Tato část popisuje podrobnosti wcf (Windows Communication Foundation) verze <xref:System.ServiceModel.Channels.SecurityBindingElement>1.0 (implementované v ) pro následující protokoly zabezpečení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="30633-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="30633-105">Specifikace/dokument</span><span class="sxs-lookup"><span data-stu-id="30633-105">Specification/Document</span></span>|<span data-ttu-id="30633-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="30633-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="30633-107">WSS: Zabezpečení zpráv SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="30633-108">WSS: Profil uživatelského tokenu 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="30633-109">WSS: X509 Profil tokenu 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="30633-110">WSS: SAML 1.1 Profil tokenu 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="30633-111">WSS: Zabezpečení zpráv SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="30633-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="30633-112">Profil tokenu uživatelského jména WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="30633-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="30633-113">WSS: X.509 Profil tokenu 1.1</span><span class="sxs-lookup"><span data-stu-id="30633-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="30633-114">WSS: Profil tokenu Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="30633-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="30633-115">WSS: SAML 1.1 Profil tokenu 1.1</span><span class="sxs-lookup"><span data-stu-id="30633-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="30633-116">Konverzace zabezpečená v ws</span><span class="sxs-lookup"><span data-stu-id="30633-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="30633-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="30633-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="30633-118">Aplikační poznámka:</span><span class="sxs-lookup"><span data-stu-id="30633-118">Application Note:</span></span><br /><br /> <span data-ttu-id="30633-119">Použití ws-trust pro tls handshake</span><span class="sxs-lookup"><span data-stu-id="30633-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="30633-120">Bude zveřejněno</span><span class="sxs-lookup"><span data-stu-id="30633-120">To be published</span></span>|  
|<span data-ttu-id="30633-121">Aplikační poznámka:</span><span class="sxs-lookup"><span data-stu-id="30633-121">Application Note:</span></span><br /><br /> <span data-ttu-id="30633-122">Použití ws-trust pro SPNEGO</span><span class="sxs-lookup"><span data-stu-id="30633-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="30633-123">Bude zveřejněno</span><span class="sxs-lookup"><span data-stu-id="30633-123">To be published</span></span>|  
|<span data-ttu-id="30633-124">Aplikační poznámka:</span><span class="sxs-lookup"><span data-stu-id="30633-124">Application Note:</span></span><br /><br /> <span data-ttu-id="30633-125">Webové služby adresování odkazů koncových bodů a identity</span><span class="sxs-lookup"><span data-stu-id="30633-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="30633-126">Bude zveřejněno</span><span class="sxs-lookup"><span data-stu-id="30633-126">To be published</span></span>|  
|<span data-ttu-id="30633-127">WS-Bezpečnostní politika 1,1</span><span class="sxs-lookup"><span data-stu-id="30633-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="30633-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="30633-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="30633-129">ve znění ve znění [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) předloženého Technickému výboru OASIS WS-SX</span><span class="sxs-lookup"><span data-stu-id="30633-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="30633-130">WCF, verze 1, poskytuje 17 režimů ověřování, které lze použít jako základ pro konfiguraci zabezpečení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="30633-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="30633-131">Každý režim je optimalizován pro společnou sadu požadavků na nasazení, například:</span><span class="sxs-lookup"><span data-stu-id="30633-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="30633-132">Pověření používaná k ověření klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="30633-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="30633-133">Mechanismy ochrany zabezpečení zpráv nebo přenosu.</span><span class="sxs-lookup"><span data-stu-id="30633-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="30633-134">Vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="30633-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="30633-135">Režim ověřování</span><span class="sxs-lookup"><span data-stu-id="30633-135">Authentication Mode</span></span>|<span data-ttu-id="30633-136">Ověření klienta</span><span class="sxs-lookup"><span data-stu-id="30633-136">Client Authentication</span></span>|<span data-ttu-id="30633-137">Ověřování serveru</span><span class="sxs-lookup"><span data-stu-id="30633-137">Server Authentication</span></span>|<span data-ttu-id="30633-138">Mode</span><span class="sxs-lookup"><span data-stu-id="30633-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="30633-139">UserNameoverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-139">UserNameOverTransport</span></span>|<span data-ttu-id="30633-140">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="30633-140">User name/password</span></span>|<span data-ttu-id="30633-141">X509</span><span class="sxs-lookup"><span data-stu-id="30633-141">X509</span></span>|<span data-ttu-id="30633-142">Přenos</span><span class="sxs-lookup"><span data-stu-id="30633-142">Transport</span></span>|  
|<span data-ttu-id="30633-143">CertificateoverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-143">CertificateOverTransport</span></span>|<span data-ttu-id="30633-144">X509</span><span class="sxs-lookup"><span data-stu-id="30633-144">X509</span></span>|<span data-ttu-id="30633-145">X509</span><span class="sxs-lookup"><span data-stu-id="30633-145">X509</span></span>|<span data-ttu-id="30633-146">Přenos</span><span class="sxs-lookup"><span data-stu-id="30633-146">Transport</span></span>|  
|<span data-ttu-id="30633-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-147">KerberosOverTransport</span></span>|<span data-ttu-id="30633-148">Windows</span><span class="sxs-lookup"><span data-stu-id="30633-148">Windows</span></span>|<span data-ttu-id="30633-149">X509</span><span class="sxs-lookup"><span data-stu-id="30633-149">X509</span></span>|<span data-ttu-id="30633-150">Přenos</span><span class="sxs-lookup"><span data-stu-id="30633-150">Transport</span></span>|  
|<span data-ttu-id="30633-151">VydánoTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="30633-152">Federovaní</span><span class="sxs-lookup"><span data-stu-id="30633-152">Federated</span></span>|<span data-ttu-id="30633-153">X509</span><span class="sxs-lookup"><span data-stu-id="30633-153">X509</span></span>|<span data-ttu-id="30633-154">Přenos</span><span class="sxs-lookup"><span data-stu-id="30633-154">Transport</span></span>|  
|<span data-ttu-id="30633-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="30633-156">Windows Sspi vyjednané</span><span class="sxs-lookup"><span data-stu-id="30633-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30633-157">Windows Sspi vyjednané</span><span class="sxs-lookup"><span data-stu-id="30633-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30633-158">Přenos</span><span class="sxs-lookup"><span data-stu-id="30633-158">Transport</span></span>|  
|<span data-ttu-id="30633-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="30633-159">AnonymousForCertificate</span></span>|<span data-ttu-id="30633-160">Žádný</span><span class="sxs-lookup"><span data-stu-id="30633-160">None</span></span>|<span data-ttu-id="30633-161">X509</span><span class="sxs-lookup"><span data-stu-id="30633-161">X509</span></span>|<span data-ttu-id="30633-162">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-162">Message</span></span>|  
|<span data-ttu-id="30633-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="30633-163">UserNameForCertificate</span></span>|<span data-ttu-id="30633-164">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="30633-164">User name/password</span></span>|<span data-ttu-id="30633-165">X509</span><span class="sxs-lookup"><span data-stu-id="30633-165">X509</span></span>|<span data-ttu-id="30633-166">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-166">Message</span></span>|  
|<span data-ttu-id="30633-167">Vzájemná certifikát</span><span class="sxs-lookup"><span data-stu-id="30633-167">MutualCertificate</span></span>|<span data-ttu-id="30633-168">X509</span><span class="sxs-lookup"><span data-stu-id="30633-168">X509</span></span>|<span data-ttu-id="30633-169">X509</span><span class="sxs-lookup"><span data-stu-id="30633-169">X509</span></span>|<span data-ttu-id="30633-170">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-170">Message</span></span>|  
|<span data-ttu-id="30633-171">Vzájemná certifikátDuplex</span><span class="sxs-lookup"><span data-stu-id="30633-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="30633-172">X509</span><span class="sxs-lookup"><span data-stu-id="30633-172">X509</span></span>|<span data-ttu-id="30633-173">X509</span><span class="sxs-lookup"><span data-stu-id="30633-173">X509</span></span>|<span data-ttu-id="30633-174">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-174">Message</span></span>|  
|<span data-ttu-id="30633-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="30633-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="30633-176">Federovaní</span><span class="sxs-lookup"><span data-stu-id="30633-176">Federated</span></span>|<span data-ttu-id="30633-177">X509</span><span class="sxs-lookup"><span data-stu-id="30633-177">X509</span></span>|<span data-ttu-id="30633-178">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-178">Message</span></span>|  
|<span data-ttu-id="30633-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="30633-179">Kerberos</span></span>|<span data-ttu-id="30633-180">Windows</span><span class="sxs-lookup"><span data-stu-id="30633-180">Windows</span></span>|<span data-ttu-id="30633-181">Windows</span><span class="sxs-lookup"><span data-stu-id="30633-181">Windows</span></span>|<span data-ttu-id="30633-182">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-182">Message</span></span>|  
|<span data-ttu-id="30633-183">Vydaný token</span><span class="sxs-lookup"><span data-stu-id="30633-183">IssuedToken</span></span>|<span data-ttu-id="30633-184">Federovaní</span><span class="sxs-lookup"><span data-stu-id="30633-184">Federated</span></span>|<span data-ttu-id="30633-185">Federovaní</span><span class="sxs-lookup"><span data-stu-id="30633-185">Federated</span></span>|<span data-ttu-id="30633-186">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-186">Message</span></span>|  
|<span data-ttu-id="30633-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-187">SspiNegotiated</span></span>|<span data-ttu-id="30633-188">Windows Sspi vyjednané</span><span class="sxs-lookup"><span data-stu-id="30633-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30633-189">Windows Sspi vyjednané</span><span class="sxs-lookup"><span data-stu-id="30633-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30633-190">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-190">Message</span></span>|  
|<span data-ttu-id="30633-191">AnonymníForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="30633-192">Žádný</span><span class="sxs-lookup"><span data-stu-id="30633-192">None</span></span>|<span data-ttu-id="30633-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="30633-193">X509, TLS-Nego</span></span>|<span data-ttu-id="30633-194">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-194">Message</span></span>|  
|<span data-ttu-id="30633-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="30633-196">Uživatelské jméno/heslo</span><span class="sxs-lookup"><span data-stu-id="30633-196">User name/password</span></span>|<span data-ttu-id="30633-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="30633-197">X509, TLS-Nego</span></span>|<span data-ttu-id="30633-198">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-198">Message</span></span>|  
|<span data-ttu-id="30633-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-199">MutualSslNegotiated</span></span>|<span data-ttu-id="30633-200">X509</span><span class="sxs-lookup"><span data-stu-id="30633-200">X509</span></span>|<span data-ttu-id="30633-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="30633-201">X509, TLS-Nego</span></span>|<span data-ttu-id="30633-202">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-202">Message</span></span>|  
|<span data-ttu-id="30633-203">VydánoTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="30633-204">Federovaní</span><span class="sxs-lookup"><span data-stu-id="30633-204">Federated</span></span>|<span data-ttu-id="30633-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="30633-205">X509, TLS-Nego</span></span>|<span data-ttu-id="30633-206">Zpráva</span><span class="sxs-lookup"><span data-stu-id="30633-206">Message</span></span>|  
  
 <span data-ttu-id="30633-207">Koncové body používající tyto režimy ověřování mohou vyjádřit své požadavky na zabezpečení pomocí ws-securitypolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="30633-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="30633-208">Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a poskytuje příklady zásad a zpráv.</span><span class="sxs-lookup"><span data-stu-id="30633-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="30633-209">WCF využívá WS-SecureConversation poskytovat podporu zabezpečené relace k ochraně více zpráv výměny mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="30633-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="30633-210">Podrobnosti o implementaci najdete níže v části Zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="30633-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="30633-211">Kromě režimů ověřování poskytuje WCF nastavení pro řízení běžných ochranných mechanismů, které se vztahují na většinu režimů ověřování založených na zabezpečení zpráv, například: pořadí podpisu versus operace šifrování, algoritmické sady, odvození klíče a potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="30633-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="30633-212">V tomto dokumentu se používají následující předpony a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="30633-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="30633-213">Předpona</span><span class="sxs-lookup"><span data-stu-id="30633-213">Prefix</span></span>|<span data-ttu-id="30633-214">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="30633-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="30633-215">s</span><span class="sxs-lookup"><span data-stu-id="30633-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="30633-216">sp</span><span class="sxs-lookup"><span data-stu-id="30633-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="30633-217">a</span><span class="sxs-lookup"><span data-stu-id="30633-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="30633-218">wsse</span><span class="sxs-lookup"><span data-stu-id="30633-218">wsse</span></span>|<span data-ttu-id="30633-219">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="30633-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="30633-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="30633-220">wsse11</span></span>|<span data-ttu-id="30633-221">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="30633-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="30633-222">wsu</span><span class="sxs-lookup"><span data-stu-id="30633-222">wsu</span></span>|<span data-ttu-id="30633-223">TBD – Identifikátor URI služby OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="30633-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="30633-224">Ds</span><span class="sxs-lookup"><span data-stu-id="30633-224">ds</span></span>|<span data-ttu-id="30633-225">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="30633-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="30633-226">Wst</span><span class="sxs-lookup"><span data-stu-id="30633-226">wst</span></span>|<span data-ttu-id="30633-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="30633-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="30633-228">wssc</span><span class="sxs-lookup"><span data-stu-id="30633-228">wssc</span></span>|<span data-ttu-id="30633-229">TBD – identifikátor URI s bezpečným ws 2005/02</span><span class="sxs-lookup"><span data-stu-id="30633-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="30633-230">vytáčí</span><span class="sxs-lookup"><span data-stu-id="30633-230">wsaw</span></span>|<span data-ttu-id="30633-231">TBD – obor názvů zásad WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="30633-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="30633-232">Wsp</span><span class="sxs-lookup"><span data-stu-id="30633-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="30633-233">mssp</span><span class="sxs-lookup"><span data-stu-id="30633-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="30633-234">1. Profily tokenů</span><span class="sxs-lookup"><span data-stu-id="30633-234">1. Token Profiles</span></span>  
 <span data-ttu-id="30633-235">Specifikace zabezpečení webových služeb představují pověření jako tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30633-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="30633-236">WCF podporuje následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="30633-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="30633-237">1.1 Uživatelské jménoToken</span><span class="sxs-lookup"><span data-stu-id="30633-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="30633-238">WCF následuje UsernameToken10 a UsernameToken11 profily s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="30633-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="30633-239">R1101 PasswordType atribut na UsernameToken\Password element musí být vynechán nebo mít hodnotu #PasswordText (výchozí).</span><span class="sxs-lookup"><span data-stu-id="30633-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="30633-240">Lze implementovat #PasswordDigest pomocí rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="30633-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="30633-241">Bylo zjištěno, že #PasswordDigest byl často mylně považován za dostatečně bezpečný mechanismus ochrany heslem.</span><span class="sxs-lookup"><span data-stu-id="30633-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="30633-242">Ale #PasswordDigest nemůže sloužit jako náhrada za šifrování UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="30633-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="30633-243">Primárním cílem #PasswordDigest je ochrana proti útokům záznamu.</span><span class="sxs-lookup"><span data-stu-id="30633-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="30633-244">V režimech ověřování WCF jsou hrozby útoku přehrání zmírněny pomocí podpisů zpráv.</span><span class="sxs-lookup"><span data-stu-id="30633-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="30633-245">B1102 WCF nikdy vyzařuje Nonce a Vytvořil dílčí prvky UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="30633-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="30633-246">Tyto dílčí prvky jsou určeny k pomoci replay detekce.</span><span class="sxs-lookup"><span data-stu-id="30633-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="30633-247">WCF místo toho používá podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="30633-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="30633-248">OASIS WSS SOAP Message Security UsernameToken Profil 1.1 (UsernameToken11) zavedl odvození klíče z funkce hesla.</span><span class="sxs-lookup"><span data-stu-id="30633-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="30633-249">B1103 UsernameToken heslo nesmí být použit pro odvození klíče a proto pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="30633-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="30633-250">Odůvodnění: hesla jsou obecně považovány za příliš slabé pro použití pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="30633-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="30633-251">1,2 x509 token</span><span class="sxs-lookup"><span data-stu-id="30633-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="30633-252">WCF podporuje certifikáty X509v3 jako typ pověření a následuje X509TokenProfile1.0 a X509TokenProfile1.1 s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="30633-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="30633-253">R1201 Atribut ValueType na elementu BinarySecurityToken musí mít hodnotu #X509v3, pokud obsahuje certifikát X509v3.</span><span class="sxs-lookup"><span data-stu-id="30633-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="30633-254">WSS X509 Profil tokenu 1.0 a 1.1 definovat také #X509PKIPathv1 a #PKCS7 jako typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="30633-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="30633-255">WCF nepodporuje tyto typy.</span><span class="sxs-lookup"><span data-stu-id="30633-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="30633-256">R1202 Pokud je v certifikátu X509 k dispozici rozšíření SubjectKeyIdentifier (SKI), wsse:KeyIdentifier by měl být použit pro externí odkazy na token s atributem ValueType jako #X509SubjectKeyIdentifier a jeho obsahem base64 kódovaná hodnota rozšíření SKI certifikátu 64.</span><span class="sxs-lookup"><span data-stu-id="30633-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="30633-257">Odkazy na SKI jsou široce implementovány a osvědčovány jako vysoce interoperabilní externí referenční typ.</span><span class="sxs-lookup"><span data-stu-id="30633-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="30633-258">R1203 Externí odkaz na token zabezpečení X509 by neměl používat ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30633-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="30633-259">R1204 Pokud x509TokenProfile1.1 je používán, externí odkaz na Token zabezpečení X509 by měl použít kryptografický otisk zavedené WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="30633-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="30633-260">WCF podporuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30633-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="30633-261">Existují však problémy s interoperabilitou s X509IssuerSerial: WCF používá řetězec k porovnání dvou hodnot X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30633-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="30633-262">Proto pokud jeden změnit pořadí komponenty předmětu name a odešle službě WCF odkaz na certifikát, nemusí být nalezen.</span><span class="sxs-lookup"><span data-stu-id="30633-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="30633-263">1.3 Token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="30633-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="30633-264">WCF podporuje protokol KerberosTokenProfile1.1 pro účely ověřování systému Windows s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="30633-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="30633-265">R1301 A Kerberos Token musí nést hodnotu GSS zabalené Kerberos v4 AP_REQ jak je definováno v GSS_API a specifikace Kerberos a musí mít ValueType atribut s hodnotou #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="30633-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="30633-266">WCF používá GSS zabalené Kerberos AP-REQ, nikoli holé AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="30633-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="30633-267">Toto je bezpečnostní osvědčený postup.</span><span class="sxs-lookup"><span data-stu-id="30633-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="30633-268">1.4 SAML v1.1 Žeton</span><span class="sxs-lookup"><span data-stu-id="30633-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="30633-269">WCF podporuje wss saml token profily 1.0 a 1.1 pro tokeny SAML v1.1.</span><span class="sxs-lookup"><span data-stu-id="30633-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="30633-270">Je možné implementovat další verze formátů tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="30633-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="30633-271">1.5 Token kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="30633-272">WCF podporuje token kontextu zabezpečení (SCT) zavedený v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="30633-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="30633-273">SCT se používá k reprezentaci kontextu zabezpečení vytvořeného v SecureConversation, stejně jako binární vyjednávací protokoly TLS a SSPI, popsané níže.</span><span class="sxs-lookup"><span data-stu-id="30633-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="30633-274">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="30633-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="30633-275">2.1 Časové razítko</span><span class="sxs-lookup"><span data-stu-id="30633-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="30633-276">Přítomnost časového razítka <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> je řízena pomocí vlastnosti třídy. <xref:System.ServiceModel.Channels.SecurityBindingElement></span><span class="sxs-lookup"><span data-stu-id="30633-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="30633-277">WCF vždy serializuje wsse:TimeStamp s wsse:Created a wsse:Expires fields.</span><span class="sxs-lookup"><span data-stu-id="30633-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="30633-278">Wsse:TimeStamp je vždy podepsánpři podepisování se používá.</span><span class="sxs-lookup"><span data-stu-id="30633-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="30633-279">2.2 Ochranný příkaz</span><span class="sxs-lookup"><span data-stu-id="30633-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="30633-280">WCF podporuje pořadí ochrany zpráv "Podepsat před šifrovat" a "Šifrovat před podpisem" (zásady zabezpečení 1.1).</span><span class="sxs-lookup"><span data-stu-id="30633-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="30633-281">"Podepsat před šifrováním" se doporučuje z důvodů, včetně: zprávy chráněné šifrovat před podpisem jsou otevřeny útokům nahrazení podpisu, pokud není použit mechanismus WS-Security 1.1 SignatureConfirmation a podpis přes šifrovaný obsah auditování je obtížnější.</span><span class="sxs-lookup"><span data-stu-id="30633-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="30633-282">2.3 Ochrana proti podpisu</span><span class="sxs-lookup"><span data-stu-id="30633-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="30633-283">Při šifrování před značkou se doporučuje chránit podpis, aby se zabránilo útoky hrubou silou pro hádání šifrovaného obsahu nebo podpisového klíče (zejména při použití vlastního tokenu se slabým klíčem).</span><span class="sxs-lookup"><span data-stu-id="30633-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="30633-284">2.4 Algoritmus Suite</span><span class="sxs-lookup"><span data-stu-id="30633-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="30633-285">WCF podporuje všechny algoritmy sady uvedené v zásadách zabezpečení 1.1.</span><span class="sxs-lookup"><span data-stu-id="30633-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="30633-286">2.5 Odvození klíče</span><span class="sxs-lookup"><span data-stu-id="30633-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="30633-287">WCF používá "Odvození klíče pro symetrické klíče", jak je popsáno v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="30633-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="30633-288">2.6 Potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="30633-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="30633-289">Potvrzení podpisu může být jako ochrana před útoky prostředníka k ochraně sady podpisů.</span><span class="sxs-lookup"><span data-stu-id="30633-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="30633-290">2.7 Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="30633-291">Každý režim ověřování popisuje určité rozložení hlavičky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30633-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="30633-292">Prvky v záhlaví zabezpečení jsou poloseřovní.</span><span class="sxs-lookup"><span data-stu-id="30633-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="30633-293">Chcete-li definovat pořadí podřízených prvků záhlaví zabezpečení, zásady ws-security definuje následující režimy rozložení záhlaví zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="30633-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30633-294">Striktní</span><span class="sxs-lookup"><span data-stu-id="30633-294">Strict</span></span>|<span data-ttu-id="30633-295">Položky jsou přidány do hlavičky zabezpečení podle číslovaných pravidel rozložení popsaných v části 7.7.1 zásad zabezpečení podle obecného principu "deklarovat před použitím".</span><span class="sxs-lookup"><span data-stu-id="30633-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="30633-296">Lax</span><span class="sxs-lookup"><span data-stu-id="30633-296">Lax</span></span>|<span data-ttu-id="30633-297">Položky jsou přidány do hlavičky zabezpečení v libovolném pořadí, které odpovídá WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="30633-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="30633-298">LaxTimestampPrvní</span><span class="sxs-lookup"><span data-stu-id="30633-298">LaxTimestampFirst</span></span>|<span data-ttu-id="30633-299">Stejné jako Lax s tím rozdílem, že první položka v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="30633-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="30633-300">LaxTimestampPoslední</span><span class="sxs-lookup"><span data-stu-id="30633-300">LaxTimestampLast</span></span>|<span data-ttu-id="30633-301">Stejné jako laxní s tím rozdílem, že poslední položka v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="30633-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="30633-302">WCF podporuje všechny čtyři režimy pro rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30633-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="30633-303">Struktura záhlaví zabezpečení a příklady zpráv pro režimy ověřování níže postupujte podle režimu "Strict".</span><span class="sxs-lookup"><span data-stu-id="30633-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="30633-304">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="30633-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="30633-305">Tato část obsahuje příkladzásady pro každý režim ověřování spolu s příklady zobrazující strukturu záhlaví zabezpečení ve zprávách vyměňovaných klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="30633-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="30633-306">6.1 Ochrana proti přepravě</span><span class="sxs-lookup"><span data-stu-id="30633-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="30633-307">WCF poskytuje pět režimů ověřování, které používají zabezpečený přenos k ochraně zpráv; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="30633-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="30633-308">Tyto režimy ověřování jsou konstruovány pomocí přenosové vazby popsané v SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="30633-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="30633-309">Pro režim ověřování UserNameOverTransport usernametoken je podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="30633-310">Pro ostatní režimy ověřování token se zobrazí jako podepsaný endorsing token.</span><span class="sxs-lookup"><span data-stu-id="30633-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="30633-311">Dodatek C.1.2 a C.1.3 securitypolicy podrobně popisují rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30633-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="30633-312">Následující příklad záhlaví zabezpečení zobrazit přísné rozložení pro daný režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="30633-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="30633-313">Hodnota vlastnosti "Odvozené klíče" pro tokeny ve všech případech je "false".</span><span class="sxs-lookup"><span data-stu-id="30633-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="30633-314">Hodnoty různých vlastností transportní vazby jsou následující:</span><span class="sxs-lookup"><span data-stu-id="30633-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="30633-315">Časové razítko: true</span><span class="sxs-lookup"><span data-stu-id="30633-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="30633-316">Rozložení záhlaví zabezpečení: Přísné</span><span class="sxs-lookup"><span data-stu-id="30633-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="30633-317">Sada algoritmů: Basic256</span><span class="sxs-lookup"><span data-stu-id="30633-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="30633-318">6.1.1 Uživatelské jménoOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="30633-319">V tomto režimu ověřování se klient ověřuje tokenem uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token, který je vždy odeslán z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="30633-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30633-320">Služba je ověřena pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="30633-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30633-321">Použitá vazba je transportní vazba.</span><span class="sxs-lookup"><span data-stu-id="30633-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="30633-322">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="30633-323">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="30633-324">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-324">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-325">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="30633-326">6.1.2 CertifikátyoverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="30633-327">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X.509, který se zobrazí ve vrstvě SOAP jako podpůrný token, který je vždy odeslán z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="30633-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30633-328">Služba je ověřena pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="30633-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30633-329">Použitá vazba je transportní vazba.</span><span class="sxs-lookup"><span data-stu-id="30633-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="30633-330">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="30633-331">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="30633-332">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-332">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-333">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="30633-334">6.1.3 VydánoTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="30633-335">V tomto režimu ověřování klient neověřuje službu jako takovou, ale představuje token vydaný službou TOKEN zabezpečení (STS) a prokáže znalost sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="30633-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="30633-336">Vydaný token se zobrazí ve vrstvě SOAP jako podpůrný token, který je vždy odeslán z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="30633-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30633-337">Služba je ověřena pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="30633-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30633-338">Vazba je transportní vazba.</span><span class="sxs-lookup"><span data-stu-id="30633-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="30633-339">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="30633-340">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="30633-341">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-341">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-342">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="30633-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="30633-344">V tomto režimu ověřování se klient ověřuje službě pomocí lístku protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="30633-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="30633-345">Token Protokolu Kerberos se zobrazí ve vrstvě SOAP jako podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30633-346">Služba je ověřena pomocí certifikátu X.509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="30633-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30633-347">Vazba je transportní vazba.</span><span class="sxs-lookup"><span data-stu-id="30633-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="30633-348">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="30633-349">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="30633-350">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-350">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-351">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="30633-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="30633-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="30633-353">V tomto režimu se k ověřování klienta a serveru používá protokol vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="30633-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="30633-354">Kerberos se používá, pokud je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="30633-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="30633-355">Výsledný SCT se zobrazí ve vrstvě SOAP jako podpůrný token, který je vždy odeslán z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="30633-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="30633-356">Služba je navíc ověřena na transportní vrstvě certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="30633-357">Použitá vazba je transportní vazba.</span><span class="sxs-lookup"><span data-stu-id="30633-357">The binding used is a transport binding.</span></span> <span data-ttu-id="30633-358">"SPNEGO" (vyjednávání) popisuje, jak WCF používá SSPI binární vyjednávací protokol s WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="30633-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="30633-359">Příklady záhlaví zabezpečení v této části jsou po SCT byla vytvořena prostřednictvím spnego handshake.</span><span class="sxs-lookup"><span data-stu-id="30633-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="30633-360">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="30633-361">Příklady záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30633-361">Security Header Examples</span></span>  
 <span data-ttu-id="30633-362">Jakmile je vytvořen token kontextu zabezpečení pomocí spnego handshake pomocí WS-Trust binární vyjednávání, zprávy aplikace mají záhlaví zabezpečení s následující strukturou.</span><span class="sxs-lookup"><span data-stu-id="30633-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="30633-363">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-363">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-364">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="30633-365">6.2 Použití certifikátů X.509 pro ověřování služeb</span><span class="sxs-lookup"><span data-stu-id="30633-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="30633-366">Tato část popisuje následující režimy ověřování: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="30633-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="30633-367">6.2.1 Vzájemné osvědčení WSS1.0</span><span class="sxs-lookup"><span data-stu-id="30633-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="30633-368">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X.509, který se zobrazí ve vrstvě SOAP jako token iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="30633-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="30633-369">Služba je také ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="30633-370">Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="30633-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="30633-371">Iniciátor token: klienta X.509 certifikát, s režimem zahrnutí nastavena na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30633-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="30633-372">Token příjemce: Certifikát X.509 serveru s režimem zahrnutí je nastaven .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30633-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="30633-373">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-374">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-375">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-376">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-377">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-378">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-379">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-379">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-380">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-380">Response</span></span>  
  
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
  
 <span data-ttu-id="30633-381">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="30633-382">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-382">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-383">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="30633-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="30633-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="30633-385">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X.509, který se zobrazí ve vrstvě SOAP jako token iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="30633-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="30633-386">Služba je také ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="30633-387">Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="30633-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="30633-388">Iniciátor token: Klienta X509 certifikát, režim zahrnutí je nastavena na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30633-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="30633-389">Token příjemce: Certifikát X509 serveru, režim zahrnutí je nastaven na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="30633-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="30633-390">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-391">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-392">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-393">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-394">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-395">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-396">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-397">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-398">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="30633-399">6.2.3 Použití symetrické vazby s ověřováním služby X.509</span><span class="sxs-lookup"><span data-stu-id="30633-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="30633-400">"WSS10" poskytuje omezenou podporu pro scénáře s tokeny X509.</span><span class="sxs-lookup"><span data-stu-id="30633-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="30633-401">Například neexistoval žádný způsob, jak poskytnout ochranu proti podpisu a šifrování pro zprávy, které používají pouze token X509 služby.</span><span class="sxs-lookup"><span data-stu-id="30633-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="30633-402">"WSS11" představil použití EncryptedKey jako symetrický token.</span><span class="sxs-lookup"><span data-stu-id="30633-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="30633-403">Nyní dočasný klíč zašifrovaný pro certifikát X.509 služby by mohl být použit pro ochranu požadavků i odpovědí.</span><span class="sxs-lookup"><span data-stu-id="30633-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="30633-404">Režimy ověřování popsané v části 6.4 níže používají tento vzor.</span><span class="sxs-lookup"><span data-stu-id="30633-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="30633-405">WS-SecurityPolicy popisuje tento vzor pomocí SymmetricBinding s tokenem služby X509 jako token ochrany.</span><span class="sxs-lookup"><span data-stu-id="30633-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="30633-406">Ověřovací režimy AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate používají podobnou instanci sp:SymmetricBinding s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="30633-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="30633-407">Token ochrany: Certifikát X509 serveru, režim zahrnutí je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30633-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="30633-408">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-409">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-410">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-411">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-412">Výše uvedené režimy ověřování se liší pouze podpůrné tokeny, které používají.</span><span class="sxs-lookup"><span data-stu-id="30633-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="30633-413">AnonymousForCertificate nemá žádné podpůrné tokeny, MutualCertificate WSS 1.1 má certifikát X509 klienta jako podpůrný tokeny, UserNameForCertificate má token UserName jako podepsaný podpůrný token a IssuedTokenForCertificate má vydaný token jako podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="30633-414">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-414">Policy</span></span>  
  
 <span data-ttu-id="30633-415">Symetrická vazba</span><span class="sxs-lookup"><span data-stu-id="30633-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="30633-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="30633-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="30633-417">V tomto režimu ověřování je klient anonymní a služba je ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30633-418">Použitá vazba je instancí třídy symetrické vazby popsané v 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="30633-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="30633-419">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-419">Policy</span></span>  
  
 <span data-ttu-id="30633-420">Podrobnosti o vazbě najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="30633-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-421">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-422">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-422">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-423">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-424">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-425">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-425">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-426">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="30633-427">6.2.5 Uživatelské jménopro certifikát</span><span class="sxs-lookup"><span data-stu-id="30633-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="30633-428">V tomto režimu ověřování se klient ověřuje službě pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="30633-429">Služba se ověřuje klientovi pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="30633-430">Použitá vazba je symetrická vazba s tokenochrany je klíč generovaný klientem, šifrované s veřejným klíčem služby.</span><span class="sxs-lookup"><span data-stu-id="30633-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30633-431">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-431">Policy</span></span>  
  
 <span data-ttu-id="30633-432">Podrobnosti o vazbě najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="30633-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="30633-433">Podepsaný podpůrný token</span><span class="sxs-lookup"><span data-stu-id="30633-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-434">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-435">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-435">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-436">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-437">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-438">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-438">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-439">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="30633-440">6.2.6 Vzájemné osvědčení (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="30633-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="30633-441">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X.509, který se zobrazí ve vrstvě SOAP jako podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30633-442">Služba je také ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30633-443">Použitá vazba je symetrická vazba s tokenochrany je klíč generovaný klientem, šifrované s veřejným klíčem služby.</span><span class="sxs-lookup"><span data-stu-id="30633-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30633-444">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-444">Policy</span></span>  
  
 <span data-ttu-id="30633-445">Podrobnosti o vazbě najdete v části Zásady v 6.2.3</span><span class="sxs-lookup"><span data-stu-id="30633-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="30633-446">Schvalování podpůrného tokenu</span><span class="sxs-lookup"><span data-stu-id="30633-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-447">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-448">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-448">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-449">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-450">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-451">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-451">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-452">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="30633-453">6.2.7 Vydanýtokenprocertifikát</span><span class="sxs-lookup"><span data-stu-id="30633-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="30633-454">V tomto režimu ověřování klient neověřuje službu jako takovou, ale místo toho představuje token vydaný službou STS a prokáže znalost sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="30633-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30633-455">Vydaný token se zobrazí ve vrstvě SOAP jako podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30633-456">Služba se ověřuje klientovi pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="30633-457">Použitá vazba je symetrická vazba s tokenochrany je klíč generovaný klientem, šifrované s veřejným klíčem služby.</span><span class="sxs-lookup"><span data-stu-id="30633-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30633-458">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-458">Policy</span></span>  
  
 <span data-ttu-id="30633-459">Podrobnosti o vazbě najdete v části Zásady v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="30633-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="30633-460">Schvalování podpůrného tokenu</span><span class="sxs-lookup"><span data-stu-id="30633-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-461">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-462">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-462">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-463">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-464">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-465">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-465">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-466">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="30633-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="30633-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="30633-468">V tomto režimu ověřování se klient ověřuje službě pomocí lístku protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="30633-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="30633-469">Stejný lístek také poskytuje ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="30633-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="30633-470">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="30633-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30633-471">Token ochrany: Lístek kerberos, režim zahrnutí je nastaven na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="30633-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="30633-472">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-473">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-474">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-475">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-476">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-477">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-478">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-478">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-479">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-480">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-481">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="30633-482">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="30633-483">6.4 Vydaný token</span><span class="sxs-lookup"><span data-stu-id="30633-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="30633-484">V tomto režimu ověřování klient neověřuje službu jako takové, spíše klient představuje token vydaný STS a prokáže znalost sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="30633-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30633-485">Služba není ověřena klientovi, jako takový, místo toho STS šifruje sdílený klíč jako součást vydaného tokenu tak, aby pouze služba může dešifrovat klíč.</span><span class="sxs-lookup"><span data-stu-id="30633-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="30633-486">Použitá vazba je jako symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="30633-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30633-487">Token ochrany: Vydaný token, režim zahrnutí je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30633-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="30633-488">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-489">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-490">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-491">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-492">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-493">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-494">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-494">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-495">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-496">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-497">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-497">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-498">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="30633-499">6.5 Použití sslnegotiated pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="30633-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="30633-500">Tato část popisuje skupinu režimů ověřování, které používají symetrickou vazbu s tokenem ochrany je token kontextu zabezpečení na WS-SecureConversation (WS-SC), jehož hodnota klíče je vyjednána spuštěním protokolu TLS přes WS-Trust (WS-T) RST/RSTR zprávy.</span><span class="sxs-lookup"><span data-stu-id="30633-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="30633-501">Podrobnosti implementace tls handshake pomocí WS-Trust jsou popsány v TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="30633-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="30633-502">Zde v příkladech zprávy budeme předpokládat, že SCT s přidruženým kontextem zabezpečení je již vytvořen prostřednictvím handshake.</span><span class="sxs-lookup"><span data-stu-id="30633-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="30633-503">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="30633-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30633-504">Token ochrany: SslContextToken, režim zahrnutí je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30633-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="30633-505">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-506">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-507">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-508">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="30633-509">6.5.1 Zásady pro ověřování služby SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="30633-510">Zásady pro všechny režimy ověřování v této části jsou podobné a liší se pouze konkrétní podepsané podpůrné nebo schvalování tokeny používané.</span><span class="sxs-lookup"><span data-stu-id="30633-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="30633-511">6.5.2 AnonymníForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="30633-512">V tomto režimu ověřování je klient anonymní a služba je ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30633-513">Použitá vazba je instancí třídy symetrické vazby popsané v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="30633-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30633-514">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-514">Policy</span></span>  
  
 <span data-ttu-id="30633-515">Podrobnosti o vazbě najdete v části Zásady v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="30633-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-516">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-517">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-517">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-518">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-519">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-520">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-520">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-521">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="30633-522">6.5.3 UserNameForSslNegotiated 6.5.3 UserNameForSslNegotiated 6.5.3 UserNameForSslNegotiated 6.</span><span class="sxs-lookup"><span data-stu-id="30633-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="30633-523">V tomto režimu ověřování klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="30633-524">Služba je ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30633-525">Použitá vazba je instancí třídy symetrické vazby popsané v 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="30633-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="30633-526">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-526">Policy</span></span>  
  
 <span data-ttu-id="30633-527">Podrobnosti o vazbě jsou uvedeny v bodě 6.5.1 výše</span><span class="sxs-lookup"><span data-stu-id="30633-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30633-528">Podepsaný podpůrný token</span><span class="sxs-lookup"><span data-stu-id="30633-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-529">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-530">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-530">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-531">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-532">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-533">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-533">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-534">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="30633-535">6.5.4 VydánoTokenForSslSlSlSlNegotiated 6.5.4 IssuedTokenForSslNegotiated 6.5.4 IssuedTokenForSs</span><span class="sxs-lookup"><span data-stu-id="30633-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="30633-536">V tomto režimu ověřování klient neověřuje službu jako takovou, ale místo toho představuje token vydaný službou STS a prokáže znalost sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="30633-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30633-537">Vydaný token se zobrazí ve vrstvě SOAP jako podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="30633-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30633-538">Služba je ověřena pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30633-539">Použitá vazba je instancí třídy symetrické vazby popsané v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="30633-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30633-540">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-540">Policy</span></span>  
  
 <span data-ttu-id="30633-541">Podrobnosti o vazbě jsou uvedeny v bodě 6.5.1 výše</span><span class="sxs-lookup"><span data-stu-id="30633-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30633-542">Schvalování podpůrného tokenu</span><span class="sxs-lookup"><span data-stu-id="30633-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-543">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-544">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-544">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-545">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-546">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-547">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-547">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-548">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="30633-549">6.5.5 MutualSslNegotiated 6.5.5</span><span class="sxs-lookup"><span data-stu-id="30633-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="30633-550">V tomto režimu ověřování se klient a služba ověřují pomocí certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="30633-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="30633-551">Použitá vazba je instancí třídy symetrické vazby popsané v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="30633-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30633-552">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-552">Policy</span></span>  
  
 <span data-ttu-id="30633-553">Podrobnosti o vazbě jsou uvedeny v bodě 6.5.1 výše</span><span class="sxs-lookup"><span data-stu-id="30633-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30633-554">Schvalování podpůrného tokenu</span><span class="sxs-lookup"><span data-stu-id="30633-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-555">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-556">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-556">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-557">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-558">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-559">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-559">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-560">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="30633-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="30633-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="30633-562">V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="30633-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="30633-563">Kerberos se používá, pokud je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="30633-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="30633-564">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="30633-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30633-565">Token ochrany: SpnegoContextToken, režim zahrnutí je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30633-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="30633-566">Ochrana tokenu: False</span><span class="sxs-lookup"><span data-stu-id="30633-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="30633-567">Celé podpisy záhlaví a textu: True</span><span class="sxs-lookup"><span data-stu-id="30633-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30633-568">Příkaz ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30633-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30633-569">Šifrovat podpis: True</span><span class="sxs-lookup"><span data-stu-id="30633-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30633-570">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-571">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-572">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-572">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-573">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-574">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-575">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-575">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-576">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="30633-577">6.7 Zabezpečená konverzace</span><span class="sxs-lookup"><span data-stu-id="30633-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="30633-578">Použitá vazba je symetrická vazba s tokenem ochrany je SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="30633-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="30633-579">SCT je vyjednána pomocí WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC) podle vnořené vazby, což je samo o sobě symetrická vazba, která používá protokol vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="30633-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="30633-580">Protokol vyjednávání použije protokol Kerberos k provedení ověřování klienta a serveru, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="30633-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="30633-581">Pokud protokol Kerberos nelze použít, vrátí se zpět na ntlm.</span><span class="sxs-lookup"><span data-stu-id="30633-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="30633-582">Zásada</span><span class="sxs-lookup"><span data-stu-id="30633-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30633-583">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30633-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30633-584">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-584">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-585">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30633-586">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30633-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30633-587">Žádost</span><span class="sxs-lookup"><span data-stu-id="30633-587">Request</span></span>  
  
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
  
 <span data-ttu-id="30633-588">Odpověď</span><span class="sxs-lookup"><span data-stu-id="30633-588">Response</span></span>  
  
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
