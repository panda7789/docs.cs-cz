---
title: "Operace s pojmenovanými kanály v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68c1ad34952ee4d20dbf56aa8ca437a3f99db751
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="47080-102">Operace s pojmenovanými kanály v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47080-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="47080-103">Kanály poskytují prostředek pro komunikaci mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="47080-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="47080-104">Existují dva typy kanály:</span><span class="sxs-lookup"><span data-stu-id="47080-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="47080-105">Anonymní kanály.</span><span class="sxs-lookup"><span data-stu-id="47080-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="47080-106">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="47080-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="47080-107">Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="47080-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="47080-108">Anonymní kanály jsou jednosměrná a nelze je použít přes síť.</span><span class="sxs-lookup"><span data-stu-id="47080-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="47080-109">Podporují pouze jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="47080-109">They support only a single server instance.</span></span> <span data-ttu-id="47080-110">Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy kde obslužné rutiny lze snadno předat podřízeného procesu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="47080-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="47080-111">V rozhraní .NET Framework, můžete implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="47080-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="47080-112">V tématu [postupy: místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="47080-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="47080-113">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="47080-113">Named pipes.</span></span>  
  
     <span data-ttu-id="47080-114">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="47080-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="47080-115">Pojmenované kanály mohou být jednosměrné nebo duplexní.</span><span class="sxs-lookup"><span data-stu-id="47080-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="47080-116">Budou podporovat komunikaci na základě zpráv a povolit více klientů najednou připojit k procesu serveru pomocí kanálu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="47080-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="47080-117">Pojmenované kanály také podporují zosobnění, které umožňuje připojování procesy používat vlastní oprávnění na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="47080-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="47080-118">V rozhraní .NET Framework, můžete implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="47080-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="47080-119">V tématu [postupy: meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="47080-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47080-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="47080-120">See Also</span></span>  
 [<span data-ttu-id="47080-121">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="47080-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="47080-122">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="47080-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="47080-123">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="47080-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
