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
ms.openlocfilehash: 1e0d2747abbacf766ddeda6f41404d8701cbc273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574363"
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="98442-102">Operace s pojmenovanými kanály v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98442-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="98442-103">Kanály poskytují prostředek pro komunikaci mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="98442-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="98442-104">Existují dva typy kanály:</span><span class="sxs-lookup"><span data-stu-id="98442-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="98442-105">Anonymní kanály.</span><span class="sxs-lookup"><span data-stu-id="98442-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="98442-106">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="98442-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="98442-107">Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="98442-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="98442-108">Anonymní kanály jsou jednosměrná a nelze je použít přes síť.</span><span class="sxs-lookup"><span data-stu-id="98442-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="98442-109">Podporují pouze jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="98442-109">They support only a single server instance.</span></span> <span data-ttu-id="98442-110">Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy kde obslužné rutiny lze snadno předat podřízeného procesu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="98442-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="98442-111">V rozhraní .NET Framework, můžete implementovat anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="98442-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="98442-112">V tématu [postupy: místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="98442-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="98442-113">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="98442-113">Named pipes.</span></span>  
  
     <span data-ttu-id="98442-114">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="98442-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="98442-115">Pojmenované kanály mohou být jednosměrné nebo duplexní.</span><span class="sxs-lookup"><span data-stu-id="98442-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="98442-116">Budou podporovat komunikaci na základě zpráv a povolit více klientů najednou připojit k procesu serveru pomocí kanálu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="98442-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="98442-117">Pojmenované kanály také podporují zosobnění, které umožňuje připojování procesy používat vlastní oprávnění na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="98442-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="98442-118">V rozhraní .NET Framework, můžete implementovat pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="98442-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="98442-119">V tématu [postupy: meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="98442-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98442-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="98442-120">See Also</span></span>  
 [<span data-ttu-id="98442-121">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="98442-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="98442-122">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="98442-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="98442-123">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="98442-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
