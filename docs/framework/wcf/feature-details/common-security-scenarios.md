---
title: Běžné scénáře zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 578ec2d7d5abe1285007ad22d8bacd69e695b1d3
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964281"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="15350-102">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="15350-102">Common Security Scenarios</span></span>
<span data-ttu-id="15350-103">Témata v tomto oddílu katalogují několik možných konfigurací zabezpečení klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="15350-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="15350-104">Konfigurace se liší v závislosti na mnoha faktorech.</span><span class="sxs-lookup"><span data-stu-id="15350-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="15350-105">Například zda je služba nebo klient v intranetu nebo zda je zabezpečení poskytované systémem Windows nebo přenos (například HTTPS).</span><span class="sxs-lookup"><span data-stu-id="15350-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15350-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="15350-106">In This Section</span></span>  
 [<span data-ttu-id="15350-107">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="15350-107">Internet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 <span data-ttu-id="15350-108">Příklad veřejného nezabezpečeného klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="15350-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="15350-109">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="15350-109">Intranet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="15350-110">Služba WCF (Basic Windows Communication Foundation) vyvinutá tak, aby poskytovala informace o zabezpečené privátní síti pro aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="15350-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="15350-111">Zabezpečení přenosu pomocí základního ověřování</span><span class="sxs-lookup"><span data-stu-id="15350-111">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 <span data-ttu-id="15350-112">Aplikace umožňuje klientům přihlašovat se pomocí vlastního ověřování.</span><span class="sxs-lookup"><span data-stu-id="15350-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="15350-113">Zabezpečení přenosu pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="15350-113">Transport Security with Windows Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 <span data-ttu-id="15350-114">Zobrazuje klienta a službu zabezpečený zabezpečením systému Windows.</span><span class="sxs-lookup"><span data-stu-id="15350-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="15350-115">Zabezpečení přenosu pomocí anonymního klienta</span><span class="sxs-lookup"><span data-stu-id="15350-115">Transport Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="15350-116">Tento scénář používá zabezpečení přenosu (například HTTPS) k zajištění důvěrnosti a integrity.</span><span class="sxs-lookup"><span data-stu-id="15350-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="15350-117">Zabezpečení přenosu pomocí ověření certifikátem</span><span class="sxs-lookup"><span data-stu-id="15350-117">Transport Security with Certificate Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="15350-118">Zobrazuje klienta a službu zabezpečený certifikátem.</span><span class="sxs-lookup"><span data-stu-id="15350-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="15350-119">Zabezpečení zpráv pomocí anonymního klienta</span><span class="sxs-lookup"><span data-stu-id="15350-119">Message Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="15350-120">Zobrazuje klienta a službu zabezpečený zabezpečením zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="15350-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="15350-121">Zabezpečení zpráv pomocí klienta uživatelského jména</span><span class="sxs-lookup"><span data-stu-id="15350-121">Message Security with a User Name Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 <span data-ttu-id="15350-122">Klient je model Windows Forms aplikace, která klientům umožňuje přihlásit se pomocí uživatelského jména a hesla domény.</span><span class="sxs-lookup"><span data-stu-id="15350-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="15350-123">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="15350-123">Message Security with a Certificate Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 <span data-ttu-id="15350-124">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="15350-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="15350-125">Kontext zabezpečení je vytvořen pomocí vyjednávání protokolu TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="15350-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="15350-126">Zabezpečení zprávy pomocí klienta Windows</span><span class="sxs-lookup"><span data-stu-id="15350-126">Message Security with a Windows Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 <span data-ttu-id="15350-127">Variace klienta certifikátu.</span><span class="sxs-lookup"><span data-stu-id="15350-127">A variation of the certificate client.</span></span> <span data-ttu-id="15350-128">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="15350-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="15350-129">Kontext zabezpečení je vytvořen prostřednictvím vyjednávání TLS.</span><span class="sxs-lookup"><span data-stu-id="15350-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="15350-130">Zabezpečení zpráv pomocí klienta Windows bez vyjednávání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="15350-130">Message Security with a Windows Client without Credential Negotiation</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="15350-131">Zobrazuje klienta a službu zabezpečenou doménou protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="15350-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="15350-132">Zabezpečení zpráv pomocí vzájemných certifikátů</span><span class="sxs-lookup"><span data-stu-id="15350-132">Message Security with Mutual Certificates</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 <span data-ttu-id="15350-133">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="15350-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="15350-134">Certifikát serveru je distribuován s aplikací a je dostupný mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="15350-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="15350-135">Zabezpečení zpráv pomocí vystavených tokenů</span><span class="sxs-lookup"><span data-stu-id="15350-135">Message Security with Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 <span data-ttu-id="15350-136">Federované zabezpečení, které umožňuje vytvoření vztahu důvěryhodnosti mezi nezávislými doménami.</span><span class="sxs-lookup"><span data-stu-id="15350-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="15350-137">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="15350-137">Trusted Subsystem</span></span>](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 <span data-ttu-id="15350-138">Klient přistupuje k jedné nebo více webovým službám, které jsou distribuovány přes síť.</span><span class="sxs-lookup"><span data-stu-id="15350-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="15350-139">Webové služby mají přístup k dalším prostředkům (jako jsou databáze nebo jiné webové služby), které musí být zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="15350-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15350-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="15350-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="15350-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="15350-141">Related Sections</span></span>  
 [<span data-ttu-id="15350-142">Autorizace</span><span class="sxs-lookup"><span data-stu-id="15350-142">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="15350-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="15350-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [<span data-ttu-id="15350-144">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="15350-144">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="15350-145">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="15350-145">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="15350-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="15350-146">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [<span data-ttu-id="15350-147">Ověřování</span><span class="sxs-lookup"><span data-stu-id="15350-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="15350-148">Autorizace</span><span class="sxs-lookup"><span data-stu-id="15350-148">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="15350-149">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="15350-149">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="15350-150">Auditování</span><span class="sxs-lookup"><span data-stu-id="15350-150">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="15350-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15350-151">See also</span></span>

- [<span data-ttu-id="15350-152">Informace o zabezpečení a osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="15350-152">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- <span data-ttu-id="15350-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="15350-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
