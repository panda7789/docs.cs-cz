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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 541770db6b9cc624fd08ab4db275bc63fa5deca9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="eef17-102">Rozšiřitelnost kanálů</span><span class="sxs-lookup"><span data-stu-id="eef17-102">Channels Extensibility</span></span>
<span data-ttu-id="eef17-103">Tato část obsahuje příklady vysvětlující vlastní kanály.</span><span class="sxs-lookup"><span data-stu-id="eef17-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eef17-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eef17-104">In This Section</span></span>  
 [<span data-ttu-id="eef17-105">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="eef17-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="eef17-106">Demonstruje místní kanál, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosu kanálu, který se používá pro komunikaci v rámci stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="eef17-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="eef17-107">Spolehlivý zabezpečený profil</span><span class="sxs-lookup"><span data-stu-id="eef17-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="eef17-108">Ukazuje, jak vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a spolehlivé zabezpečení profilu (konfigurace).</span><span class="sxs-lookup"><span data-stu-id="eef17-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="eef17-109">Dispečer vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="eef17-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="eef17-110">Ukazuje, jak vytvořit kanál zásobníku vlastní způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a jak vytvořit vlastní kanál dispečera v prostředí hostitele webu.</span><span class="sxs-lookup"><span data-stu-id="eef17-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="eef17-111">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="eef17-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="eef17-112">Ukazuje, jak omezit množství paměti k přechodnému ukládání velkých zprávy odeslané pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eef17-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="eef17-113">Kanál potvrzení HTTP</span><span class="sxs-lookup"><span data-stu-id="eef17-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="eef17-114">Demonstruje vrstveného kanál, který změní jednosměrný vzorcem zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="eef17-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="eef17-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="eef17-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="eef17-116">Demonstruje postup vytvoření vlastního protokolu kanál používat soubory cookie HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="eef17-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="eef17-117">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="eef17-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="eef17-118">Ukazuje, jak implementovat vlastní vazby element, který vytváří objekty factory kanálu a naslouchací procesy kanál zachytávat všechny příchozí a odchozí zprávy na určitém místě v zásobníku spuštění.</span><span class="sxs-lookup"><span data-stu-id="eef17-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
