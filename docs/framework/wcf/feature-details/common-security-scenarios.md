---
title: Běžné scénáře zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: f36ebdb5ea248ec8134c688f89eb5d0be38dfe38
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579733"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="0b38b-102">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b38b-102">Common Security Scenarios</span></span>
<span data-ttu-id="0b38b-103">Témata v tomto oddílu katalogují několik možných konfigurací zabezpečení klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="0b38b-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="0b38b-104">Konfigurace se liší v závislosti na mnoha faktorech.</span><span class="sxs-lookup"><span data-stu-id="0b38b-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="0b38b-105">Například zda je služba nebo klient v intranetu nebo zda je zabezpečení poskytované systémem Windows nebo přenos (například HTTPS).</span><span class="sxs-lookup"><span data-stu-id="0b38b-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b38b-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0b38b-106">In This Section</span></span>  
 [<span data-ttu-id="0b38b-107">Nezabezpečený internetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="0b38b-107">Internet Unsecured Client and Service</span></span>](internet-unsecured-client-and-service.md)  
 <span data-ttu-id="0b38b-108">Příklad veřejného nezabezpečeného klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="0b38b-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="0b38b-109">Nezabezpečený intranetový klient a služba</span><span class="sxs-lookup"><span data-stu-id="0b38b-109">Intranet Unsecured Client and Service</span></span>](intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="0b38b-110">Služba WCF (Basic Windows Communication Foundation) vyvinutá tak, aby poskytovala informace o zabezpečené privátní síti pro aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="0b38b-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="0b38b-111">Zabezpečení přenosu pomocí základního ověřování</span><span class="sxs-lookup"><span data-stu-id="0b38b-111">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)  
 <span data-ttu-id="0b38b-112">Aplikace umožňuje klientům přihlašovat se pomocí vlastního ověřování.</span><span class="sxs-lookup"><span data-stu-id="0b38b-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="0b38b-113">Zabezpečení přenosu pomocí ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="0b38b-113">Transport Security with Windows Authentication</span></span>](transport-security-with-windows-authentication.md)  
 <span data-ttu-id="0b38b-114">Zobrazuje klienta a službu zabezpečený zabezpečením systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0b38b-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="0b38b-115">Zabezpečení přenosu s anonymním klientem</span><span class="sxs-lookup"><span data-stu-id="0b38b-115">Transport Security with an Anonymous Client</span></span>](transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="0b38b-116">Tento scénář používá zabezpečení přenosu (například HTTPS) k zajištění důvěrnosti a integrity.</span><span class="sxs-lookup"><span data-stu-id="0b38b-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="0b38b-117">Zabezpečení přenosu pomocí ověření certifikátem</span><span class="sxs-lookup"><span data-stu-id="0b38b-117">Transport Security with Certificate Authentication</span></span>](transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="0b38b-118">Zobrazuje klienta a službu zabezpečený certifikátem.</span><span class="sxs-lookup"><span data-stu-id="0b38b-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="0b38b-119">Zabezpečení zpráv pomocí anonymního klienta</span><span class="sxs-lookup"><span data-stu-id="0b38b-119">Message Security with an Anonymous Client</span></span>](message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="0b38b-120">Zobrazuje klienta a službu zabezpečený zabezpečením zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="0b38b-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="0b38b-121">Zabezpečení zpráv pomocí klienta uživatelského jména</span><span class="sxs-lookup"><span data-stu-id="0b38b-121">Message Security with a User Name Client</span></span>](message-security-with-a-user-name-client.md)  
 <span data-ttu-id="0b38b-122">Klient je model Windows Forms aplikace, která klientům umožňuje přihlásit se pomocí uživatelského jména a hesla domény.</span><span class="sxs-lookup"><span data-stu-id="0b38b-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="0b38b-123">Zabezpečení zpráv pomocí klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="0b38b-123">Message Security with a Certificate Client</span></span>](message-security-with-a-certificate-client.md)  
 <span data-ttu-id="0b38b-124">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="0b38b-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0b38b-125">Kontext zabezpečení je vytvořen pomocí vyjednávání protokolu TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="0b38b-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="0b38b-126">Zabezpečení zprávy pomocí klienta Windows</span><span class="sxs-lookup"><span data-stu-id="0b38b-126">Message Security with a Windows Client</span></span>](message-security-with-a-windows-client.md)  
 <span data-ttu-id="0b38b-127">Variace klienta certifikátu.</span><span class="sxs-lookup"><span data-stu-id="0b38b-127">A variation of the certificate client.</span></span> <span data-ttu-id="0b38b-128">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="0b38b-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0b38b-129">Kontext zabezpečení je vytvořen prostřednictvím vyjednávání TLS.</span><span class="sxs-lookup"><span data-stu-id="0b38b-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="0b38b-130">Zabezpečení zpráv pomocí klienta Windows bez vyjednávání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="0b38b-130">Message Security with a Windows Client without Credential Negotiation</span></span>](message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="0b38b-131">Zobrazuje klienta a službu zabezpečenou doménou protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="0b38b-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="0b38b-132">Zabezpečení zpráv pomocí vzájemných certifikátů</span><span class="sxs-lookup"><span data-stu-id="0b38b-132">Message Security with Mutual Certificates</span></span>](message-security-with-mutual-certificates.md)  
 <span data-ttu-id="0b38b-133">Servery mají certifikáty a každý z klientů má certifikát.</span><span class="sxs-lookup"><span data-stu-id="0b38b-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="0b38b-134">Certifikát serveru je distribuován s aplikací a je dostupný mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="0b38b-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="0b38b-135">Zabezpečení zpráv pomocí vystavených tokenů</span><span class="sxs-lookup"><span data-stu-id="0b38b-135">Message Security with Issued Tokens</span></span>](message-security-with-issued-tokens.md)  
 <span data-ttu-id="0b38b-136">Federované zabezpečení, které umožňuje vytvoření vztahu důvěryhodnosti mezi nezávislými doménami.</span><span class="sxs-lookup"><span data-stu-id="0b38b-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="0b38b-137">Důvěryhodný subsystém</span><span class="sxs-lookup"><span data-stu-id="0b38b-137">Trusted Subsystem</span></span>](trusted-subsystem.md)  
 <span data-ttu-id="0b38b-138">Klient přistupuje k jedné nebo více webovým službám, které jsou distribuovány přes síť.</span><span class="sxs-lookup"><span data-stu-id="0b38b-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="0b38b-139">Webové služby mají přístup k dalším prostředkům (jako jsou databáze nebo jiné webové služby), které musí být zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="0b38b-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0b38b-140">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="0b38b-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="0b38b-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0b38b-141">Related Sections</span></span>  
 [<span data-ttu-id="0b38b-142">Autorizace</span><span class="sxs-lookup"><span data-stu-id="0b38b-142">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="0b38b-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b38b-143">Security Overview</span></span>](security-overview.md)  
  
 [<span data-ttu-id="0b38b-144">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b38b-144">Security</span></span>](security.md)  
  
 [<span data-ttu-id="0b38b-145">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b38b-145">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="0b38b-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0b38b-146">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
 [<span data-ttu-id="0b38b-147">Authentication</span><span class="sxs-lookup"><span data-stu-id="0b38b-147">Authentication</span></span>](authentication-in-wcf.md)  
  
 [<span data-ttu-id="0b38b-148">Autorizace</span><span class="sxs-lookup"><span data-stu-id="0b38b-148">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="0b38b-149">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0b38b-149">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="0b38b-150">Auditování</span><span class="sxs-lookup"><span data-stu-id="0b38b-150">Auditing</span></span>](auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b38b-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b38b-151">See also</span></span>

- [<span data-ttu-id="0b38b-152">Informace o zabezpečení a doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="0b38b-152">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)
- <span data-ttu-id="0b38b-153">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0b38b-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
