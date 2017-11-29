---
title: "Protokoly zabezpečení verze 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="b5a24-102">Protokoly zabezpečení verze 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="b5a24-103">Protokoly webových služeb zabezpečení zadejte mechanismy zabezpečení webové služby, které se týkají všech existujícího podnikového zasílání zpráv požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="b5a24-104">Tato část popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podrobnosti o verzi 1.0 (implementované v <xref:System.ServiceModel.Channels.SecurityBindingElement>) pro protokoly zabezpečení následující webových služeb.</span><span class="sxs-lookup"><span data-stu-id="b5a24-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="b5a24-105">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="b5a24-105">Specification/Document</span></span>|<span data-ttu-id="b5a24-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="b5a24-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="b5a24-107">WSS: Zabezpečení zpráv protokolu SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="b5a24-108">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-SOAP-Message-Security-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="b5a24-109">WSS: Uživatelské jméno Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="b5a24-110">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="b5a24-111">WSS: X509 Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="b5a24-112">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-x509-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="b5a24-113">WSS: SAML 1.1 Token profil 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="b5a24-114">http://docs.oasis-open.org/WSS/oasis-WSS-SAML-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="b5a24-115">WSS: Zabezpečení zpráv SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="b5a24-116">http://www.oasis-open.org/committees/download.php/16790/WSS-V1.1-spec-OS-SOAPMessageSecurity.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="b5a24-117">WSS uživatelské jméno tokenu Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="b5a24-118">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="b5a24-119">WSS: X.509 tokenu Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="b5a24-120">http://www.oasis-open.org/committees/download.php/16785/WSS-V1.1-spec-OS-x509TokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="b5a24-121">WSS: Token protokolu Kerberos Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="b5a24-122">http://www.oasis-open.org/committees/download.php/16788/WSS-V1.1-spec-OS-KerberosTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="b5a24-123">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="b5a24-124">http://www.oasis-open.org/committees/download.php/16768/WSS-V1.1-spec-OS-SAMLTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="b5a24-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="b5a24-125">WS zabezpečené konverzace</span><span class="sxs-lookup"><span data-stu-id="b5a24-125">WS-Secure Conversation</span></span>|<span data-ttu-id="b5a24-126">http://msdn.microsoft.com/ws/2005/02/ws-Secure-conversation/</span><span class="sxs-lookup"><span data-stu-id="b5a24-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="b5a24-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="b5a24-127">WS-Trust</span></span>|<span data-ttu-id="b5a24-128">http://msdn.microsoft.com/ws/2005/02/WS-Trust/</span><span class="sxs-lookup"><span data-stu-id="b5a24-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="b5a24-129">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="b5a24-129">Application Note:</span></span><br /><br /> <span data-ttu-id="b5a24-130">Pomocí protokolu WS-Trust pro TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="b5a24-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="b5a24-131">K publikování</span><span class="sxs-lookup"><span data-stu-id="b5a24-131">To be published</span></span>|  
|<span data-ttu-id="b5a24-132">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="b5a24-132">Application Note:</span></span><br /><br /> <span data-ttu-id="b5a24-133">Pomocí protokolu WS-Trust pro SPNEGO</span><span class="sxs-lookup"><span data-stu-id="b5a24-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="b5a24-134">K publikování</span><span class="sxs-lookup"><span data-stu-id="b5a24-134">To be published</span></span>|  
|<span data-ttu-id="b5a24-135">Poznámka: aplikace:</span><span class="sxs-lookup"><span data-stu-id="b5a24-135">Application Note:</span></span><br /><br /> <span data-ttu-id="b5a24-136">Webové služby adresování odkazy na koncový bod a Identity</span><span class="sxs-lookup"><span data-stu-id="b5a24-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="b5a24-137">K publikování</span><span class="sxs-lookup"><span data-stu-id="b5a24-137">To be published</span></span>|  
|<span data-ttu-id="b5a24-138">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="b5a24-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="b5a24-139">(2005/07)</span></span>|<span data-ttu-id="b5a24-140">http://msdn.microsoft.com/ws/2005/07/WS-Security-Policy/</span><span class="sxs-lookup"><span data-stu-id="b5a24-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="b5a24-141">ve znění chybující odeslána OASIS WS-SX technický výbor http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="b5a24-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-142">, verze 1, poskytuje 17 režimy ověřování, které lze použít jako základ pro konfigurace zabezpečení webové služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="b5a24-143">Každý režimu je optimalizovaná pro společnou sadu požadavky na nasazení, jako například:</span><span class="sxs-lookup"><span data-stu-id="b5a24-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="b5a24-144">Přihlašovací údaje použité k ověření klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="b5a24-145">Zpráva nebo přenosu ochrany mechanismy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="b5a24-146">Zpráva exchange vzory.</span><span class="sxs-lookup"><span data-stu-id="b5a24-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="b5a24-147">Režim ověřování</span><span class="sxs-lookup"><span data-stu-id="b5a24-147">Authentication Mode</span></span>|<span data-ttu-id="b5a24-148">Ověření klienta</span><span class="sxs-lookup"><span data-stu-id="b5a24-148">Client Authentication</span></span>|<span data-ttu-id="b5a24-149">Ověření serveru</span><span class="sxs-lookup"><span data-stu-id="b5a24-149">Server Authentication</span></span>|<span data-ttu-id="b5a24-150">Režim</span><span class="sxs-lookup"><span data-stu-id="b5a24-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="b5a24-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-151">UserNameOverTransport</span></span>|<span data-ttu-id="b5a24-152">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="b5a24-152">User name/password</span></span>|<span data-ttu-id="b5a24-153">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-153">X509</span></span>|<span data-ttu-id="b5a24-154">Přenos</span><span class="sxs-lookup"><span data-stu-id="b5a24-154">Transport</span></span>|  
|<span data-ttu-id="b5a24-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-155">CertificateOverTransport</span></span>|<span data-ttu-id="b5a24-156">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-156">X509</span></span>|<span data-ttu-id="b5a24-157">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-157">X509</span></span>|<span data-ttu-id="b5a24-158">Přenos</span><span class="sxs-lookup"><span data-stu-id="b5a24-158">Transport</span></span>|  
|<span data-ttu-id="b5a24-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-159">KerberosOverTransport</span></span>|<span data-ttu-id="b5a24-160">Windows</span><span class="sxs-lookup"><span data-stu-id="b5a24-160">Windows</span></span>|<span data-ttu-id="b5a24-161">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-161">X509</span></span>|<span data-ttu-id="b5a24-162">Přenos</span><span class="sxs-lookup"><span data-stu-id="b5a24-162">Transport</span></span>|  
|<span data-ttu-id="b5a24-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="b5a24-164">Federované</span><span class="sxs-lookup"><span data-stu-id="b5a24-164">Federated</span></span>|<span data-ttu-id="b5a24-165">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-165">X509</span></span>|<span data-ttu-id="b5a24-166">Přenos</span><span class="sxs-lookup"><span data-stu-id="b5a24-166">Transport</span></span>|  
|<span data-ttu-id="b5a24-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="b5a24-168">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="b5a24-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="b5a24-169">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="b5a24-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="b5a24-170">Přenos</span><span class="sxs-lookup"><span data-stu-id="b5a24-170">Transport</span></span>|  
|<span data-ttu-id="b5a24-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-171">AnonymousForCertificate</span></span>|<span data-ttu-id="b5a24-172">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5a24-172">None</span></span>|<span data-ttu-id="b5a24-173">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-173">X509</span></span>|<span data-ttu-id="b5a24-174">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-174">Message</span></span>|  
|<span data-ttu-id="b5a24-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-175">UserNameForCertificate</span></span>|<span data-ttu-id="b5a24-176">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="b5a24-176">User name/password</span></span>|<span data-ttu-id="b5a24-177">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-177">X509</span></span>|<span data-ttu-id="b5a24-178">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-178">Message</span></span>|  
|<span data-ttu-id="b5a24-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-179">MutualCertificate</span></span>|<span data-ttu-id="b5a24-180">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-180">X509</span></span>|<span data-ttu-id="b5a24-181">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-181">X509</span></span>|<span data-ttu-id="b5a24-182">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-182">Message</span></span>|  
|<span data-ttu-id="b5a24-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="b5a24-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="b5a24-184">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-184">X509</span></span>|<span data-ttu-id="b5a24-185">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-185">X509</span></span>|<span data-ttu-id="b5a24-186">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-186">Message</span></span>|  
|<span data-ttu-id="b5a24-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="b5a24-188">Federované</span><span class="sxs-lookup"><span data-stu-id="b5a24-188">Federated</span></span>|<span data-ttu-id="b5a24-189">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-189">X509</span></span>|<span data-ttu-id="b5a24-190">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-190">Message</span></span>|  
|<span data-ttu-id="b5a24-191">Pomocí protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="b5a24-191">Kerberos</span></span>|<span data-ttu-id="b5a24-192">Windows</span><span class="sxs-lookup"><span data-stu-id="b5a24-192">Windows</span></span>|<span data-ttu-id="b5a24-193">Windows</span><span class="sxs-lookup"><span data-stu-id="b5a24-193">Windows</span></span>|<span data-ttu-id="b5a24-194">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-194">Message</span></span>|  
|<span data-ttu-id="b5a24-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="b5a24-195">IssuedToken</span></span>|<span data-ttu-id="b5a24-196">Federované</span><span class="sxs-lookup"><span data-stu-id="b5a24-196">Federated</span></span>|<span data-ttu-id="b5a24-197">Federované</span><span class="sxs-lookup"><span data-stu-id="b5a24-197">Federated</span></span>|<span data-ttu-id="b5a24-198">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-198">Message</span></span>|  
|<span data-ttu-id="b5a24-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-199">SspiNegotiated</span></span>|<span data-ttu-id="b5a24-200">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="b5a24-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="b5a24-201">Windows Sspi vyjednal</span><span class="sxs-lookup"><span data-stu-id="b5a24-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="b5a24-202">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-202">Message</span></span>|  
|<span data-ttu-id="b5a24-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="b5a24-204">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5a24-204">None</span></span>|<span data-ttu-id="b5a24-205">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="b5a24-205">X509, TLS-Nego</span></span>|<span data-ttu-id="b5a24-206">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-206">Message</span></span>|  
|<span data-ttu-id="b5a24-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="b5a24-208">Uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="b5a24-208">User name/password</span></span>|<span data-ttu-id="b5a24-209">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="b5a24-209">X509, TLS-Nego</span></span>|<span data-ttu-id="b5a24-210">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-210">Message</span></span>|  
|<span data-ttu-id="b5a24-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-211">MutualSslNegotiated</span></span>|<span data-ttu-id="b5a24-212">X509</span><span class="sxs-lookup"><span data-stu-id="b5a24-212">X509</span></span>|<span data-ttu-id="b5a24-213">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="b5a24-213">X509, TLS-Nego</span></span>|<span data-ttu-id="b5a24-214">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-214">Message</span></span>|  
|<span data-ttu-id="b5a24-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="b5a24-216">Federované</span><span class="sxs-lookup"><span data-stu-id="b5a24-216">Federated</span></span>|<span data-ttu-id="b5a24-217">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="b5a24-217">X509, TLS-Nego</span></span>|<span data-ttu-id="b5a24-218">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b5a24-218">Message</span></span>|  
  
 <span data-ttu-id="b5a24-219">Koncové body pomocí těchto režimech ověřování můžete express jejich požadavky na zabezpečení pomocí protokolu WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="b5a24-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="b5a24-220">Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a obsahuje příklady zásad a zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5a24-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-221">využívá WS-SecureConversation pro poskytování zabezpečených relací podpory k ochraně výměny více zpráv mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="b5a24-221"> leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="b5a24-222">Podrobné informace o nasazení naleznete v tématu "Zabezpečené relace" níže.</span><span class="sxs-lookup"><span data-stu-id="b5a24-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="b5a24-223">Kromě režimy ověřování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsahuje nastavení pro kontrolu obecné ochrany mechanismy, které se vztahují na většinu režimy ověřování na základě zabezpečení zpráv, například: pořadí podpis versus operace šifrování, algoritmus sady odvození klíče a potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="b5a24-224">V tomto dokumentu se používají následující předpony a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b5a24-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="b5a24-225">Předpona</span><span class="sxs-lookup"><span data-stu-id="b5a24-225">Prefix</span></span>|<span data-ttu-id="b5a24-226">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b5a24-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="b5a24-227">s</span><span class="sxs-lookup"><span data-stu-id="b5a24-227">s</span></span>|<span data-ttu-id="b5a24-228">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="b5a24-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="b5a24-229">SP</span><span class="sxs-lookup"><span data-stu-id="b5a24-229">sp</span></span>|<span data-ttu-id="b5a24-230">http://schemas.xmlsoap.org/ws/2005/07/securityPolicy</span><span class="sxs-lookup"><span data-stu-id="b5a24-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="b5a24-231">A</span><span class="sxs-lookup"><span data-stu-id="b5a24-231">a</span></span>|<span data-ttu-id="b5a24-232">http://www.w3.org/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="b5a24-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="b5a24-233">wsse</span><span class="sxs-lookup"><span data-stu-id="b5a24-233">wsse</span></span>|<span data-ttu-id="b5a24-234">BUDE URČENO – IDENTIFIKÁTOR URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="b5a24-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="b5a24-235">wsse11</span></span>|<span data-ttu-id="b5a24-236">BUDE URČENO – IDENTIFIKÁTOR URI OASIS WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="b5a24-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="b5a24-237">týkajících</span><span class="sxs-lookup"><span data-stu-id="b5a24-237">wsu</span></span>|<span data-ttu-id="b5a24-238">Bude určeno – nástroj URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="b5a24-239">DS</span><span class="sxs-lookup"><span data-stu-id="b5a24-239">ds</span></span>|<span data-ttu-id="b5a24-240">Bude určeno – identifikátor URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="b5a24-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="b5a24-241">WST</span><span class="sxs-lookup"><span data-stu-id="b5a24-241">wst</span></span>|<span data-ttu-id="b5a24-242">Bude určeno – WS-Trust 2005/02 identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="b5a24-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="b5a24-243">wssc</span><span class="sxs-lookup"><span data-stu-id="b5a24-243">wssc</span></span>|<span data-ttu-id="b5a24-244">Bude určeno – WS-SecureConversation 2005/02 identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="b5a24-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="b5a24-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="b5a24-245">wsaw</span></span>|<span data-ttu-id="b5a24-246">Bude určeno - WS-Addressing zásad obor názvů</span><span class="sxs-lookup"><span data-stu-id="b5a24-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="b5a24-247">WSP</span><span class="sxs-lookup"><span data-stu-id="b5a24-247">wsp</span></span>|<span data-ttu-id="b5a24-248">http://schemas.xmlsoap.org/ws/2004/09/Policy</span><span class="sxs-lookup"><span data-stu-id="b5a24-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="b5a24-249">mssp</span><span class="sxs-lookup"><span data-stu-id="b5a24-249">mssp</span></span>|<span data-ttu-id="b5a24-250">http://schemas.microsoft.com/ws/2005/07/securityPolicy</span><span class="sxs-lookup"><span data-stu-id="b5a24-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="b5a24-251">1. Token profily</span><span class="sxs-lookup"><span data-stu-id="b5a24-251">1. Token Profiles</span></span>  
 <span data-ttu-id="b5a24-252">Webové služby zabezpečení specifikace představují přihlašovací údaje jako tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-253">podporuje následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="b5a24-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="b5a24-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="b5a24-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-255">Následuje UsernameToken10 a UsernameToken11 profily s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="b5a24-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="b5a24-256">Atribut R1101 PasswordType UsernameToken\Password elementu musí být buď vynechána, nebo musí mít hodnotu #PasswordText (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b5a24-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="b5a24-257">Jeden můžete implementovat #PasswordDigest pomocí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b5a24-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="b5a24-258">Bylo zjištěno, že byl #PasswordDigest často zaměněny být dostatečně zabezpečeného hesla ochranný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="b5a24-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="b5a24-259">Ale #PasswordDigest nemůže sloužit jako náhrada pro šifrování UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="b5a24-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="b5a24-260">Primární cílem #PasswordDigest je ochrana proti útoku formou opakovaného.</span><span class="sxs-lookup"><span data-stu-id="b5a24-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="b5a24-261">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režimy ověřování, hrozby útoku formou opakovaného přehrávání napraveny pomocí podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="b5a24-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="b5a24-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy vysílá hodnotu Nonce a vytvořen dílčí prvky UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="b5a24-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="b5a24-263">Tyto prvky jsou určeny ke zjišťování opakování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-264">Místo toho používá podpisy zpráv.</span><span class="sxs-lookup"><span data-stu-id="b5a24-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="b5a24-265">OASIS WSS protokolu SOAP zprávy zabezpečení UsernameToken Profile 1.1 (UsernameToken11) zavedla odvození klíče z funkce hesla.</span><span class="sxs-lookup"><span data-stu-id="b5a24-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="b5a24-266">Heslo B1103 UsernameToken nesmí se používat pro odvození klíče a proto pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="b5a24-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="b5a24-267">Odůvodnění: hesla jsou obvykle považovány za příliš slabé má být použit pro kryptografické operace.</span><span class="sxs-lookup"><span data-stu-id="b5a24-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="b5a24-268">1.2 x 509 tokenu</span><span class="sxs-lookup"><span data-stu-id="b5a24-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-269">podporuje certifikáty X509v3 jako typ přihlašovacích údajů a dodržuje X509TokenProfile1.0 a X509TokenProfile1.1 s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="b5a24-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="b5a24-270">Atribut R1201 The typ hodnoty v elementu BinarySecurityToken musí mít hodnotu #X509v3 obsahuje certifikát X509v3.</span><span class="sxs-lookup"><span data-stu-id="b5a24-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="b5a24-271">WSS X509 tokenu profil 1.0 a 1.1 definovat také #X509PKIPathv1 a PKCS&#7; jako typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="b5a24-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-272">Tyto typy nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b5a24-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="b5a24-273">R1202 Pokud rozšíření identifikátor klíče SubjectKeyIdentifier (subjektu) se nachází v X509 certifikát, by měl být wsse:KeyIdentifier používá pro externí odkazy na token, s typ hodnoty atributu jako #X509SubjectKeyIdentifier a jejího obsahu hodnota kódováním Base 64 rozšíření identifikátor klíče subjektu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="b5a24-274">Identifikátor klíče subjektu odkazy jsou široce implementována a ověřené jako vysoce interoperabilní externí odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="b5a24-275">R1203 Externího odkazu na X509 zabezpečení tokenu by MĚL používat ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="b5a24-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="b5a24-276">Pokud X509TokenProfile1.1 R1204 se používá, externí odkaz na X509 tokenu zabezpečení by MĚL použít kryptografický otisk zaváděné WS-zabezpečení 1.1.</span><span class="sxs-lookup"><span data-stu-id="b5a24-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-277">podporuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="b5a24-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="b5a24-278">Ale existují problémy s interoperabilitou s X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá k porovnání dvou hodnot X509IssuerSerial řetězec.</span><span class="sxs-lookup"><span data-stu-id="b5a24-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="b5a24-279">Proto pokud jeden změní součástí název předmětu a odesílá do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odkaz na certifikát služby, nemusí být nalezen.</span><span class="sxs-lookup"><span data-stu-id="b5a24-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="b5a24-280">1.3 Token protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="b5a24-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-281">podporuje KerberosTokenProfile1.1 pro účely ověřování systému Windows s těmito omezeními:</span><span class="sxs-lookup"><span data-stu-id="b5a24-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="b5a24-282">R1301 A protokolu Kerberos Token musí mít hodnotu GSS zabalená AP_REQ v4 protokolu Kerberos, jak jsou definovány v GSS_API a specifikace protokolu Kerberos a musí mít atribut ValueType s GSS_Kerberosv5_AP_REQ # hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-283">používá GSS zabalené AP protokolu Kerberos-REQ, není úplné Asie-požadavků</span><span class="sxs-lookup"><span data-stu-id="b5a24-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="b5a24-284">Toto je nejlepším postupem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="b5a24-285">1.4 SAML v1.1 Token</span><span class="sxs-lookup"><span data-stu-id="b5a24-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-286">podporuje tokenu SAML WSS profily 1.0 a 1.1 pro tokeny SAML verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="b5a24-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="b5a24-287">Je možné implementovat jiných verzích formáty tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="b5a24-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="b5a24-288">1.5 Token kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-289">podporuje zabezpečení kontextu tokenu (SCT) byla zavedená v WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="b5a24-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="b5a24-290">SCT se používá k reprezentování kontextu zabezpečení nastavené v SecureConversation také jako binární vyjednávání protokoly TLS a rozhraní SSPI, které jsou popsané dál.</span><span class="sxs-lookup"><span data-stu-id="b5a24-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="b5a24-291">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="b5a24-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="b5a24-292">2.1 časové razítko</span><span class="sxs-lookup"><span data-stu-id="b5a24-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="b5a24-293">Přítomnost časového razítka je řízena pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5a24-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-294">vždy serializuje wsse:TimeStamp s wsse: vytvoření a wsse: vyprší platnost pole.</span><span class="sxs-lookup"><span data-stu-id="b5a24-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="b5a24-295">Při podepisování se používá, je vždy podepisován wsse:TimeStamp.</span><span class="sxs-lookup"><span data-stu-id="b5a24-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="b5a24-296">2.2 ochrany pořadí</span><span class="sxs-lookup"><span data-stu-id="b5a24-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-297">podporuje pořadí ochrany zprávy "Přihlášení před šifrování" a "Šifrovat před přihlášení" (1.1 zásady zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="b5a24-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="b5a24-298">"Podepsat před šifrovat" se doporučuje důvodů včetně: zprávy chráněné pomocí šifrování před přihlašovacích jsou otevřené podpis nahrazení útoky, pokud se používá mechanismus SignatureConfirmation 1.1 WS-zabezpečení a umožňuje podpis přes šifrovaný obsah těžší auditování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="b5a24-299">2.3 podpis ochrany</span><span class="sxs-lookup"><span data-stu-id="b5a24-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="b5a24-300">Pokud se používá šifrování před přihlášení, se doporučuje k ochraně podpis před útoky hrubou silou pro uhodnutí šifrovaný obsah nebo podpisový klíč (zejména při vlastního tokenu se používá s slabé materiál klíče).</span><span class="sxs-lookup"><span data-stu-id="b5a24-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="b5a24-301">2.4 algoritmus Suite</span><span class="sxs-lookup"><span data-stu-id="b5a24-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-302">podporuje všechny sady algoritmus uvedené v 1.1 zásady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="b5a24-303">2.5 odvození klíče</span><span class="sxs-lookup"><span data-stu-id="b5a24-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-304">používá "Klíč odvození symetrické klíče", jak je popsáno v WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="b5a24-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="b5a24-305">2.6 potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="b5a24-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="b5a24-306">Potvrzení podpisu může být jako ochranu před útoky střední man k ochraně sadu podpisy.</span><span class="sxs-lookup"><span data-stu-id="b5a24-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="b5a24-307">2.7 rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="b5a24-308">Každý režim ověřování popisuje rozložení pro záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="b5a24-309">Prvky v záhlaví zabezpečení jsou polovičním seřazené.</span><span class="sxs-lookup"><span data-stu-id="b5a24-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="b5a24-310">Pokud chcete definovat pořadí podřízených elementů záhlaví zabezpečení, zásady zabezpečení WS definuje v následujících režimech rozložení záhlaví zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="b5a24-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5a24-311">Striktní</span><span class="sxs-lookup"><span data-stu-id="b5a24-311">Strict</span></span>|<span data-ttu-id="b5a24-312">Položky budou přidány do těchto záhlaví zabezpečení, že pravidla číslem rozložení popsané v zásadách zabezpečení části 7.7.1 podle obecné Princip "deklarovat před použitím".</span><span class="sxs-lookup"><span data-stu-id="b5a24-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="b5a24-313">Hodnotě lax</span><span class="sxs-lookup"><span data-stu-id="b5a24-313">Lax</span></span>|<span data-ttu-id="b5a24-314">Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, které vyhovuje WSS: zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b5a24-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="b5a24-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="b5a24-315">LaxTimestampFirst</span></span>|<span data-ttu-id="b5a24-316">Stejné jako Lax s tím rozdílem, že první položky v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="b5a24-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="b5a24-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="b5a24-317">LaxTimestampLast</span></span>|<span data-ttu-id="b5a24-318">Stejné jako hodnotě lax s tím rozdílem, že poslední položky v záhlaví zabezpečení musí být wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="b5a24-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-319">podporuje všechny čtyři režimy pro rozvržení záhlaví zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="b5a24-320">Příklady strukturu a zpráva záhlaví zabezpečení pro režimy ověřování níže podle režim "Strict".</span><span class="sxs-lookup"><span data-stu-id="b5a24-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="b5a24-321">2. Společné parametry zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="b5a24-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="b5a24-322">Tato část obsahuje příklady zásad pro každý režim ověřování spolu s příklady zobrazující struktura záhlaví zabezpečení v zprávy vyměňují klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="b5a24-323">6.1 přenosu ochrany</span><span class="sxs-lookup"><span data-stu-id="b5a24-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b5a24-324">poskytuje pět režimy ověřování, které používají zabezpečené přenos k ochraně zprávy; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="b5a24-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="b5a24-325">Tyto režimy ověřování jsou vytvářeny pomocí popsaných v SecurityPolicy vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="b5a24-326">Režim ověřování UsernameToken UserNameOverTransport je podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="b5a24-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="b5a24-327">Pro další režimy ověřování tokenu zobrazí jako podepsaný token či identifikaci.</span><span class="sxs-lookup"><span data-stu-id="b5a24-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="b5a24-328">Příloha C.1.2 a C.1.3 SecurityPolicy popisují rozvržení záhlaví zabezpečení podrobně.</span><span class="sxs-lookup"><span data-stu-id="b5a24-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="b5a24-329">Následující příklad hlavičky zabezpečení zobrazit striktní rozložení pro režim daného ověřování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="b5a24-330">Hodnota vlastnosti "Odvozené klíče" pro tokeny ve všech případech je "false".</span><span class="sxs-lookup"><span data-stu-id="b5a24-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="b5a24-331">Hodnoty různé vlastnosti vazby přenosu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b5a24-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="b5a24-332">Časové razítko: true</span><span class="sxs-lookup"><span data-stu-id="b5a24-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="b5a24-333">Rozvržení záhlaví zabezpečení: striktní</span><span class="sxs-lookup"><span data-stu-id="b5a24-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="b5a24-334">Algoritmus Suite: Basic256</span><span class="sxs-lookup"><span data-stu-id="b5a24-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="b5a24-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="b5a24-336">Tento režim ověřování klient se ověří uživatelské jméno tokenem, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token vždy odeslané ze iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="b5a24-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="b5a24-337">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b5a24-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="b5a24-338">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="b5a24-339">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="b5a24-340">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="b5a24-341">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-341">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-342">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="b5a24-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="b5a24-344">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako či identifikaci podpůrné token, který se vždy odesílá z iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="b5a24-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="b5a24-345">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b5a24-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="b5a24-346">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="b5a24-347">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-347">Policy</span></span>  
  
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
  
 <span data-ttu-id="b5a24-348">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="b5a24-349">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-349">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-350">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="b5a24-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="b5a24-352">S Tento režim ověřování klienta služby, jako například neověřuje, ale místo uvede tokenem vydaným podle zabezpečení tokenu služby (STS) a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="b5a24-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="b5a24-353">Vystavený token se zobrazí ve vrstvě protokolu SOAP či identifikaci podpůrné token, který se vždy odesílá z iniciátoru k příjemce.</span><span class="sxs-lookup"><span data-stu-id="b5a24-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="b5a24-354">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b5a24-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="b5a24-355">Vazba je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="b5a24-356">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-356">Policy</span></span>  
  
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
  
 <span data-ttu-id="b5a24-357">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="b5a24-358">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-358">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-359">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="b5a24-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="b5a24-361">Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="b5a24-362">Token protokolu Kerberos se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="b5a24-363">Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b5a24-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="b5a24-364">Vazba je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="b5a24-365">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-365">Policy</span></span>  
  
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
  
 <span data-ttu-id="b5a24-366">Rozvržení záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="b5a24-367">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-367">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-368">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="b5a24-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="b5a24-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="b5a24-370">Pomocí tohoto režimu vyjednávání protokolu slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="b5a24-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="b5a24-371">Pokud je to možné, používá protokol Kerberos jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="b5a24-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="b5a24-372">Výsledný SCT se zobrazí ve vrstvě protokolu SOAP či identifikaci token podpory, který se vždy odesílá z iniciátor k příjemce.</span><span class="sxs-lookup"><span data-stu-id="b5a24-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="b5a24-373">Služba je kromě ověřit v přenosové vrstvě certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="b5a24-374">Vazba použitá je vazba přenosu.</span><span class="sxs-lookup"><span data-stu-id="b5a24-374">The binding used is a transport binding.</span></span> <span data-ttu-id="b5a24-375">"SPNEGO" (vyjednávání) popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá protokol binární vyjednávání SSPI s WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b5a24-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="b5a24-376">Příklady záhlaví zabezpečení v této části jsou po navázání SCT prostřednictvím SPNEGO handshake.</span><span class="sxs-lookup"><span data-stu-id="b5a24-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="b5a24-377">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="b5a24-378">Příklady záhlaví zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5a24-378">Security Header Examples</span></span>  
 <span data-ttu-id="b5a24-379">Jakmile tokenu kontextu zabezpečení vytvořeno prostřednictvím metody handshake SPNEGO binární vyjednání WS-Trust, zprávy aplikací mít záhlaví zabezpečení s následující strukturou.</span><span class="sxs-lookup"><span data-stu-id="b5a24-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="b5a24-380">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-380">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-381">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="b5a24-382">6.2 pomocí certifikátů X.509 pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="b5a24-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="b5a24-383">Tato část popisuje následující režimy ověřování: MutualCertificate WSS1.0, vzájemné CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="b5a24-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="b5a24-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="b5a24-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="b5a24-385">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="b5a24-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="b5a24-386">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="b5a24-387">Vazba použitá je asymetrické vazbu s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="b5a24-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="b5a24-388">Token iniciátor: certifikát X.509 klienta, s zahrnutí režim nastavený na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="b5a24-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="b5a24-389">Příjemce Token: Server je certifikát X.509, s režimem zahrnutí nastavena .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="b5a24-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="b5a24-390">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-391">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-392">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-393">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-394">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-395">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-396">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-396">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-397">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-397">Response</span></span>  
  
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
  
 <span data-ttu-id="b5a24-398">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="b5a24-399">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-399">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-400">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-400">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="b5a24-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="b5a24-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="b5a24-402">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako iniciátor token.</span><span class="sxs-lookup"><span data-stu-id="b5a24-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="b5a24-403">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="b5a24-404">Vazba použitá je asymetrické vazbu s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="b5a24-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="b5a24-405">Token iniciátor: Klienta X509 certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="b5a24-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="b5a24-406">Příjemce Token: Serveru X509 certifikát, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="b5a24-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="b5a24-407">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-408">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-409">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-410">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-411">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-411">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-412">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-413">Žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="b5a24-413">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-414">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-415">Žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="b5a24-415">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="b5a24-416">6.2.3 pomocí ověřování služby X.509 SymmetricBinding</span><span class="sxs-lookup"><span data-stu-id="b5a24-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="b5a24-417">"WSS10" k dispozici omezená podpora pro scénáře s X509 tokeny.</span><span class="sxs-lookup"><span data-stu-id="b5a24-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="b5a24-418">Například se žádný způsob, jak zajistit ochranu podpis a šifrování zpráv pomocí pouze token služby X509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="b5a24-419">"WSS11" uvedla využití EncryptedKey symetrický token.</span><span class="sxs-lookup"><span data-stu-id="b5a24-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="b5a24-420">Nyní na dočasný klíč šifrována pro certifikát X.509 služby může být použita pro ochranu zprávy požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b5a24-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="b5a24-421">Režimy ověřování, který je popsaný v části 6.4 níže pomocí tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="b5a24-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="b5a24-422">Popisuje tento vzor SymmetricBinding pomocí služby WS-SecurityPolicy X509 token jako token ochrany.</span><span class="sxs-lookup"><span data-stu-id="b5a24-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="b5a24-423">Režimy ověřování AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používat podobné instance sp:SymmetricBinding s následující hodnoty vlastností:</span><span class="sxs-lookup"><span data-stu-id="b5a24-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="b5a24-424">Ochrany Token: X509 serveru certifikát, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="b5a24-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="b5a24-425">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-426">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-427">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-428">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-429">Výše uvedené režimy ověřování podpůrné tokeny, které používají pouze lišit.</span><span class="sxs-lookup"><span data-stu-id="b5a24-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="b5a24-430">AnonymousForCertificate nemá všechny podpůrné tokeny, MutualCertificate WSS 1.1 má klienta X509 certifikátu jako potvrzování podpora tokenů, UserNameForCertificate má Token uživatelské jméno jako podepsaný token a IssuedTokenForCertificate má vystavený token jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="b5a24-431">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-431">Policy</span></span>  
  
 <span data-ttu-id="b5a24-432">Symetrické vazby</span><span class="sxs-lookup"><span data-stu-id="b5a24-432">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="b5a24-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="b5a24-434">S Tento režim ověřování je anonymní klienta a služby je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-435">Vazba použitá instance symetrický vazby je, jak je popsáno v 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="b5a24-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="b5a24-436">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-436">Policy</span></span>  
  
 <span data-ttu-id="b5a24-437">Pro vytvoření vazby podrobnosti najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="b5a24-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-438">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-439">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-439">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-440">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-440">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-441">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-442">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-442">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-443">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-443">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="b5a24-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="b5a24-445">Klient se ověří do služby pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="b5a24-446">Služba se ověřuje na klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-447">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="b5a24-448">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-448">Policy</span></span>  
  
 <span data-ttu-id="b5a24-449">Pro vytvoření vazby podrobnosti najdete v části "Zásady" v 6.2.3 výše</span><span class="sxs-lookup"><span data-stu-id="b5a24-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="b5a24-450">Podepsaný Token podpory</span><span class="sxs-lookup"><span data-stu-id="b5a24-450">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-451">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-452">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-452">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-453">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-453">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-454">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-455">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-455">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-456">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-456">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="b5a24-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="b5a24-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="b5a24-458">S Tento režim ověřování, které klient se ověří pomocí X.509 certificate, která se zobrazí ve vrstvě protokolu SOAP jako token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="b5a24-459">Služba je také ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-460">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="b5a24-461">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-461">Policy</span></span>  
  
 <span data-ttu-id="b5a24-462">Viz zásady v 6.2.3 pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5a24-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="b5a24-463">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="b5a24-463">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-464">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-465">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-465">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-466">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-466">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-467">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-468">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-468">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-469">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-469">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="b5a24-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="b5a24-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="b5a24-471">Pomocí tohoto ověřování režim, který jako takový, ale místo toho se ke službě, neověřuje klient uvede tokenem vydaným službou tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="b5a24-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="b5a24-472">Vystavený token se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="b5a24-473">Služba se ověřuje na klienta pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-474">Vazba použitá je symetrický vazbu s tokenem ochrany se klíče generované klientem zašifrované pomocí veřejného klíče služby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="b5a24-475">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-475">Policy</span></span>  
  
 <span data-ttu-id="b5a24-476">Viz zásady v 6.2.3 výše podrobnosti vazby</span><span class="sxs-lookup"><span data-stu-id="b5a24-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="b5a24-477">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="b5a24-477">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-478">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-479">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-479">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-480">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-480">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-481">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-482">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-482">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-483">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-483">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="b5a24-484">6.3 protokolu Kerberos</span><span class="sxs-lookup"><span data-stu-id="b5a24-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="b5a24-485">Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="b5a24-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="b5a24-486">Tento stejný lístek taky poskytuje ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="b5a24-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="b5a24-487">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="b5a24-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="b5a24-488">Ochrana Token: Lístek protokolu Kerberos, zahrnutí režim je nastaven na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="b5a24-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="b5a24-489">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-490">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-491">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-492">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-493">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-493">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-494">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-495">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-495">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-496">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-496">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-497">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-498">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="b5a24-499">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="b5a24-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="b5a24-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="b5a24-501">S Tento režim ověřování, které klient neověřuje ke službě jako například místo klienta uvede tokenem vydaným pomocí služby tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="b5a24-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="b5a24-502">Služba není ověřen klientovi jako takový, místo toho šifruje Služba tokenů zabezpečení sdílený klíč jako součást vydaný token tak, aby pouze služby může dešifrovat klíč.</span><span class="sxs-lookup"><span data-stu-id="b5a24-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="b5a24-503">Vazba použitá se jako symetrický vazba s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="b5a24-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="b5a24-504">Ochrana Token: Vydán Token, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="b5a24-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="b5a24-505">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-506">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-507">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-508">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-509">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-509">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-510">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-511">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-511">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-512">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-512">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-513">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-514">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-514">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-515">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-515">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="b5a24-516">6.5 pomocí SslNegotiated pro ověřování služby</span><span class="sxs-lookup"><span data-stu-id="b5a24-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="b5a24-517">Tato část popisuje režimy ověřování, které symetrický vazbu pomocí tokenu ochrany se kontextu zabezpečení tokenu za WS-SecureConversation (WS-SC), jehož hodnota klíče vyjedná spuštěním protokol TLS přes WS-Trust (WS-T) RVNÍ skupinu nebo RSTR zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5a24-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="b5a24-518">Podrobnosti o implementaci TLS handshake pomocí WS-Trust jsou popsané v TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="b5a24-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="b5a24-519">Zde v příkladech zpráva budeme předpokládat, SCT s kontextu zabezpečení je již navázáno prostřednictvím provádění metody handshake.</span><span class="sxs-lookup"><span data-stu-id="b5a24-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="b5a24-520">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="b5a24-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="b5a24-521">Ochrana Token: SslContextToken, zahrnutí režim je nastaven na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="b5a24-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="b5a24-522">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-523">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-524">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-525">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="b5a24-526">6.5.1 zásady pro ověřování služby SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="b5a24-527">Zásady pro všechny režimy ověřování v této části jsou podobné a liší pouze konkrétní podpora podepsaný držitelem nebo potvrdit správnost použití tokenů.</span><span class="sxs-lookup"><span data-stu-id="b5a24-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="b5a24-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="b5a24-529">S Tento režim ověřování je anonymní klienta a služby je ověřený pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-530">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="b5a24-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="b5a24-531">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-531">Policy</span></span>  
  
 <span data-ttu-id="b5a24-532">Viz zásady v bodu 6.5.1 výše podrobnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="b5a24-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-533">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-534">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-534">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-535">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-535">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-536">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-537">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-537">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-538">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-538">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="b5a24-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="b5a24-540">Pomocí tohoto ověřování režim, který je klient ověřování pomocí uživatelského jména Token, který se zobrazí ve vrstvě protokolu SOAP jako podepsaný token.</span><span class="sxs-lookup"><span data-stu-id="b5a24-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="b5a24-541">Služba je ověřen pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-542">Vazba použitá instance symetrický vazby je, jak je popsáno v bodu 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="b5a24-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="b5a24-543">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-543">Policy</span></span>  
  
 <span data-ttu-id="b5a24-544">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5a24-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="b5a24-545">Podepsaný Token podpory</span><span class="sxs-lookup"><span data-stu-id="b5a24-545">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-546">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-547">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-547">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-548">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-548">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-549">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-550">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-550">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-551">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-551">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="b5a24-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="b5a24-553">Pomocí tohoto ověřování režim, který jako takový, ale místo toho se ke službě, neověřuje klient uvede tokenem vydaným pomocí služby tokenů zabezpečení a prokáže znalosti sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="b5a24-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="b5a24-554">Vystavený token se zobrazí ve vrstvě protokolu SOAP token podporující potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5a24-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="b5a24-555">Služba je ověřen pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="b5a24-556">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="b5a24-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="b5a24-557">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-557">Policy</span></span>  
  
 <span data-ttu-id="b5a24-558">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5a24-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="b5a24-559">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="b5a24-559">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-560">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-561">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-561">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-562">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-562">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-563">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-564">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-564">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-565">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-565">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="b5a24-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="b5a24-567">S Tento režim ověřování klienta a služby je ověřování pomocí certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="b5a24-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="b5a24-568">Vazba použitá je instance symetrický vazby, jak je popsáno v bodu 6.5.1 výše.</span><span class="sxs-lookup"><span data-stu-id="b5a24-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="b5a24-569">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-569">Policy</span></span>  
  
 <span data-ttu-id="b5a24-570">Najdete v tématu bodu 6.5.1 výše pro vazby podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5a24-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="b5a24-571">Potvrdit správnost podpora tokenu</span><span class="sxs-lookup"><span data-stu-id="b5a24-571">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-572">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-573">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-573">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-574">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-574">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-575">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-576">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-576">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-577">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-577">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="b5a24-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="b5a24-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="b5a24-579">S Tento režim ověřování vyjednávání protokolu slouží k provádění ověření klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="b5a24-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="b5a24-580">Pokud je to možné, používá protokol Kerberos jinak NTLM.</span><span class="sxs-lookup"><span data-stu-id="b5a24-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="b5a24-581">Vazba použitá je symetrický vazbu s následujícími vlastnostmi;</span><span class="sxs-lookup"><span data-stu-id="b5a24-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="b5a24-582">Ochrana Token: SpnegoContextToken, zahrnutí režim je nastaven na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="b5a24-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="b5a24-583">Token ochrany: False</span><span class="sxs-lookup"><span data-stu-id="b5a24-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="b5a24-584">Celý záhlaví a podpisy textu: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="b5a24-585">Pořadí Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="b5a24-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="b5a24-586">Šifrování podpis: True</span><span class="sxs-lookup"><span data-stu-id="b5a24-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="b5a24-587">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-587">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-588">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-589">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-589">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-590">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-590">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-591">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-592">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-592">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-593">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-593">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="b5a24-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="b5a24-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="b5a24-595">Vazba použitá je symetrický vazbu s tokenem ochrany se SCT za WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="b5a24-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="b5a24-596">SCT vyjedná použití podle vnořené vazby, které je samo symetrický vazbu, která používá vyjednávání protokolu WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="b5a24-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="b5a24-597">Vyjednávání protokolu budou používat protokol Kerberos k provedení ověřování klienta a serveru, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="b5a24-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="b5a24-598">Pokud nemůžete používat Kerberos, ji budou vrátit k protokolu NTLM.</span><span class="sxs-lookup"><span data-stu-id="b5a24-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="b5a24-599">Zásady</span><span class="sxs-lookup"><span data-stu-id="b5a24-599">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="b5a24-600">Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="b5a24-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="b5a24-601">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-601">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-602">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-602">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="b5a24-603">Příklady záhlaví zabezpečení: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="b5a24-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="b5a24-604">Požadavek</span><span class="sxs-lookup"><span data-stu-id="b5a24-604">Request</span></span>  
  
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
  
 <span data-ttu-id="b5a24-605">Odpověď</span><span class="sxs-lookup"><span data-stu-id="b5a24-605">Response</span></span>  
  
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
