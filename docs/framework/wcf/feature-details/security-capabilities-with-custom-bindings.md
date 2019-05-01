---
title: Možnosti zabezpečení u vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990922"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="2c40f-102">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="2c40f-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="2c40f-103">Umožňuje zvládnout běžné úkoly zabezpečení pomocí jedné z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="2c40f-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="2c40f-104">Pokud potřebujete větší kontrolu, ale můžete vytvořit vlastní vazby s <xref:System.ServiceModel.Channels.SecurityBindingElement>, jak je popsáno v těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="2c40f-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="2c40f-105">Další informace o vlastních vazeb naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="2c40f-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c40f-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2c40f-106">In This Section</span></span>  
 [<span data-ttu-id="2c40f-107">Režimy ověřování SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2c40f-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="2c40f-108">Popisuje režimy ověřování, které lze prostřednictvím vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2c40f-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="2c40f-109">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2c40f-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="2c40f-110">Popisuje základní kroky pro vytvoření vlastní vazby pomocí elementu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2c40f-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="2c40f-111">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="2c40f-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="2c40f-112">Popisuje, jak vytvořit prvek zabezpečení pro zadaný režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="2c40f-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="2c40f-113">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2c40f-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="2c40f-114">Popisuje postup zakázání zabezpečených relací při vytváření služby federation service.</span><span class="sxs-lookup"><span data-stu-id="2c40f-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="2c40f-115">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="2c40f-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="2c40f-116">Popisuje, jak zjistit, když dojde k opakování útoku.</span><span class="sxs-lookup"><span data-stu-id="2c40f-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="2c40f-117">Postupy: Vytvoření podpůrného pověření</span><span class="sxs-lookup"><span data-stu-id="2c40f-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="2c40f-118">Popisuje, jak zadat podpůrných přihlašovacích údajů ke službě, pokud služba vyžaduje, aby ho.</span><span class="sxs-lookup"><span data-stu-id="2c40f-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="2c40f-119">Postupy: Nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="2c40f-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="2c40f-120">Popisuje postup při digitální podpis zprávy potvrzení podpisů.</span><span class="sxs-lookup"><span data-stu-id="2c40f-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="2c40f-121">Postupy: Sada Maxclockskew</span><span class="sxs-lookup"><span data-stu-id="2c40f-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="2c40f-122">Popisuje, jak nastavit maximální povolený časový rozdíl mezi službou a klienta.</span><span class="sxs-lookup"><span data-stu-id="2c40f-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="2c40f-123">Postupy: Zákaz šifrování digitálních podpisů</span><span class="sxs-lookup"><span data-stu-id="2c40f-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="2c40f-124">Popisuje, jak zákaz šifrování digitálních podpisů může mít zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2c40f-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2c40f-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2c40f-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="2c40f-126">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2c40f-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="2c40f-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2c40f-127">Related Sections</span></span>  
 [<span data-ttu-id="2c40f-128">Princip úrovně ochrany</span><span class="sxs-lookup"><span data-stu-id="2c40f-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="2c40f-129">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2c40f-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c40f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c40f-130">See also</span></span>

- [<span data-ttu-id="2c40f-131">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2c40f-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="2c40f-132">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2c40f-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="2c40f-133">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="2c40f-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
