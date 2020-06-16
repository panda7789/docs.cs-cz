---
title: Operace kanálu v .NET
description: 'Přečtěte si o operacích kanálu v rozhraní .NET. Kanály poskytují prostředky pro komunikaci mezi procesy. Existují dva druhy kanálů: anonymní kanály a pojmenované kanály.'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 35a3910bbab1b34f085a55524be0b18b3fa81958
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768882"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="c07b4-105">Operace kanálu v .NET</span><span class="sxs-lookup"><span data-stu-id="c07b4-105">Pipe Operations in .NET</span></span>
<span data-ttu-id="c07b4-106">Kanály poskytují prostředky pro komunikaci mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c07b4-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="c07b4-107">Existují dva typy kanálů:</span><span class="sxs-lookup"><span data-stu-id="c07b4-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="c07b4-108">Anonymní kanály.</span><span class="sxs-lookup"><span data-stu-id="c07b4-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="c07b4-109">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="c07b4-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="c07b4-110">Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="c07b4-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="c07b4-111">Anonymní kanály jsou jednosměrné a nelze je použít přes síť.</span><span class="sxs-lookup"><span data-stu-id="c07b4-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="c07b4-112">Podporují jenom jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="c07b4-112">They support only a single server instance.</span></span> <span data-ttu-id="c07b4-113">Anonymní kanály jsou užitečné pro komunikaci mezi vlákny nebo mezi nadřazenými a podřízenými procesy, kde je možné obslužné rutiny kanálu snadno předat podřízenému procesu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="c07b4-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="c07b4-114">V rozhraní .NET implementujete anonymní kanály pomocí <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> tříd a.</span><span class="sxs-lookup"><span data-stu-id="c07b4-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="c07b4-115">Viz [Postupy: použití anonymních kanálů pro místní komunikaci mezi procesy](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="c07b4-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="c07b4-116">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="c07b4-116">Named pipes.</span></span>  
  
     <span data-ttu-id="c07b4-117">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="c07b4-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="c07b4-118">Pojmenované kanály můžou být jednosměrné nebo duplexní.</span><span class="sxs-lookup"><span data-stu-id="c07b4-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="c07b4-119">Podporují komunikaci založenou na zprávách a umožňují více klientům současně se současně připojit k procesu serveru pomocí stejného názvu kanálu.</span><span class="sxs-lookup"><span data-stu-id="c07b4-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="c07b4-120">Pojmenované kanály také podporují zosobnění, které umožňuje připojujícím se procesům používat na vzdálených serverech vlastní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c07b4-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="c07b4-121">V rozhraní .NET implementujete pojmenované kanály pomocí <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> tříd a.</span><span class="sxs-lookup"><span data-stu-id="c07b4-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="c07b4-122">Viz [Postupy: použití pojmenovaných kanálů pro komunikaci mezi procesy sítě](how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="c07b4-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07b4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c07b4-123">See also</span></span>

- [<span data-ttu-id="c07b4-124">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="c07b4-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="c07b4-125">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="c07b4-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="c07b4-126">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="c07b4-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
