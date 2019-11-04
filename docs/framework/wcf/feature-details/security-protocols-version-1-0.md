---
title: Protokoly zabezpečení verze 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: e22150d21638cffdf804008c32285f900bb1e263
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459040"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="9cf2f-102">Protokoly zabezpečení verze 1.0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="9cf2f-103">Protokoly specifikace Web Services Security poskytují mechanismy zabezpečení webových služeb, které pokrývají všechny stávající požadavky na zabezpečení podnikových zpráv.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="9cf2f-104">Tato část popisuje podrobnosti o Windows Communication Foundation (WCF) verze 1,0 (implementované v <xref:System.ServiceModel.Channels.SecurityBindingElement>) pro následující protokoly zabezpečení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="9cf2f-105">Specifikace/dokument</span><span class="sxs-lookup"><span data-stu-id="9cf2f-105">Specification/Document</span></span>|<span data-ttu-id="9cf2f-106">Propojit</span><span class="sxs-lookup"><span data-stu-id="9cf2f-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="9cf2f-107">WSS: zabezpečení zpráv SOAP 1,0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="9cf2f-108">WSS: Profil tokenu uživatelského jména 1,0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="9cf2f-109">WSS: Profil tokenu x509 1,0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="9cf2f-110">WSS: Profil tokenu SAML 1,1 1,0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="9cf2f-111">WSS: zabezpečení zpráv SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="9cf2f-112">Token uživatelského jména WSS – profil 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="9cf2f-113">WSS: X. 509 – profil tokenu 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="9cf2f-114">WSS: Profil tokenu protokolu Kerberos 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="9cf2f-115">WSS: Profil tokenu SAML 1,1 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="9cf2f-116">Konverzace WS-Secure</span><span class="sxs-lookup"><span data-stu-id="9cf2f-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="9cf2f-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="9cf2f-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="9cf2f-118">Poznámka k aplikaci:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-118">Application Note:</span></span><br /><br /> <span data-ttu-id="9cf2f-119">Použití WS-Trust pro handshake TLS</span><span class="sxs-lookup"><span data-stu-id="9cf2f-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="9cf2f-120">K publikování</span><span class="sxs-lookup"><span data-stu-id="9cf2f-120">To be published</span></span>|  
|<span data-ttu-id="9cf2f-121">Poznámka k aplikaci:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-121">Application Note:</span></span><br /><br /> <span data-ttu-id="9cf2f-122">Používání WS-Trust pro SPNEGO</span><span class="sxs-lookup"><span data-stu-id="9cf2f-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="9cf2f-123">K publikování</span><span class="sxs-lookup"><span data-stu-id="9cf2f-123">To be published</span></span>|  
|<span data-ttu-id="9cf2f-124">Poznámka k aplikaci:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-124">Application Note:</span></span><br /><br /> <span data-ttu-id="9cf2f-125">Odkazy a identita koncových bodů adresování webových služeb</span><span class="sxs-lookup"><span data-stu-id="9cf2f-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="9cf2f-126">K publikování</span><span class="sxs-lookup"><span data-stu-id="9cf2f-126">To be published</span></span>|  
|<span data-ttu-id="9cf2f-127">WS-SecurityPolicy 1,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="9cf2f-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="9cf2f-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="9cf2f-129">Jak bylo upraveno službou [Seznam chyb](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) odeslané technickému výboru Oasis ws-sx</span><span class="sxs-lookup"><span data-stu-id="9cf2f-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="9cf2f-130">Služba WCF verze 1 poskytuje 17 režimů ověřování, které lze použít jako základ pro konfiguraci zabezpečení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="9cf2f-131">Jednotlivé režimy jsou optimalizované pro společnou sadu požadavků na nasazení, jako například:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="9cf2f-132">Pověření používaná k ověřování klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="9cf2f-133">Mechanismy ochrany zabezpečení zpráv nebo přenosů.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="9cf2f-134">Vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="9cf2f-135">Režim ověřování</span><span class="sxs-lookup"><span data-stu-id="9cf2f-135">Authentication Mode</span></span>|<span data-ttu-id="9cf2f-136">Ověřování klienta</span><span class="sxs-lookup"><span data-stu-id="9cf2f-136">Client Authentication</span></span>|<span data-ttu-id="9cf2f-137">Ověřování serveru</span><span class="sxs-lookup"><span data-stu-id="9cf2f-137">Server Authentication</span></span>|<span data-ttu-id="9cf2f-138">Režim</span><span class="sxs-lookup"><span data-stu-id="9cf2f-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="9cf2f-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-139">UserNameOverTransport</span></span>|<span data-ttu-id="9cf2f-140">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="9cf2f-140">User name/password</span></span>|<span data-ttu-id="9cf2f-141">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-141">X509</span></span>|<span data-ttu-id="9cf2f-142">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-142">Transport</span></span>|  
|<span data-ttu-id="9cf2f-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-143">CertificateOverTransport</span></span>|<span data-ttu-id="9cf2f-144">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-144">X509</span></span>|<span data-ttu-id="9cf2f-145">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-145">X509</span></span>|<span data-ttu-id="9cf2f-146">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-146">Transport</span></span>|  
|<span data-ttu-id="9cf2f-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-147">KerberosOverTransport</span></span>|<span data-ttu-id="9cf2f-148">Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-148">Windows</span></span>|<span data-ttu-id="9cf2f-149">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-149">X509</span></span>|<span data-ttu-id="9cf2f-150">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-150">Transport</span></span>|  
|<span data-ttu-id="9cf2f-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="9cf2f-152">Federované</span><span class="sxs-lookup"><span data-stu-id="9cf2f-152">Federated</span></span>|<span data-ttu-id="9cf2f-153">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-153">X509</span></span>|<span data-ttu-id="9cf2f-154">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-154">Transport</span></span>|  
|<span data-ttu-id="9cf2f-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="9cf2f-156">Vyjednávání SSPI systému Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="9cf2f-157">Vyjednávání SSPI systému Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="9cf2f-158">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-158">Transport</span></span>|  
|<span data-ttu-id="9cf2f-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-159">AnonymousForCertificate</span></span>|<span data-ttu-id="9cf2f-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="9cf2f-160">None</span></span>|<span data-ttu-id="9cf2f-161">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-161">X509</span></span>|<span data-ttu-id="9cf2f-162">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-162">Message</span></span>|  
|<span data-ttu-id="9cf2f-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-163">UserNameForCertificate</span></span>|<span data-ttu-id="9cf2f-164">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="9cf2f-164">User name/password</span></span>|<span data-ttu-id="9cf2f-165">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-165">X509</span></span>|<span data-ttu-id="9cf2f-166">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-166">Message</span></span>|  
|<span data-ttu-id="9cf2f-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-167">MutualCertificate</span></span>|<span data-ttu-id="9cf2f-168">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-168">X509</span></span>|<span data-ttu-id="9cf2f-169">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-169">X509</span></span>|<span data-ttu-id="9cf2f-170">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-170">Message</span></span>|  
|<span data-ttu-id="9cf2f-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="9cf2f-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="9cf2f-172">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-172">X509</span></span>|<span data-ttu-id="9cf2f-173">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-173">X509</span></span>|<span data-ttu-id="9cf2f-174">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-174">Message</span></span>|  
|<span data-ttu-id="9cf2f-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="9cf2f-176">Federované</span><span class="sxs-lookup"><span data-stu-id="9cf2f-176">Federated</span></span>|<span data-ttu-id="9cf2f-177">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-177">X509</span></span>|<span data-ttu-id="9cf2f-178">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-178">Message</span></span>|  
|<span data-ttu-id="9cf2f-179">Sdílené</span><span class="sxs-lookup"><span data-stu-id="9cf2f-179">Kerberos</span></span>|<span data-ttu-id="9cf2f-180">Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-180">Windows</span></span>|<span data-ttu-id="9cf2f-181">Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-181">Windows</span></span>|<span data-ttu-id="9cf2f-182">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-182">Message</span></span>|  
|<span data-ttu-id="9cf2f-183">Třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="9cf2f-183">IssuedToken</span></span>|<span data-ttu-id="9cf2f-184">Federované</span><span class="sxs-lookup"><span data-stu-id="9cf2f-184">Federated</span></span>|<span data-ttu-id="9cf2f-185">Federované</span><span class="sxs-lookup"><span data-stu-id="9cf2f-185">Federated</span></span>|<span data-ttu-id="9cf2f-186">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-186">Message</span></span>|  
|<span data-ttu-id="9cf2f-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-187">SspiNegotiated</span></span>|<span data-ttu-id="9cf2f-188">Vyjednávání SSPI systému Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="9cf2f-189">Vyjednávání SSPI systému Windows</span><span class="sxs-lookup"><span data-stu-id="9cf2f-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="9cf2f-190">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-190">Message</span></span>|  
|<span data-ttu-id="9cf2f-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="9cf2f-192">Žádné</span><span class="sxs-lookup"><span data-stu-id="9cf2f-192">None</span></span>|<span data-ttu-id="9cf2f-193">X509, TLS-NEGO</span><span class="sxs-lookup"><span data-stu-id="9cf2f-193">X509, TLS-Nego</span></span>|<span data-ttu-id="9cf2f-194">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-194">Message</span></span>|  
|<span data-ttu-id="9cf2f-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="9cf2f-196">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="9cf2f-196">User name/password</span></span>|<span data-ttu-id="9cf2f-197">X509, TLS-NEGO</span><span class="sxs-lookup"><span data-stu-id="9cf2f-197">X509, TLS-Nego</span></span>|<span data-ttu-id="9cf2f-198">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-198">Message</span></span>|  
|<span data-ttu-id="9cf2f-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-199">MutualSslNegotiated</span></span>|<span data-ttu-id="9cf2f-200">X509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-200">X509</span></span>|<span data-ttu-id="9cf2f-201">X509, TLS-NEGO</span><span class="sxs-lookup"><span data-stu-id="9cf2f-201">X509, TLS-Nego</span></span>|<span data-ttu-id="9cf2f-202">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-202">Message</span></span>|  
|<span data-ttu-id="9cf2f-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="9cf2f-204">Federované</span><span class="sxs-lookup"><span data-stu-id="9cf2f-204">Federated</span></span>|<span data-ttu-id="9cf2f-205">X509, TLS-NEGO</span><span class="sxs-lookup"><span data-stu-id="9cf2f-205">X509, TLS-Nego</span></span>|<span data-ttu-id="9cf2f-206">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cf2f-206">Message</span></span>|  
  
 <span data-ttu-id="9cf2f-207">Koncové body využívající takové režimy ověřování mohou vyjádřit požadavky na zabezpečení pomocí WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="9cf2f-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="9cf2f-208">Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a poskytuje příklady zásad a zpráv.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="9cf2f-209">WCF využívá WS-SecureConversation k poskytování zabezpečených relací, které umožňují chránit výměny více zpráv mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="9cf2f-210">Podrobnosti o implementaci najdete níže v části "zabezpečené relace".</span><span class="sxs-lookup"><span data-stu-id="9cf2f-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="9cf2f-211">Kromě režimů ověřování nabízí WCF nastavení pro řízení běžných mechanismů ochrany, které se vztahují na většinu režimů ověřování založených na zabezpečení zpráv, například: pořadí podpisů a operací šifrování, sady algoritmů, odvození klíče. a potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="9cf2f-212">V tomto dokumentu se používají následující předpony a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="9cf2f-213">směr</span><span class="sxs-lookup"><span data-stu-id="9cf2f-213">Prefix</span></span>|<span data-ttu-id="9cf2f-214">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9cf2f-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="9cf2f-215">s</span><span class="sxs-lookup"><span data-stu-id="9cf2f-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="9cf2f-216">SP</span><span class="sxs-lookup"><span data-stu-id="9cf2f-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="9cf2f-217">Určitého</span><span class="sxs-lookup"><span data-stu-id="9cf2f-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="9cf2f-218">wsse</span><span class="sxs-lookup"><span data-stu-id="9cf2f-218">wsse</span></span>|<span data-ttu-id="9cf2f-219">TBD – OASIS WSS 1,0 URI</span><span class="sxs-lookup"><span data-stu-id="9cf2f-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="9cf2f-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="9cf2f-220">wsse11</span></span>|<span data-ttu-id="9cf2f-221">TBD – OASIS WSS 1,1 URI</span><span class="sxs-lookup"><span data-stu-id="9cf2f-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="9cf2f-222">wsu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-222">wsu</span></span>|<span data-ttu-id="9cf2f-223">TBD – identifikátor URI nástroje OASIS WSS 1,0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="9cf2f-224">služby</span><span class="sxs-lookup"><span data-stu-id="9cf2f-224">ds</span></span>|<span data-ttu-id="9cf2f-225">TBD – XMLDSig URI W3C</span><span class="sxs-lookup"><span data-stu-id="9cf2f-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="9cf2f-226">WST</span><span class="sxs-lookup"><span data-stu-id="9cf2f-226">wst</span></span>|<span data-ttu-id="9cf2f-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="9cf2f-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="9cf2f-228">wssc</span><span class="sxs-lookup"><span data-stu-id="9cf2f-228">wssc</span></span>|<span data-ttu-id="9cf2f-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="9cf2f-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="9cf2f-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="9cf2f-230">wsaw</span></span>|<span data-ttu-id="9cf2f-231">TBD – obor názvů zásad WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="9cf2f-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="9cf2f-232">WSP</span><span class="sxs-lookup"><span data-stu-id="9cf2f-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="9cf2f-233">mssp</span><span class="sxs-lookup"><span data-stu-id="9cf2f-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="9cf2f-234">1. profily tokenů</span><span class="sxs-lookup"><span data-stu-id="9cf2f-234">1. Token Profiles</span></span>  
 <span data-ttu-id="9cf2f-235">Specifikace specifikace Web Services Security reprezentují přihlašovací údaje jako tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="9cf2f-236">WCF podporuje následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="9cf2f-237">1,1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="9cf2f-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="9cf2f-238">WCF sleduje profily UsernameToken10 a UsernameToken11 s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="9cf2f-239">Atribut R1101 PasswordType elementu UsernameToken\Password musí být buď vynechán, nebo musí mít hodnotu #PasswordText (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9cf2f-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="9cf2f-240">Jeden může implementovat #PasswordDigest s využitím rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="9cf2f-241">Zjistilo se, že #PasswordDigest bylo často zaměněno jako zabezpečený dostatečný mechanismus ochrany heslem.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="9cf2f-242">#PasswordDigest ale nemůžou sloužit jako náhrada za šifrování UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="9cf2f-243">Primárním cílem #PasswordDigest je ochrana před útoky přes opakované přehrání.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="9cf2f-244">V režimech ověřování WCF se hrozby útoku na opakování sníží pomocí podpisů zpráv.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="9cf2f-245">B1102 WCF nikdy negeneruje hodnoty nonce a vytvořil dílčí prvky pro UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="9cf2f-246">Tyto dílčí prvky jsou určeny k detekci opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="9cf2f-247">WCF místo toho používá podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="9cf2f-248">OASIS WSS protokolu SOAP Message Security UsernameToken Profile 1,1 (UsernameToken11) zavedla odvození klíče z funkce Password.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="9cf2f-249">Heslo B1103 UsernameToken nesmí být použito pro odvození klíče, a proto pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="9cf2f-250">Odůvodnění: hesla se obecně považují za příliš slabá, aby je bylo možné použít pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="9cf2f-251">Token x509 1,2</span><span class="sxs-lookup"><span data-stu-id="9cf2f-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="9cf2f-252">WCF podporuje certifikáty X509v3 jako typ přihlašovacích údajů a sleduje X509TokenProfile 1.0 a X509TokenProfile 1.1 s následujícími omezeními:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="9cf2f-253">R1201 atribut ValueType elementu BinarySecurityToken musí mít hodnotu #X509v3, pokud obsahuje certifikát X509v3.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="9cf2f-254">Definice tokenu WSS x509 1,0 a 1,1 také #X509PKIPathv1 a #PKCS7 jako typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="9cf2f-255">WCF tyto typy nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="9cf2f-256">R1202 Pokud je v certifikátu x509 k dispozici rozšíření SubjectKeyIdentifier (SKI), wsse: identifikátor klíče by měl být použit pro externí odkazy na token, s atributem ValueType jako #X509SubjectKeyIdentifier a jeho obsahem jako hodnota v kódování Base64 rozšíření LYŽAŘSKÉho certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="9cf2f-257">Odkazy na SKI jsou široce implementovány a ověřeny jako vysoce interoperabilní externí typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="9cf2f-258">R1203 externí odkaz na token zabezpečení x509 by neměl používat DS: X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="9cf2f-259">R1204 Pokud se používá X509TokenProfile 1.1, externí odkaz na token zabezpečení x509 by měl používat kryptografický otisk, který zavádí WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="9cf2f-260">WCF podporuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="9cf2f-261">Existují však problémy interoperability s X509IssuerSerial: WCF používá řetězec k porovnání dvou hodnot X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="9cf2f-262">Proto pokud jedna změna pořadí součástí názvu subjektu a odesílá do služby WCF odkaz na certifikát, nemusí být nalezena.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="9cf2f-263">Token protokolu Kerberos 1,3</span><span class="sxs-lookup"><span data-stu-id="9cf2f-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="9cf2f-264">WCF podporuje KerberosTokenProfile 1.1 pro účely ověřování systému Windows s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="9cf2f-265">R1301 token protokolu Kerberos musí mít hodnotu zabaleného protokolu Kerberos v4 AP_REQ, jak je definováno v GSS_API a specifikace protokolu Kerberos, a musí mít atribut ValueType s hodnotou #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="9cf2f-266">WCF používá zabalené ověřování pomocí služby GSS AP-REQ, nikoli úplného přístupového bodu-REQ.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="9cf2f-267">To je nejlepší postup zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="9cf2f-268">Token SAML v 1.1 1,4</span><span class="sxs-lookup"><span data-stu-id="9cf2f-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="9cf2f-269">WCF podporuje pro tokeny SAML v 1.1 profily tokenů SAML v WSS 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="9cf2f-270">Je možné implementovat jiné verze formátů tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="9cf2f-271">Token kontextu zabezpečení 1,5</span><span class="sxs-lookup"><span data-stu-id="9cf2f-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="9cf2f-272">Služba WCF podporuje token kontextu zabezpečení (SCT) představený v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="9cf2f-273">SCT se používá k reprezentaci kontextu zabezpečení vytvořeného v SecureConversation a také binárních protokolů pro vyjednávání TLS a SSPI popsaných níže.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="9cf2f-274">2. běžné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="9cf2f-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="9cf2f-275">Časové razítko 2,1</span><span class="sxs-lookup"><span data-stu-id="9cf2f-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="9cf2f-276">Přítomnost časového razítka je řízena pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="9cf2f-277">WCF vždycky serializace wsse: TimeStamp pomocí polí wsse: created a wsse: Expires.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="9cf2f-278">Wsse: časové razítko je vždy podepsáno při použití podepisování.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="9cf2f-279">2,2. pořadí ochrany</span><span class="sxs-lookup"><span data-stu-id="9cf2f-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="9cf2f-280">WCF podporuje pořadí zpráv před zašifrováním a před podepsáním (zásady zabezpečení 1,1).</span><span class="sxs-lookup"><span data-stu-id="9cf2f-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="9cf2f-281">Doporučení "před šifrováním" se doporučují z důvodů, mezi které patří: zprávy chráněné šifrováním před tím, než se přihlásí k zástupným útokům, pokud se nepoužije mechanismus WS-Security 1,1 SignatureConfirmation a signatura přešifrovaného obsahu vytvoří auditování je obtížnější.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="9cf2f-282">2,3 signatura ochrany</span><span class="sxs-lookup"><span data-stu-id="9cf2f-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="9cf2f-283">Při šifrování před použitím podpisu se doporučuje chránit signaturu, aby nedocházelo k útokům hrubou silou za účelem odhadování šifrovaného obsahu nebo podpisového klíče (zejména pokud se vlastní token používá se slabým materiálem klíče).</span><span class="sxs-lookup"><span data-stu-id="9cf2f-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="9cf2f-284">Sada algoritmů 2,4</span><span class="sxs-lookup"><span data-stu-id="9cf2f-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="9cf2f-285">WCF podporuje všechny sady algoritmů uvedené v zásadách zabezpečení 1,1.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="9cf2f-286">2,5 odvození klíče</span><span class="sxs-lookup"><span data-stu-id="9cf2f-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="9cf2f-287">WCF používá odvození klíče pro symetrické klíče, jak je popsáno v tématu WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="9cf2f-288">2,6 potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="9cf2f-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="9cf2f-289">Potvrzení podpisu může být ochrany proti útokům ze střední osoby na ochranu sady podpisů.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="9cf2f-290">2,7 rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="9cf2f-291">Každý režim ověřování popisuje určité rozložení pro záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="9cf2f-292">Prvky v záhlaví zabezpečení jsou částečně seřazené.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="9cf2f-293">Pro definování pořadí podřízených prvků záhlaví zabezpečení definuje zásada WS-Security následující režimy rozvržení záhlaví zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cf2f-294">Zásadní</span><span class="sxs-lookup"><span data-stu-id="9cf2f-294">Strict</span></span>|<span data-ttu-id="9cf2f-295">Položky jsou přidány do záhlaví zabezpečení podle pravidel číslovaného rozložení, které jsou popsány v části zásady zabezpečení 7.7.1, podle obecné zásady deklarace před použitím.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="9cf2f-296">LAX</span><span class="sxs-lookup"><span data-stu-id="9cf2f-296">Lax</span></span>|<span data-ttu-id="9cf2f-297">Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, které odpovídá WSS: zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="9cf2f-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="9cf2f-298">LaxTimestampFirst</span></span>|<span data-ttu-id="9cf2f-299">Stejné jako LAX s tím rozdílem, že první položka v záhlaví zabezpečení musí být wsse: Timestamp</span><span class="sxs-lookup"><span data-stu-id="9cf2f-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="9cf2f-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="9cf2f-300">LaxTimestampLast</span></span>|<span data-ttu-id="9cf2f-301">Stejné jako LAX s tím rozdílem, že poslední položka v záhlaví zabezpečení musí být wsse: Timestamp</span><span class="sxs-lookup"><span data-stu-id="9cf2f-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="9cf2f-302">WCF podporuje všechny čtyři režimy pro rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="9cf2f-303">Struktura záhlaví zabezpečení a příklady zpráv pro režimy ověřování níže následují po "striktním" režimu.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="9cf2f-304">2. běžné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="9cf2f-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="9cf2f-305">V této části najdete příklady zásad pro jednotlivé režimy ověřování spolu s příklady zobrazení struktury záhlaví zabezpečení ve zprávách vyměňovaných klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="9cf2f-306">6,1 Transport Protection</span><span class="sxs-lookup"><span data-stu-id="9cf2f-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="9cf2f-307">WCF nabízí pět režimů ověřování, které používají k ochraně zpráv zabezpečený přenos. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="9cf2f-308">Tyto režimy ověřování jsou vytvořeny pomocí přenosové vazby popsané v části SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="9cf2f-309">Pro režim ověřování UserNameOverTransport je UsernameToken podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="9cf2f-310">Pro jiné režimy ověřování se token zobrazí jako podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="9cf2f-311">Příloha C. 1.2 a C. 1.3 programu SecurityPolicy popisují podrobné rozložení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="9cf2f-312">Následující příklady hlaviček zabezpečení znázorňují striktní rozložení pro daný režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="9cf2f-313">Hodnota vlastnosti "odvozené klíče" pro tokeny ve všech případech je "false".</span><span class="sxs-lookup"><span data-stu-id="9cf2f-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="9cf2f-314">Hodnoty různých vlastností transportní vazby jsou následující:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="9cf2f-315">Časové razítko: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="9cf2f-316">Rozložení záhlaví zabezpečení: striktní</span><span class="sxs-lookup"><span data-stu-id="9cf2f-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="9cf2f-317">Sada algoritmů: Basic256</span><span class="sxs-lookup"><span data-stu-id="9cf2f-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="9cf2f-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="9cf2f-319">V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token, který se vždy odesílá z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="9cf2f-320">Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="9cf2f-321">Použitá vazba je přenosová vazba.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="9cf2f-322">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-323">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="9cf2f-324">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-324">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-325">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="9cf2f-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="9cf2f-327">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako připravující token, který se vždycky odesílá z iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="9cf2f-328">Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="9cf2f-329">Použitá vazba je přenosová vazba.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="9cf2f-330">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-331">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="9cf2f-332">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-332">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-333">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="9cf2f-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="9cf2f-335">V tomto režimu ověřování klient neověřuje službu, například, ale prezentuje token vydaný službou tokenu zabezpečení (STS) a prokáže znalosti sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="9cf2f-336">Vydaný token se zobrazí ve vrstvě SOAP jako průkazní token, který je vždycky odesílán od iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="9cf2f-337">Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="9cf2f-338">Vazba je přenosová vazba.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="9cf2f-339">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-340">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="9cf2f-341">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-341">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-342">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="9cf2f-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="9cf2f-344">V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="9cf2f-345">Token protokolu Kerberos se zobrazí ve vrstvě SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="9cf2f-346">Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="9cf2f-347">Vazba je přenosová vazba.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="9cf2f-348">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-349">Rozložení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="9cf2f-350">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-350">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-351">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="9cf2f-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="9cf2f-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="9cf2f-353">V tomto režimu se k ověřování klienta a serveru používá protokol vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="9cf2f-354">Kerberos se používá, pokud je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="9cf2f-355">Výsledný SCT se zobrazí ve vrstvě SOAP jako průkazní token, který je vždy odeslán od iniciátoru příjemci.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="9cf2f-356">Služba se navíc ověřuje na transportní vrstvě pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-357">Použitá vazba je přenosová vazba.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-357">The binding used is a transport binding.</span></span> <span data-ttu-id="9cf2f-358">"SPNEGO" (vyjednávání) popisuje, jak WCF používá protokol binárního vyjednávání SSPI s WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="9cf2f-359">Příklady hlaviček zabezpečení v této části jsou po navázání SCT prostřednictvím metody handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="9cf2f-360">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="9cf2f-361">Příklady záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf2f-361">Security Header Examples</span></span>  
 <span data-ttu-id="9cf2f-362">Jakmile je token kontextu zabezpečení vytvořen pomocí SPNEGO handshake pomocí binárního vyjednávání WS-Trust, budou zprávy aplikace obsahovat záhlaví zabezpečení s následující strukturou.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="9cf2f-363">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-363">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-364">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="9cf2f-365">6,2 použití certifikátů X. 509 pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="9cf2f-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="9cf2f-366">Tato část popisuje následující režimy ověřování: MutualCertificate WSS 1.0, vzájemné CertificateDuplex, MutualCertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="9cf2f-367">6.2.1 MutualCertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="9cf2f-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="9cf2f-368">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="9cf2f-369">Služba je také ověřena pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="9cf2f-370">Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="9cf2f-371">Token iniciátoru: certifikát X. 509 klienta s režimem zahrnutí nastaveným na. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="9cf2f-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="9cf2f-372">Token příjemce: je nastavený certifikát X. 509 serveru s režimem zahrnutí. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="9cf2f-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="9cf2f-373">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-374">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-375">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-376">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-377">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-378">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-379">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-379">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-380">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-380">Response</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-381">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="9cf2f-382">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-382">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-383">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="9cf2f-384">MutualCertificateDuplex 6.2.2</span><span class="sxs-lookup"><span data-stu-id="9cf2f-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="9cf2f-385">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="9cf2f-386">Služba je také ověřena pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="9cf2f-387">Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="9cf2f-388">Token iniciátoru: certifikát x509 klienta, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="9cf2f-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="9cf2f-389">Token příjemce: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToInitiator.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="9cf2f-390">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-391">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-392">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-393">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-394">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-395">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-396">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="9cf2f-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-397">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-398">Žádost a odpověď</span><span class="sxs-lookup"><span data-stu-id="9cf2f-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="9cf2f-399">6.2.3 s použitím SymmetricBinding s ověřováním služby X. 509</span><span class="sxs-lookup"><span data-stu-id="9cf2f-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="9cf2f-400">"WSS10" poskytl omezená podpora pro scénáře s tokeny x509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="9cf2f-401">Například neexistuje způsob, jak poskytnout podpisovou a šifrovací ochranu pro zprávy pomocí tokenu x509 služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="9cf2f-402">"WSS11" zavedlo použití EncryptedKey jako symetrického tokenu.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="9cf2f-403">Nyní může být pro ochranu požadavků a odpovědí použit dočasný klíč zašifrovaný pro certifikát X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="9cf2f-404">Tento model se používá v režimech ověřování popsaných v části 6,4.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="9cf2f-405">WS-SecurityPolicy popisuje tento vzor pomocí SymmetricBinding s tokenem x509 Service jako tokenem ochrany.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="9cf2f-406">Režimy ověřování AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používají podobné instance SP: SymmetricBinding s následujícími hodnotami vlastností:</span><span class="sxs-lookup"><span data-stu-id="9cf2f-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="9cf2f-407">Token ochrany: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="9cf2f-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="9cf2f-408">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-409">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-410">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-411">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-412">Výše uvedené režimy ověřování se liší pouze podpůrnými tokeny, které používají.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="9cf2f-413">AnonymousForCertificate nemá žádné podpůrné tokeny, MutualCertificate WSS 1,1 má certifikát x509 klienta jako přihlášené tokeny pro podporu, UserNameForCertificate má token UserName jako podepsaný podpůrný token a IssuedTokenForCertificate má vydaný token jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="9cf2f-414">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-414">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-415">Symetrická vazba</span><span class="sxs-lookup"><span data-stu-id="9cf2f-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="9cf2f-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="9cf2f-417">V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-418">Použitá vazba je instancí symetrických vazeb, jak je popsáno v 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="9cf2f-419">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-419">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-420">Podrobnosti o vazbě najdete v části "zásady" v 6.2.3 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-421">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-422">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-422">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-423">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-424">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-425">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-425">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-426">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="9cf2f-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="9cf2f-428">V tomto režimu ověřování klient ověřuje službu pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="9cf2f-429">Služba se ověřuje pro klienta pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-430">Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="9cf2f-431">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-431">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-432">Podrobnosti o vazbě najdete v části "zásady" v 6.2.3 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-433">Podepsaný podpůrný token</span><span class="sxs-lookup"><span data-stu-id="9cf2f-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-434">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-435">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-435">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-436">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-437">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-438">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-438">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-439">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="9cf2f-440">6.2.6 MutualCertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="9cf2f-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="9cf2f-441">V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="9cf2f-442">Služba je také ověřena pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-443">Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="9cf2f-444">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-444">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-445">Podrobnosti o vazbě najdete v tématu věnovaném zásadám 6.2.3.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-446">Schvaluje se podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-447">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-448">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-448">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-449">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-450">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-451">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-451">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-452">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="9cf2f-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="9cf2f-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="9cf2f-454">V tomto režimu ověřování klient neověřuje službu, jako je, ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="9cf2f-455">Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="9cf2f-456">Služba se ověřuje pro klienta pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-457">Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="9cf2f-458">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-458">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-459">Podrobnosti o vazbě najdete v tématu zásady v 6.2.3 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-460">Schvaluje se podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-461">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-462">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-462">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-463">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-464">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-465">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-465">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-466">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="9cf2f-467">protokol Kerberos 6,3</span><span class="sxs-lookup"><span data-stu-id="9cf2f-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="9cf2f-468">V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="9cf2f-469">Stejný lístek taky zajišťuje ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="9cf2f-470">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="9cf2f-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="9cf2f-471">Token ochrany: lístek protokolu Kerberos, režim zahrnutí je nastaven na. ../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="9cf2f-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="9cf2f-472">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-473">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-474">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-475">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-476">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-477">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-478">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-478">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-479">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-480">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-481">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="9cf2f-482">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="9cf2f-483">6,4 třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="9cf2f-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="9cf2f-484">V tomto režimu ověřování klient neověřuje službu, takže klient prezentuje token vydaný službou STS a prokáže znalost sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="9cf2f-485">Služba není ověřena klientovi, jako by se místo toho služba STS zašifroval sdílený klíč jako součást vydaného tokenu, aby se klíč dešifroval jenom službou.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="9cf2f-486">Použitá vazba je jako symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="9cf2f-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="9cf2f-487">Token ochrany: vydaný token, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="9cf2f-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="9cf2f-488">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-489">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-490">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-491">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-492">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-493">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-494">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-494">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-495">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-496">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-497">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-497">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-498">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="9cf2f-499">6,5 použití SslNegotiated pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="9cf2f-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="9cf2f-500">Tato část popisuje skupinu režimů ověřování, které používají symetrickou vazbu s tokenem ochrany, který je tokenem kontextu zabezpečení na WS-SecureConversation (WS-SC), jehož hodnota klíče je vyjednáno spuštěním protokolu TLS prostřednictvím WS-Trust (WS-T) RST/ RSTR zprávy.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="9cf2f-501">Podrobnosti implementace TLS handshake pomocí WS-Trust jsou popsány v tématu TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="9cf2f-502">V příkladech zprávy budeme předpokládat, že SCT s přidruženým kontextem zabezpečení je již vytvořen pomocí metody handshake.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="9cf2f-503">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="9cf2f-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="9cf2f-504">Token ochrany: SslContextToken, režim zahrnutí je nastaven na. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="9cf2f-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="9cf2f-505">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-506">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-507">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-508">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="9cf2f-509">zásady 6.5.1 pro ověřování služby SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="9cf2f-510">Zásady pro všechny režimy ověřování v této části jsou podobné a liší se pouze konkrétními podepsanými podpůrnými nebo schválenými tokeny.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="9cf2f-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="9cf2f-512">V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-513">Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="9cf2f-514">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-514">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-515">Podrobnosti o vazbách najdete v tématu zásady v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-516">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-517">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-517">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-518">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-519">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-520">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-520">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-521">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="9cf2f-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="9cf2f-523">V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="9cf2f-524">Služba se ověřuje pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-525">Použitá vazba je instancí symetrických vazeb, jak je popsáno v 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="9cf2f-526">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-526">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-527">Podrobnosti o vazbě najdete v části 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-528">Podepsaný podpůrný token</span><span class="sxs-lookup"><span data-stu-id="9cf2f-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-529">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-530">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-530">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-531">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-532">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-533">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-533">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-534">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="9cf2f-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="9cf2f-536">V tomto režimu ověřování klient neověřuje službu, jako by ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="9cf2f-537">Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="9cf2f-538">Služba se ověřuje pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="9cf2f-539">Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="9cf2f-540">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-540">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-541">Podrobnosti o vazbě najdete v části 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-542">Schvaluje se podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-543">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-544">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-544">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-545">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-546">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-547">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-547">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-548">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="9cf2f-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="9cf2f-550">V tomto režimu ověřování se klient a služba ověřují pomocí certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="9cf2f-551">Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="9cf2f-552">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-552">Policy</span></span>  
  
 <span data-ttu-id="9cf2f-553">Podrobnosti o vazbě najdete v části 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="9cf2f-554">Schvaluje se podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-555">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-556">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-556">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-557">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-558">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-559">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-559">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-560">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="9cf2f-561">6,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="9cf2f-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="9cf2f-562">V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="9cf2f-563">Kerberos se používá, pokud je to možné, jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="9cf2f-564">Použitá vazba je symetrická vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="9cf2f-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="9cf2f-565">Token ochrany: SpnegoContextToken, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="9cf2f-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="9cf2f-566">Ochrana tokenů: false</span><span class="sxs-lookup"><span data-stu-id="9cf2f-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="9cf2f-567">Celé záhlaví a podpisy textu: pravda</span><span class="sxs-lookup"><span data-stu-id="9cf2f-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="9cf2f-568">Pořadí ochrany: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="9cf2f-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="9cf2f-569">Šifrovat podpis: true</span><span class="sxs-lookup"><span data-stu-id="9cf2f-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="9cf2f-570">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-571">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-572">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-572">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-573">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-574">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-575">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-575">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-576">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="9cf2f-577">6,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="9cf2f-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="9cf2f-578">Použitá vazba je symetrická vazba s tokenem ochrany, která je SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="9cf2f-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="9cf2f-579">SCT se vyjednávat pomocí WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC) podle vnořené vazby, která je sám symetrickou vazbou, která používá protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="9cf2f-580">Protokol vyjednávání bude používat protokol Kerberos k ověřování klienta a serveru, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="9cf2f-581">Pokud se protokol Kerberos nedá použít, přepne se na NTLM.</span><span class="sxs-lookup"><span data-stu-id="9cf2f-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="9cf2f-582">politických</span><span class="sxs-lookup"><span data-stu-id="9cf2f-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="9cf2f-583">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="9cf2f-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="9cf2f-584">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-584">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-585">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="9cf2f-586">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="9cf2f-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="9cf2f-587">Request</span><span class="sxs-lookup"><span data-stu-id="9cf2f-587">Request</span></span>  
  
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
  
 <span data-ttu-id="9cf2f-588">Základě</span><span class="sxs-lookup"><span data-stu-id="9cf2f-588">Response</span></span>  
  
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
