---
title: Falšování
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107884"
---
# <a name="tampering"></a><span data-ttu-id="bdd89-102">Falšování</span><span class="sxs-lookup"><span data-stu-id="bdd89-102">Tampering</span></span>
<span data-ttu-id="bdd89-103">*Manipulace* je změna zprávu nebo doručení zprávy a pomocí upravený zprávy pro účely, než jaké byla určená.</span><span class="sxs-lookup"><span data-stu-id="bdd89-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="bdd89-104">Nezakazujte WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="bdd89-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="bdd89-105">Specifikace WS-Addressing obsahuje záhlaví adres v každé zprávě, povolení příjemce zprávy ověření odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="bdd89-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="bdd89-106">Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="bdd89-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="bdd89-107">Pokud režim zabezpečení je nastavený na zprávu a WS-Addressing je zakázaná, útočník by mohl přijmout žádost od klienta a odeslat do jiné služby, a druhý služby nemá možnost nijak zjistit, že zpráva pochází z původního klienta.</span><span class="sxs-lookup"><span data-stu-id="bdd89-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="bdd89-108">V důsledku toho první služby můžete předstírat, že, že je klient upozorňovat druhý služby.</span><span class="sxs-lookup"><span data-stu-id="bdd89-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="bdd89-109">Chcete-li tento problém zmírnit, nikdy nastavte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>a vyhnout se použití <xref:System.ServiceModel.Channels.MessageVersion>, jako je například statické <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastavuje <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="bdd89-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd89-110">See also</span></span>

- [<span data-ttu-id="bdd89-111">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bdd89-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="bdd89-112">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="bdd89-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="bdd89-113">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="bdd89-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="bdd89-114">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="bdd89-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="bdd89-115">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="bdd89-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [<span data-ttu-id="bdd89-116">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="bdd89-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
