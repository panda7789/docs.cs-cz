---
title: Operace s pojmenovanými kanály v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 919d4606e4ba72f07ba382244f8508975beffec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741237"
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="f3708-102">Operace s pojmenovanými kanály v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f3708-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="f3708-103">Kanály poskytují způsob meziprocesová komunikace.</span><span class="sxs-lookup"><span data-stu-id="f3708-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="f3708-104">Existují dva druhy kanály:</span><span class="sxs-lookup"><span data-stu-id="f3708-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="f3708-105">Anonymní kanály.</span><span class="sxs-lookup"><span data-stu-id="f3708-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="f3708-106">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f3708-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="f3708-107">Anonymní kanály menší nákladovou režii než pojmenované kanály, ale nabízí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="f3708-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="f3708-108">Anonymní kanály jsou jednosměrná a nelze použít přes síť.</span><span class="sxs-lookup"><span data-stu-id="f3708-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="f3708-109">Podporují pouze jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="f3708-109">They support only a single server instance.</span></span> <span data-ttu-id="f3708-110">Anonymní kanály jsou užitečné pro komunikaci mezi vlákny, nebo mezi nadřazenými a podřízenými procesy, kde popisovače kanálu lze snadno předat podřízený proces při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f3708-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="f3708-111">V rozhraní .NET Framework, implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3708-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="f3708-112">Zobrazit [jak: Místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="f3708-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="f3708-113">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="f3708-113">Named pipes.</span></span>  
  
     <span data-ttu-id="f3708-114">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="f3708-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="f3708-115">Pojmenované kanály mohou být jednosměrné nebo obousměrné.</span><span class="sxs-lookup"><span data-stu-id="f3708-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="f3708-116">Tyto mohly podporovat komunikaci založenou na zprávách a povolit víc klientů současně připojit k procesu serveru pomocí kanálu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="f3708-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="f3708-117">Pojmenované kanály podporují také zosobnění, což umožňuje připojujícím se procesům použít vlastní oprávnění na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="f3708-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="f3708-118">V rozhraní .NET Framework, implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3708-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="f3708-119">Zobrazit [jak: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="f3708-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3708-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3708-120">See also</span></span>

- [<span data-ttu-id="f3708-121">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="f3708-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="f3708-122">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="f3708-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="f3708-123">Postupy: Použití pojmenované kanály meziprocesová síťová komunikace</span><span class="sxs-lookup"><span data-stu-id="f3708-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
