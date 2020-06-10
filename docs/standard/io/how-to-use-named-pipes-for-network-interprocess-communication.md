---
title: 'Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů'
description: Viz dva příklady použití pojmenovaných kanálů pro komunikaci mezi procesy mezi serverem kanálu a jedním nebo více klienty kanálu v síti.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: a529d1d44a903df36099a59e07f4582554d230f2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662560"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="f521e-103">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="f521e-103">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="f521e-104">Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu.</span><span class="sxs-lookup"><span data-stu-id="f521e-104">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="f521e-105">Nabízejí větší počet funkcí než anonymní kanály, které poskytují meziprocesovou komunikaci v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f521e-105">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="f521e-106">Pojmenované kanály podporují plně duplexní komunikaci přes síť a větší počet instancí serveru, komunikaci založenou na zprávách a zosobnění klienta, což umožňuje připojujícím se procesům použít vlastní sadu oprávnění na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="f521e-106">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="f521e-107">Chcete-li implementovat pojmenované kanály, použijte třídu <xref:System.IO.Pipes.NamedPipeServerStream> a třídu <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="f521e-107">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f521e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f521e-108">Example</span></span>  
 <span data-ttu-id="f521e-109">Následující příklad znázorňuje způsob vytvoření pojmenovaného kanálu pomocí třídy <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="f521e-109">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="f521e-110">V tomto příkladu vytvoří proces serveru čtyři vlákna.</span><span class="sxs-lookup"><span data-stu-id="f521e-110">In this example, the server process creates four threads.</span></span> <span data-ttu-id="f521e-111">Jednotlivá vlákna mohou přijmout připojení klienta.</span><span class="sxs-lookup"><span data-stu-id="f521e-111">Each thread can accept a client connection.</span></span> <span data-ttu-id="f521e-112">Proces připojeného klienta poté serveru poskytne název souboru.</span><span class="sxs-lookup"><span data-stu-id="f521e-112">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="f521e-113">Pokud má klient dostatečná oprávnění, proces serveru otevře soubor a odešle obsah zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="f521e-113">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="f521e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f521e-114">Example</span></span>  
 <span data-ttu-id="f521e-115">Následující příklad znázorňuje proces klienta, který používá třídu <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="f521e-115">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="f521e-116">Klient se připojí k procesu serveru a odešle serveru název souboru.</span><span class="sxs-lookup"><span data-stu-id="f521e-116">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="f521e-117">Příklad používá zosobnění, takže identita, pod kterou je spuštěna klientská aplikace, musí mít oprávnění přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="f521e-117">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="f521e-118">Server poté odešle obsah souboru zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="f521e-118">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="f521e-119">Obsah souboru je následně zobrazen v konzole.</span><span class="sxs-lookup"><span data-stu-id="f521e-119">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f521e-120">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f521e-120">Robust Programming</span></span>  
 <span data-ttu-id="f521e-121">Procesy klienta a serveru uvedené v tomto příkladu jsou určeny ke spuštění ve stejném počítači, takže název serveru předaný objektu <xref:System.IO.Pipes.NamedPipeClientStream> je `"."`.</span><span class="sxs-lookup"><span data-stu-id="f521e-121">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="f521e-122">Pokud procesy klienta a serveru byly na různých počítačích, znak `"."` by měl být nahrazen síťovým názvem počítače, na kterém je spuštěn proces serveru.</span><span class="sxs-lookup"><span data-stu-id="f521e-122">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f521e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f521e-123">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="f521e-124">Kanály</span><span class="sxs-lookup"><span data-stu-id="f521e-124">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="f521e-125">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="f521e-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
