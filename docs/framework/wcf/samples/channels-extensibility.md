---
title: Rozšiřitelnost kanálů
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 9dbae26a548bdc8a8cfb05a3dd90db91475b55ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600630"
---
# <a name="channels-extensibility"></a><span data-ttu-id="d64b4-102">Rozšiřitelnost kanálů</span><span class="sxs-lookup"><span data-stu-id="d64b4-102">Channels Extensibility</span></span>
<span data-ttu-id="d64b4-103">Tato část obsahuje ukázky, které ukazují vlastní kanály.</span><span class="sxs-lookup"><span data-stu-id="d64b4-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d64b4-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d64b4-104">In This Section</span></span>  
 [<span data-ttu-id="d64b4-105">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="d64b4-105">Local Channel</span></span>](local-channel.md)  
 <span data-ttu-id="d64b4-106">Ukazuje místní kanál, kanál přenosu WCF, který se používá ke komunikaci ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d64b4-106">Demonstrates the local channel, a WCF transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="d64b4-107">Řešení ReliableSecureProfile</span><span class="sxs-lookup"><span data-stu-id="d64b4-107">Reliable Secure Profile</span></span>](reliable-secure-profile.md)  
 <span data-ttu-id="d64b4-108">Ukazuje, jak vytvořit WCF a spolehlivý zabezpečený profil (RSP).</span><span class="sxs-lookup"><span data-stu-id="d64b4-108">Demonstrates how to compose WCF and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="d64b4-109">Dispečer vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="d64b4-109">Custom Channel Dispatcher</span></span>](custom-channel-dispatcher.md)  
 <span data-ttu-id="d64b4-110">Ukazuje, jak vytvořit zásobník kanálů vlastním způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a vytvořením vlastního dispečera kanálu v prostředí webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="d64b4-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="d64b4-111">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="d64b4-111">Chunking Channel</span></span>](chunking-channel.md)  
 <span data-ttu-id="d64b4-112">Ukazuje, jak omezit velikost paměti, která se používá ke vyrovnávací paměti pro velké zprávy odeslané pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="d64b4-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using WCF.</span></span>
  
 [<span data-ttu-id="d64b4-113">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="d64b4-113">HttpCookieSession</span></span>](httpcookiesession.md)  
 <span data-ttu-id="d64b4-114">Ukazuje, jak vytvořit vlastní kanál protokolu pro použití souborů cookie protokolu HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="d64b4-114">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="d64b4-115">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="d64b4-115">Custom Message Interceptor</span></span>](custom-message-interceptor.md)  
 <span data-ttu-id="d64b4-116">Ukazuje, jak implementovat vlastní prvek vazby, který vytváří továrny kanálů a naslouchací procesy kanálu pro zachycení všech příchozích a odchozích zpráv v určitém bodě v zásobníku běhu.</span><span class="sxs-lookup"><span data-stu-id="d64b4-116">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
