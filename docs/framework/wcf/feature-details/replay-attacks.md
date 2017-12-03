---
title: "Útoky opakováním"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd96404adea7fb8e7d59dcea322b2d3832f2bfe4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="replay-attacks"></a><span data-ttu-id="fcf89-102">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="fcf89-102">Replay Attacks</span></span>
<span data-ttu-id="fcf89-103">A *přehráním útoku* nastane, když útočník zkopíruje datového proudu zpráv mezi dvěma účastníky a replays datový proud na jeden nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="fcf89-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="fcf89-104">Pokud omezeny, počítače podřízené útoku zpracovat datového proudu jako legitimní zprávy, což vede k řadu chybný důsledky, jako je například redundantní objednávky položky.</span><span class="sxs-lookup"><span data-stu-id="fcf89-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="fcf89-105">Vazby může být vystavené útokům s reflexe</span><span class="sxs-lookup"><span data-stu-id="fcf89-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="fcf89-106">*Reflexe útoky* jsou opětovná přehrání zprávy zpět do odesílatele, jako kdyby jejich pochází přijímač jako odpověď.</span><span class="sxs-lookup"><span data-stu-id="fcf89-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="fcf89-107">Standardní *zjišťování opakování* v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanismus nezpracovává automaticky to.</span><span class="sxs-lookup"><span data-stu-id="fcf89-107">The standard *replay detection* in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="fcf89-108">Reflexe útoky jsou omezeny ve výchozím nastavení, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model služby přidá ID podepsanou zprávu do zprávy žádosti a očekává přihlášeni `relates-to` hlavičky v odpovědi na zprávy.</span><span class="sxs-lookup"><span data-stu-id="fcf89-108">Reflection attacks are mitigated by default because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="fcf89-109">Zpráva žádosti v důsledku toho nelze přehrány jako odpověď.</span><span class="sxs-lookup"><span data-stu-id="fcf89-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="fcf89-110">Ve scénářích zabezpečenou zprávu spolehlivé (RM) jsou omezeny reflexe útoky protože:</span><span class="sxs-lookup"><span data-stu-id="fcf89-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
-   <span data-ttu-id="fcf89-111">Vytvoření pořadí a vytvořit pořadí odpovědi zpráva schémat se liší.</span><span class="sxs-lookup"><span data-stu-id="fcf89-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
-   <span data-ttu-id="fcf89-112">Protože klient nemůže porozumět takové zprávy, nelze pro nezpracovávají pořadí přehrány pořadí zprávy, které klient odesílá zpět do.</span><span class="sxs-lookup"><span data-stu-id="fcf89-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
-   <span data-ttu-id="fcf89-113">Duplexní pořadí dvě pořadí ID musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="fcf89-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="fcf89-114">Odchozí zprávy pořadí nelze proto přehrány zpět jako příchozí zprávy pořadí (všechna pořadí záhlaví a texty jsou podepsané, příliš).</span><span class="sxs-lookup"><span data-stu-id="fcf89-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="fcf89-115">Jenom vazby, které jsou náchylné k útokům reflexe jsou bez WS-Addressing: vlastní vazby, které mají WS adresování zakázat a použít symetrický zabezpečení na základě klíčů.</span><span class="sxs-lookup"><span data-stu-id="fcf89-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="fcf89-116"><xref:System.ServiceModel.BasicHttpBinding> Nepoužívá WS-Addressing ve výchozím nastavení, ale nepoužívá symetrický zabezpečení na základě klíčů způsobem, který mohou být zranitelné v důsledku tento útok.</span><span class="sxs-lookup"><span data-stu-id="fcf89-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="fcf89-117">Je toto řešení pro vlastní vazby není vytvoření kontextu zabezpečení nebo tak, aby vyžadovala WS-Addressing hlavičky.</span><span class="sxs-lookup"><span data-stu-id="fcf89-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="fcf89-118">Webové farmy: Útočník opětovná přehrání požadavek na víc uzlů</span><span class="sxs-lookup"><span data-stu-id="fcf89-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="fcf89-119">Klient používá službu, která se implementuje na webové farmy.</span><span class="sxs-lookup"><span data-stu-id="fcf89-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="fcf89-120">Útočník replays žádost byla odeslána do jednoho uzlu ve farmě do jiného uzlu ve farmě.</span><span class="sxs-lookup"><span data-stu-id="fcf89-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="fcf89-121">Kromě toho pokud restartování služby mezipaměti opětovného přehrání vyprazdňuje, což útočníkovi o přehrání žádosti.</span><span class="sxs-lookup"><span data-stu-id="fcf89-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="fcf89-122">(Mezipaměť obsahuje podpis hodnoty používané, dříve zobrazenou zpráv a zabraňuje přehrání, takže tyto podpisy lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="fcf89-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="fcf89-123">Přehrání mezipaměti nejsou sdílená mezi webové farmy.)</span><span class="sxs-lookup"><span data-stu-id="fcf89-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="fcf89-124">Způsoby zmírnění patří:</span><span class="sxs-lookup"><span data-stu-id="fcf89-124">Mitigations include:</span></span>  
  
-   <span data-ttu-id="fcf89-125">Režim zabezpečení zpráv pomocí tokenů kontextu stavová zabezpečení (s nebo bez zabezpečené konverzaci povoleno).</span><span class="sxs-lookup"><span data-stu-id="fcf89-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="fcf89-126">[Postupy: Vytvoření kontextu zabezpečení tokenu pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="fcf89-126"> [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
-   <span data-ttu-id="fcf89-127">Nakonfigurujte službu, která používá zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="fcf89-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf89-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcf89-128">See Also</span></span>  
 [<span data-ttu-id="fcf89-129">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fcf89-129">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="fcf89-130">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="fcf89-130">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="fcf89-131">Zvýšení úrovně oprávnění</span><span class="sxs-lookup"><span data-stu-id="fcf89-131">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="fcf89-132">Odmítnutí služby</span><span class="sxs-lookup"><span data-stu-id="fcf89-132">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="fcf89-133">Manipulaci</span><span class="sxs-lookup"><span data-stu-id="fcf89-133">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [<span data-ttu-id="fcf89-134">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="fcf89-134">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
