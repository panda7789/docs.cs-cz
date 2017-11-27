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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8852c4d19c48af2beee598f4ddfae7b775a025f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tampering"></a><span data-ttu-id="1a7e0-102">Falšování</span><span class="sxs-lookup"><span data-stu-id="1a7e0-102">Tampering</span></span>
<span data-ttu-id="1a7e0-103">*Manipulaci* je operace změna zpráva nebo doručení zpráv a pomocí změněna zprávy pro účel, než jaké byla určená.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="1a7e0-104">Nezakazujte adresování WS</span><span class="sxs-lookup"><span data-stu-id="1a7e0-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="1a7e0-105">Specifikace WS-Addressing poskytuje hlavičky adresy na každou zprávu, povolení příjemce zprávy ověření odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="1a7e0-106">Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="1a7e0-107">Režim zabezpečení je nastavena na zprávu, a adresování WS je zakázáno, útočník může trvat žádost od klienta a odeslat ho do jiné služby, a druhá služby nemá možnost nijak detekci, zda zpráva byla přijata z původního klienta.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="1a7e0-108">Ve skutečnosti první služby můžete předstírají, že ho je klient při posuzování druhý službě.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="1a7e0-109">Toto riziko lze snížit nikdy nastavit <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>a vyhnout se použití <xref:System.ServiceModel.Channels.MessageVersion>, například statické <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastavuje <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a7e0-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a7e0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a7e0-110">See Also</span></span>  
 [<span data-ttu-id="1a7e0-111">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1a7e0-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="1a7e0-112">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="1a7e0-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="1a7e0-113">Zvýšení úrovně oprávnění</span><span class="sxs-lookup"><span data-stu-id="1a7e0-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="1a7e0-114">Odmítnutí služby</span><span class="sxs-lookup"><span data-stu-id="1a7e0-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="1a7e0-115">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="1a7e0-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="1a7e0-116">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="1a7e0-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
