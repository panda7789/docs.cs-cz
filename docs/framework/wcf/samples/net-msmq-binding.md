---
title: Vazby Net MSMQ
ms.date: 03/30/2017
ms.assetid: fe4bb696-f57c-4cb3-9b7e-9d95fe6b8323
ms.openlocfilehash: ee32ea09eed28c1c7cd5df2df2d13fd5f41f4b22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972377"
---
# <a name="net-msmq-binding"></a><span data-ttu-id="1fc46-102">Vazby Net MSMQ</span><span class="sxs-lookup"><span data-stu-id="1fc46-102">Net MSMQ Binding</span></span>
<span data-ttu-id="1fc46-103">Tato část obsahuje ukázky, které demonstrují, pomocí atributů vazby služby MSMQ elementu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1fc46-103">This section contains samples that demonstrate using MSMQ binding attributes of an endpoint element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fc46-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1fc46-104">In This Section</span></span>  
 [<span data-ttu-id="1fc46-105">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="1fc46-105">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 <span data-ttu-id="1fc46-106">Ukazuje, jak k provedení transakčního komunikaci ve frontě pomocí služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="1fc46-106">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="1fc46-107">Nestálá komunikace ve frontě</span><span class="sxs-lookup"><span data-stu-id="1fc46-107">Volatile Queued Communication</span></span>](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 <span data-ttu-id="1fc46-108">Ukazuje, jak k provádění nestálá komunikace ve frontě za přenos řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="1fc46-108">Demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="1fc46-109">Fronty nedoručených zpráv</span><span class="sxs-lookup"><span data-stu-id="1fc46-109">Dead Letter Queues</span></span>](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 <span data-ttu-id="1fc46-110">Ukazuje, jak pro zpracování a zpracování zpráv, které selhaly doručování.</span><span class="sxs-lookup"><span data-stu-id="1fc46-110">Demonstrates how to handle and process messages that have failed delivery.</span></span>  
  
 [<span data-ttu-id="1fc46-111">Zacházení s nezpracovatelnými zprávami ve službě MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="1fc46-111">Poison Message Handling in MSMQ 4.0</span></span>](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md)  
 <span data-ttu-id="1fc46-112">Ukazuje, jak provádět zpracování ve službě MSMQ 4.0 pomocí nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="1fc46-112">Demonstrates how to perform poison message handling in a service using MSMQ 4.0.</span></span>  
  
 [<span data-ttu-id="1fc46-113">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="1fc46-113">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 <span data-ttu-id="1fc46-114">Ukazuje, jak odesílat a přijímat sadu související zprávy ve frontě komunikace prostřednictvím přenosu služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="1fc46-114">Demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="1fc46-115">Obousměrná komunikace</span><span class="sxs-lookup"><span data-stu-id="1fc46-115">Two-Way Communication</span></span>](../../../../docs/framework/wcf/samples/two-way-communication.md)  
 <span data-ttu-id="1fc46-116">Ukazuje, jak se provedly počet zrušených zpracovaných obousměrná komunikace ve frontě MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1fc46-116">Demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span>
  
 [<span data-ttu-id="1fc46-117">SRMP</span><span class="sxs-lookup"><span data-stu-id="1fc46-117">SRMP</span></span>](../../../../docs/framework/wcf/samples/srmp.md)  
 <span data-ttu-id="1fc46-118">Ukazuje, jak k provedení transakčního komunikaci ve frontě pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="1fc46-118">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 [<span data-ttu-id="1fc46-119">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="1fc46-119">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 <span data-ttu-id="1fc46-120">Ukazuje, jak implementovat aplikaci, která používá WS-Security x.509 v3 s ověřováním pomocí certifikátu klienta a vyžaduje ověření serveru pomocí služby MSMQ na server certifikát x.509 v3.</span><span class="sxs-lookup"><span data-stu-id="1fc46-120">Demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span>
