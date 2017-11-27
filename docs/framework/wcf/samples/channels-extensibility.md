---
title: "Rozšiřitelnost kanálů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e0cf92edc4ec05df3e5e8c25b90bcf253e94ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="c2fa6-102">Rozšiřitelnost kanálů</span><span class="sxs-lookup"><span data-stu-id="c2fa6-102">Channels Extensibility</span></span>
<span data-ttu-id="c2fa6-103">Tato část obsahuje příklady vysvětlující vlastní kanály.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2fa6-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c2fa6-104">In This Section</span></span>  
 [<span data-ttu-id="c2fa6-105">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="c2fa6-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="c2fa6-106">Demonstruje místní kanál, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosu kanálu, který se používá pro komunikaci v rámci stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="c2fa6-107">Řešení Reliablesecureprofile</span><span class="sxs-lookup"><span data-stu-id="c2fa6-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="c2fa6-108">Ukazuje, jak vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a spolehlivé zabezpečení profilu (konfigurace).</span><span class="sxs-lookup"><span data-stu-id="c2fa6-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="c2fa6-109">Dispečer vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="c2fa6-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="c2fa6-110">Ukazuje, jak vytvořit kanál zásobníku vlastní způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a jak vytvořit vlastní kanál dispečera v prostředí hostitele webu.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="c2fa6-111">Rozdělování kanálu</span><span class="sxs-lookup"><span data-stu-id="c2fa6-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="c2fa6-112">Ukazuje, jak omezit množství paměti k přechodnému ukládání velkých zprávy odeslané pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2fa6-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="c2fa6-113">Kanál potvrzení HTTP</span><span class="sxs-lookup"><span data-stu-id="c2fa6-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="c2fa6-114">Demonstruje vrstveného kanál, který změní jednosměrný vzorcem zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="c2fa6-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="c2fa6-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="c2fa6-116">Demonstruje postup vytvoření vlastního protokolu kanál používat soubory cookie HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="c2fa6-117">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="c2fa6-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="c2fa6-118">Ukazuje, jak implementovat vlastní vazby element, který vytváří objekty factory kanálu a naslouchací procesy kanál zachytávat všechny příchozí a odchozí zprávy na určitém místě v zásobníku spuštění.</span><span class="sxs-lookup"><span data-stu-id="c2fa6-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
