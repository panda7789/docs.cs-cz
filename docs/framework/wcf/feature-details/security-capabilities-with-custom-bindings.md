---
title: "Možnosti zabezpečení u vlastních vazeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="138c9-102">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="138c9-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="138c9-103">Běžné úkoly, zabezpečení můžete provést pomocí jedné z vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="138c9-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="138c9-104">Pokud potřebujete větší kontrolu, ale můžete vytvořit vlastní vazby s <xref:System.ServiceModel.Channels.SecurityBindingElement>, jak je popsáno v těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="138c9-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="138c9-105">vlastní vazby, najdete v části [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="138c9-105"> custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="138c9-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="138c9-106">In This Section</span></span>  
 [<span data-ttu-id="138c9-107">Režimy ověřování SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="138c9-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="138c9-108">Popisuje režimy ověřování, které lze prostřednictvím vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="138c9-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="138c9-109">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="138c9-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="138c9-110">Popisuje základní kroky pro vytvoření vlastní vazby s elementem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="138c9-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="138c9-111">Postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="138c9-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="138c9-112">Popisuje, jak vytvořit element zabezpečení pro zadaný režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="138c9-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="138c9-113">Postupy: zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="138c9-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="138c9-114">Popisuje postup zakázání zabezpečených relací při vytváření služby federation service.</span><span class="sxs-lookup"><span data-stu-id="138c9-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="138c9-115">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="138c9-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="138c9-116">Popisuje, jak určit, kdy dojde k útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="138c9-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="138c9-117">Postupy: vytvoření přihlašovacích údajů podpora</span><span class="sxs-lookup"><span data-stu-id="138c9-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="138c9-118">Popisuje, jak zadat podpůrné pověření pro služby, pokud služba vyžaduje, aby ho.</span><span class="sxs-lookup"><span data-stu-id="138c9-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="138c9-119">Postupy: nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="138c9-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="138c9-120">Popisuje postup při digitálnímu podepisování zpráv potvrďte podpisy.</span><span class="sxs-lookup"><span data-stu-id="138c9-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="138c9-121">Postupy: Sada zkosení max. frekvence</span><span class="sxs-lookup"><span data-stu-id="138c9-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="138c9-122">Popisuje, jak nastavit maximální povolený časový rozdíl mezi službou a klienta.</span><span class="sxs-lookup"><span data-stu-id="138c9-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="138c9-123">Postupy: Zakázání šifrování digitálních podpisů</span><span class="sxs-lookup"><span data-stu-id="138c9-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="138c9-124">Popisuje, jak zakázáním šifrování digitálních podpisů může mít výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="138c9-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="138c9-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="138c9-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="138c9-126">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="138c9-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="138c9-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="138c9-127">Related Sections</span></span>  
 [<span data-ttu-id="138c9-128">Princip úrovně ochrany</span><span class="sxs-lookup"><span data-stu-id="138c9-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="138c9-129">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="138c9-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="138c9-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="138c9-130">See Also</span></span>  
 [<span data-ttu-id="138c9-131">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="138c9-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="138c9-132">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="138c9-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="138c9-133">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="138c9-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
