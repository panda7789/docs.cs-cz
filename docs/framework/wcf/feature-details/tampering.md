---
title: Falšování
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600708"
---
# <a name="tampering"></a><span data-ttu-id="18b40-102">Falšování</span><span class="sxs-lookup"><span data-stu-id="18b40-102">Tampering</span></span>
<span data-ttu-id="18b40-103">*Manipulace* je způsob změny zprávy nebo doručení zprávy a použití změněné zprávy pro jiný účel, než k čemu bylo určeno.</span><span class="sxs-lookup"><span data-stu-id="18b40-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="18b40-104">Nepovolujte WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="18b40-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="18b40-105">Specifikace WS-Addressing poskytuje záhlaví adres pro každou zprávu a umožňuje příjemci zprávy ověřit odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="18b40-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="18b40-106">Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnosti na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="18b40-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="18b40-107">Pokud je režim zabezpečení nastavený na stav zpráva a služba WS-Addressing je zakázaná, může útočník přijmout požadavek od klienta a odeslat ho do jiné služby a druhá služba nijak nedokázala zjistit, jestli zpráva pochází z původního klienta.</span><span class="sxs-lookup"><span data-stu-id="18b40-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="18b40-108">V důsledku toho může první služba předstírat, že se jedná o klienta při komunikaci s druhou službou.</span><span class="sxs-lookup"><span data-stu-id="18b40-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="18b40-109">Chcete-li tuto skutečnost zmírnit, nenastavte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost na hodnotu <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> a vyhněte se použití <xref:System.ServiceModel.Channels.MessageVersion> , jako je například statická <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastaví <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost na hodnotu <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="18b40-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b40-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="18b40-110">See also</span></span>

- [<span data-ttu-id="18b40-111">Otázky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="18b40-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="18b40-112">Zpřístupnění informací</span><span class="sxs-lookup"><span data-stu-id="18b40-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="18b40-113">Zvýšení oprávnění</span><span class="sxs-lookup"><span data-stu-id="18b40-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="18b40-114">Útok DoS</span><span class="sxs-lookup"><span data-stu-id="18b40-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="18b40-115">Nepodporované scénáře</span><span class="sxs-lookup"><span data-stu-id="18b40-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="18b40-116">Útoky opakováním</span><span class="sxs-lookup"><span data-stu-id="18b40-116">Replay Attacks</span></span>](replay-attacks.md)
