---
title: 'Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů'
description: Naučte se používat anonymní kanály pro místní komunikaci mezi procesy na místním počítači v .NET. Anonymní kanály vyžadují méně režijních nákladů než pojmenované kanály.
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
ms.openlocfilehash: 090a25aea4f280fc2ad00cf7777a501c475dfc66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594800"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="b88c4-104">Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů</span><span class="sxs-lookup"><span data-stu-id="b88c4-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="b88c4-105">Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b88c4-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="b88c4-106">Tyto anonymní kanály nabízejí méně funkcí než pojmenované kanály, mají však také menší nákladovou režii.</span><span class="sxs-lookup"><span data-stu-id="b88c4-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="b88c4-107">Anonymní kanály lze použít pro usnadnění meziprocesové komunikace na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b88c4-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="b88c4-108">Anonymní kanály nelze použít pro komunikaci v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="b88c4-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="b88c4-109">Chcete-li implementovat anonymní kanály, použijte třídy <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="b88c4-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b88c4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b88c4-110">Example</span></span>  
 <span data-ttu-id="b88c4-111">Následující příklad znázorňuje způsob, jakým lze odeslat řetězec z nadřazeného procesu podřízenému procesu pomocí anonymních kanálů.</span><span class="sxs-lookup"><span data-stu-id="b88c4-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="b88c4-112">Tento příklad vytvoří objekt <xref:System.IO.Pipes.AnonymousPipeServerStream> v nadřazeném procesu s hodnotou <xref:System.IO.Pipes.PipeDirection> nastavenou na <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="b88c4-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="b88c4-113">Nadřazený proces poté vytvoří podřízený proces pomocí popisovače klienta a objekt <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="b88c4-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="b88c4-114">Podřízený proces má hodnotu <xref:System.IO.Pipes.PipeDirection> nastavenu na <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="b88c4-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="b88c4-115">Nadřazený proces poté odešle řetězec zadaný uživatelem podřízenému procesu.</span><span class="sxs-lookup"><span data-stu-id="b88c4-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="b88c4-116">Řetězec se zobrazí v konzole podřízeného procesu.</span><span class="sxs-lookup"><span data-stu-id="b88c4-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="b88c4-117">Následující příklad znázorňuje proces serveru.</span><span class="sxs-lookup"><span data-stu-id="b88c4-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="b88c4-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b88c4-118">Example</span></span>  
 <span data-ttu-id="b88c4-119">Následující příklad znázorňuje proces klienta.</span><span class="sxs-lookup"><span data-stu-id="b88c4-119">The following example shows the client process.</span></span> <span data-ttu-id="b88c4-120">Proces serveru spustí proces klienta a poskytne tomuto procesu popisovač klienta.</span><span class="sxs-lookup"><span data-stu-id="b88c4-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="b88c4-121">Výsledný spustitelný soubor z kódu klienta by měl být pojmenován jako `pipeClient.exe` a zkopírován do stejného adresáře jako spustitelný soubor serveru před spuštěním procesu serveru.</span><span class="sxs-lookup"><span data-stu-id="b88c4-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="b88c4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b88c4-122">See also</span></span>

- [<span data-ttu-id="b88c4-123">Kanály</span><span class="sxs-lookup"><span data-stu-id="b88c4-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="b88c4-124">Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů</span><span class="sxs-lookup"><span data-stu-id="b88c4-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
