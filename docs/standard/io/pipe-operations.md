---
title: Operace potrubí v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706553"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="d9833-102">Operace potrubí v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d9833-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="d9833-103">Potrubí poskytují prostředky pro meziprocesovou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d9833-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="d9833-104">Existují dva typy trubek:</span><span class="sxs-lookup"><span data-stu-id="d9833-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="d9833-105">Anonymní trubky.</span><span class="sxs-lookup"><span data-stu-id="d9833-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="d9833-106">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="d9833-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="d9833-107">Anonymní kanály vyžadují menší režii než pojmenované kanály, ale nabízejí omezené služby.</span><span class="sxs-lookup"><span data-stu-id="d9833-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="d9833-108">Anonymní kanály jsou jednosměrné a nelze je používat v síti.</span><span class="sxs-lookup"><span data-stu-id="d9833-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="d9833-109">Podporují pouze jednu instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="d9833-109">They support only a single server instance.</span></span> <span data-ttu-id="d9833-110">Anonymní kanály jsou užitečné pro komunikaci mezi podprocesy nebo mezi nadřazené a podřízené procesy, kde popisovače kanálu lze snadno předat podřízenému procesu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d9833-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="d9833-111">V rozhraní .NET implementovat anonymní <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> kanály pomocí a třídy.</span><span class="sxs-lookup"><span data-stu-id="d9833-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="d9833-112">Viz [Postup: Použití anonymních kanálů pro místní meziprocesovou komunikaci](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="d9833-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="d9833-113">Pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="d9833-113">Named pipes.</span></span>  
  
     <span data-ttu-id="d9833-114">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="d9833-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="d9833-115">Pojmenované kanály mohou být jednosměrné nebo duplexní.</span><span class="sxs-lookup"><span data-stu-id="d9833-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="d9833-116">Podporují komunikaci založenou na textech a umožňují více klientům připojit se současně k procesu serveru pomocí stejného názvu kanálu.</span><span class="sxs-lookup"><span data-stu-id="d9833-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="d9833-117">Pojmenované kanály také podporují zosobnění, což umožňuje připojovacím procesům používat vlastní oprávnění na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="d9833-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="d9833-118">V rozhraní .NET implementujete <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> pojmenované kanály pomocí tříd a.</span><span class="sxs-lookup"><span data-stu-id="d9833-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="d9833-119">Viz [Postup: Použití pojmenovaných kanálů pro meziprocesovou komunikaci v síti](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="d9833-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9833-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9833-120">See also</span></span>

- [<span data-ttu-id="d9833-121">I/O souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="d9833-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="d9833-122">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="d9833-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="d9833-123">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="d9833-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
