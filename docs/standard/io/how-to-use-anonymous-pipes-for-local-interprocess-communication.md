---
title: 'Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db23b424d4357ad94b8b0de66ca71726b765321e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47234806"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="32c34-102">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="32c34-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="32c34-103">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="32c34-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="32c34-104">Tyto anonymní kanály nabízejí méně funkcí než pojmenované kanály, mají však také menší nákladovou režii.</span><span class="sxs-lookup"><span data-stu-id="32c34-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="32c34-105">Anonymní kanály lze použít pro usnadnění meziprocesové komunikace na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="32c34-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="32c34-106">Anonymní kanály nelze použít pro komunikaci v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="32c34-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="32c34-107">Chcete-li implementovat anonymní kanály, použijte třídy <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="32c34-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c34-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="32c34-108">Example</span></span>  
 <span data-ttu-id="32c34-109">Následující příklad znázorňuje způsob, jakým lze odeslat řetězec z nadřazeného procesu podřízenému procesu pomocí anonymních kanálů.</span><span class="sxs-lookup"><span data-stu-id="32c34-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="32c34-110">Tento příklad vytvoří objekt <xref:System.IO.Pipes.AnonymousPipeServerStream> v nadřazeném procesu s hodnotou <xref:System.IO.Pipes.PipeDirection> nastavenou na <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="32c34-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="32c34-111">Nadřazený proces poté vytvoří podřízený proces pomocí popisovače klienta a objekt <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="32c34-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="32c34-112">Podřízený proces má hodnotu <xref:System.IO.Pipes.PipeDirection> nastavenu na <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="32c34-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="32c34-113">Nadřazený proces poté odešle řetězec zadaný uživatelem podřízenému procesu.</span><span class="sxs-lookup"><span data-stu-id="32c34-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="32c34-114">Řetězec se zobrazí v konzole podřízeného procesu.</span><span class="sxs-lookup"><span data-stu-id="32c34-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="32c34-115">Následující příklad znázorňuje proces serveru.</span><span class="sxs-lookup"><span data-stu-id="32c34-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="32c34-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="32c34-116">Example</span></span>  
 <span data-ttu-id="32c34-117">Následující příklad znázorňuje proces klienta.</span><span class="sxs-lookup"><span data-stu-id="32c34-117">The following example shows the client process.</span></span> <span data-ttu-id="32c34-118">Proces serveru spustí proces klienta a poskytne tomuto procesu popisovač klienta.</span><span class="sxs-lookup"><span data-stu-id="32c34-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="32c34-119">Výsledný spustitelný soubor z kódu klienta by měl být pojmenován jako `pipeClient.exe` a zkopírován do stejného adresáře jako spustitelný soubor serveru před spuštěním procesu serveru.</span><span class="sxs-lookup"><span data-stu-id="32c34-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="32c34-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32c34-120">See also</span></span>

- [<span data-ttu-id="32c34-121">Pojmenované kanály</span><span class="sxs-lookup"><span data-stu-id="32c34-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
- [<span data-ttu-id="32c34-122">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="32c34-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
