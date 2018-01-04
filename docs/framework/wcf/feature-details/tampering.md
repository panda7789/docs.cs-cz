---
title: "Falšování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ee041de1a9e009ca68ecc8bba8bc2fa06ba6ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tampering"></a><span data-ttu-id="29e9d-102">Falšování</span><span class="sxs-lookup"><span data-stu-id="29e9d-102">Tampering</span></span>
<span data-ttu-id="29e9d-103">*Manipulaci* je operace změna zpráva nebo doručení zpráv a pomocí změněna zprávy pro účel, než jaké byla určená.</span><span class="sxs-lookup"><span data-stu-id="29e9d-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="29e9d-104">Nezakazujte adresování WS</span><span class="sxs-lookup"><span data-stu-id="29e9d-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="29e9d-105">Specifikace WS-Addressing poskytuje hlavičky adresy na každou zprávu, povolení příjemce zprávy ověření odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="29e9d-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="29e9d-106">Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="29e9d-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="29e9d-107">Režim zabezpečení je nastavena na zprávu, a adresování WS je zakázáno, útočník může trvat žádost od klienta a odeslat ho do jiné služby, a druhá služby nemá možnost nijak detekci, zda zpráva byla přijata z původního klienta.</span><span class="sxs-lookup"><span data-stu-id="29e9d-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="29e9d-108">Ve skutečnosti první služby můžete předstírají, že ho je klient při posuzování druhý službě.</span><span class="sxs-lookup"><span data-stu-id="29e9d-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="29e9d-109">Toto riziko lze snížit nikdy nastavit <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>a vyhnout se použití <xref:System.ServiceModel.Channels.MessageVersion>, například statické <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastavuje <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="29e9d-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e9d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="29e9d-110">See Also</span></span>  
 [<span data-ttu-id="29e9d-111">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="29e9d-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="29e9d-112">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="29e9d-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="29e9d-113">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="29e9d-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="29e9d-114">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="29e9d-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="29e9d-115">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="29e9d-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="29e9d-116">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="29e9d-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
