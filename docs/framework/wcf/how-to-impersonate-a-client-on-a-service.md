---
title: "Postupy: Zosobnění klienta ve službě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c868e2b31fa15d0f0c9228828beba03666d5591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="9963e-102">Postupy: Zosobnění klienta ve službě</span><span class="sxs-lookup"><span data-stu-id="9963e-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="9963e-103">Zosobnění klienta na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby povoluje službu k provádění akcí jménem klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-103">Impersonating a client on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="9963e-104">Pro akce v souladu přístup ovládacího prvku seznam (ACL) kontroly, jako je přístup k adresářů a souborů na počítači, nebo o přístup k databázi systému SQL Server že je kontrola seznamu ACL pro uživatelský účet klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="9963e-105">Toto téma ukazuje základní kroky potřebné k povolení klientovi v doméně systému Windows nastavení úrovně zosobnění klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="9963e-106">Pracovní příklad tohoto najdete v tématu [zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9963e-107">zosobnění klienta, najdete v části [delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-107"> client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9963e-108">Když klient a služba běží na stejném počítači a klient je spuštěn pod účtem systému (to znamená, `Local System` nebo `Network Service`), když zabezpečené relace se naváže stavová tokeny kontext zabezpečení nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="9963e-109">WinForms nebo konzolové aplikace obvykle běží pod aktuálně přihlášený účet tak, aby ve výchozím nastavení se můžou zosobnit účet.</span><span class="sxs-lookup"><span data-stu-id="9963e-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="9963e-110">Nicméně, pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a že stránky je hostován v [!INCLUDE[iis601](../../../includes/iis601-md.md)] nebo běh služby IIS 7.0, pak klient `Network Service` účet ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9963e-110">However, when the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and that page is hosted in [!INCLUDE[iis601](../../../includes/iis601-md.md)] or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="9963e-111">Všechny vazby poskytované systémem, které podporují zabezpečených relací ve výchozím nastavení používá token bezstavové kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9963e-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="9963e-112">Ale pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a zabezpečených relací s stavová tokeny kontext zabezpečení se používají, nelze jej zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-112">However, if the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9963e-113">pomocí stavová tokenů kontextu zabezpečení v zabezpečené relaci, najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-113"> using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="9963e-114">Chcete-li povolit zosobnění klienta z mezipaměti tokenu systému Windows ve službě</span><span class="sxs-lookup"><span data-stu-id="9963e-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1.  <span data-ttu-id="9963e-115">Vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="9963e-115">Create the service.</span></span> <span data-ttu-id="9963e-116">Podívejte se kurz tento základní postup, [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="9963e-117">Použít vazbu, která používá ověřování systému Windows a vytvoří relaci, jako například <xref:System.ServiceModel.NetTcpBinding> nebo <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="9963e-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="9963e-118">Při vytváření implementace rozhraní služby, použít <xref:System.ServiceModel.OperationBehaviorAttribute> třída metodu, která vyžaduje zosobnění klienta.</span><span class="sxs-lookup"><span data-stu-id="9963e-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="9963e-119">Nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.ImpersonationOption.Required>.</span><span class="sxs-lookup"><span data-stu-id="9963e-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="9963e-120">Nastavení úrovně povolené zosobnění na straně klienta</span><span class="sxs-lookup"><span data-stu-id="9963e-120">To set the allowed impersonation level on the client</span></span>  
  
1.  <span data-ttu-id="9963e-121">Vytvoření kódu klienta služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="9963e-122">[Přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-122"> [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="9963e-123">Po vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, nastavte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třída na jednu z <xref:System.Security.Principal.TokenImpersonationLevel> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="9963e-123">After creating the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9963e-124">Použít <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, Vyjednané ověřování protokolu Kerberos (někdy nazývané *více větev* nebo *vícekrokový* protokolu Kerberos) se musí použít.</span><span class="sxs-lookup"><span data-stu-id="9963e-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="9963e-125">Popis toho, jak tuto funkci implementovat, najdete v části [osvědčené postupy pro zabezpečení](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="9963e-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9963e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9963e-126">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [<span data-ttu-id="9963e-127">Zosobnění klienta</span><span class="sxs-lookup"><span data-stu-id="9963e-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [<span data-ttu-id="9963e-128">Delegace a zosobnění</span><span class="sxs-lookup"><span data-stu-id="9963e-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
