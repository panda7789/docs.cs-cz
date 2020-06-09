---
title: Možnosti zabezpečení u vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595190"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="0b47d-102">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="0b47d-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="0b47d-103">Většinu běžných úloh zabezpečení můžete provádět pomocí jedné z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="0b47d-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="0b47d-104">Pokud však potřebujete větší kontrolu, můžete vytvořit vlastní vazbu s a <xref:System.ServiceModel.Channels.SecurityBindingElement> , jak je vysvětleno v těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="0b47d-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="0b47d-105">Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0b47d-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b47d-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0b47d-106">In This Section</span></span>  
 [<span data-ttu-id="0b47d-107">Režimy ověřování SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0b47d-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="0b47d-108">Popisuje režimy ověřování, které lze použít s vlastní vazbou.</span><span class="sxs-lookup"><span data-stu-id="0b47d-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="0b47d-109">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0b47d-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="0b47d-110">Popisuje základní kroky pro vytvoření vlastní vazby s prvkem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0b47d-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="0b47d-111">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="0b47d-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="0b47d-112">Popisuje, jak vytvořit prvek zabezpečení pro zadaný režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="0b47d-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="0b47d-113">Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0b47d-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="0b47d-114">Popisuje, jak zakázat zabezpečené relace při vytváření federační služby.</span><span class="sxs-lookup"><span data-stu-id="0b47d-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="0b47d-115">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="0b47d-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="0b47d-116">Popisuje, jak určit, kdy dojde k útoku na opakování.</span><span class="sxs-lookup"><span data-stu-id="0b47d-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="0b47d-117">Postupy: Vytvoření podpůrných přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="0b47d-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="0b47d-118">V této části najdete popis postupu poskytnutí podpůrného pověření ke službě, pokud je služba vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="0b47d-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="0b47d-119">Postupy: Nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="0b47d-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="0b47d-120">Popisuje kroky pro potvrzení podpisů při digitálním podepisování zprávy.</span><span class="sxs-lookup"><span data-stu-id="0b47d-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="0b47d-121">Postupy: Nastavení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="0b47d-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="0b47d-122">V této části najdete popis postupu nastavení maximálního povoleného časového rozdílu mezi službou a klientem.</span><span class="sxs-lookup"><span data-stu-id="0b47d-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="0b47d-123">Postupy: Zákaz šifrování digitálních podpisů</span><span class="sxs-lookup"><span data-stu-id="0b47d-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="0b47d-124">Popisuje, jak zakázat šifrování digitálních podpisů může mít výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="0b47d-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0b47d-125">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="0b47d-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="0b47d-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0b47d-126">Related Sections</span></span>  
 [<span data-ttu-id="0b47d-127">Princip úrovně ochrany</span><span class="sxs-lookup"><span data-stu-id="0b47d-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="0b47d-128">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0b47d-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b47d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b47d-129">See also</span></span>

- [<span data-ttu-id="0b47d-130">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b47d-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="0b47d-131">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0b47d-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="0b47d-132">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="0b47d-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
