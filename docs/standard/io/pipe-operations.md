---
title: Operace kanálu v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706553"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="0840e-102">Operace kanálu v .NET</span><span class="sxs-lookup"><span data-stu-id="0840e-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="0840e-103">Kanály poskytují prostředky pro komunikaci mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0840e-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="0840e-104">Existují dva typy kanálů:</span><span class="sxs-lookup"><span data-stu-id="0840e-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="0840e-105">Anonymní kanály.</span><span class="sxs-lookup"><span data-stu-id="0840e-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="0840e-106">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="0840e-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="0840e-107">Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="0840e-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="0840e-108">Anonymní kanály jsou jednosměrné a nelze je použít přes síť.</span><span class="sxs-lookup"><span data-stu-id="0840e-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="0840e-109">Podporují jenom jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="0840e-109">They support only a single server instance.</span></span> <span data-ttu-id="0840e-110">Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy, kde je možné obslužné rutiny kanálu snadno předat podřízenému procesu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="0840e-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="0840e-111">V rozhraní .NET implementujete anonymní kanály pomocí tříd <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="0840e-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="0840e-112">Viz [Postupy: použití anonymních kanálů pro místní komunikaci mezi procesy](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="0840e-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="0840e-113">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="0840e-113">Named pipes.</span></span>  
  
     <span data-ttu-id="0840e-114">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="0840e-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="0840e-115">Pojmenované kanály můžou být jednosměrné nebo duplexní.</span><span class="sxs-lookup"><span data-stu-id="0840e-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="0840e-116">Podporují komunikaci založenou na zprávách a umožňují více klientům současně se současně připojit k procesu serveru pomocí stejného názvu kanálu.</span><span class="sxs-lookup"><span data-stu-id="0840e-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="0840e-117">Pojmenované kanály také podporují zosobnění, které umožňuje připojujícím se procesům používat na vzdálených serverech vlastní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0840e-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="0840e-118">V rozhraní .NET implementujete pojmenované kanály pomocí tříd <xref:System.IO.Pipes.NamedPipeServerStream> a <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="0840e-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="0840e-119">Viz [Postupy: použití pojmenovaných kanálů pro komunikaci mezi procesy sítě](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="0840e-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0840e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0840e-120">See also</span></span>

- [<span data-ttu-id="0840e-121">Vstup/výstup souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="0840e-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="0840e-122">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="0840e-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="0840e-123">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="0840e-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
