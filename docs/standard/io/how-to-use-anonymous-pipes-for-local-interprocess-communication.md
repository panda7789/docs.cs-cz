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
ms.openlocfilehash: 16018be820951a2739d602edb99845eb89495d5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706644"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Postupy: Místní meziprocesová komunikace pomocí anonymních kanálů
Anonymní kanály poskytují meziprocesovou komunikaci na místním počítači. Tyto anonymní kanály nabízejí méně funkcí než pojmenované kanály, mají však také menší nákladovou režii. Anonymní kanály lze použít pro usnadnění meziprocesové komunikace na místním počítači. Anonymní kanály nelze použít pro komunikaci v rámci sítě.  
  
 Chcete-li implementovat anonymní kanály, použijte třídy <xref:System.IO.Pipes.AnonymousPipeServerStream> a <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje způsob, jakým lze odeslat řetězec z nadřazeného procesu podřízenému procesu pomocí anonymních kanálů. Tento příklad vytvoří objekt <xref:System.IO.Pipes.AnonymousPipeServerStream> v nadřazeném procesu s hodnotou <xref:System.IO.Pipes.PipeDirection> nastavenou na <xref:System.IO.Pipes.PipeDirection.Out>. Nadřazený proces poté vytvoří podřízený proces pomocí popisovače klienta a objekt <xref:System.IO.Pipes.AnonymousPipeClientStream>. Podřízený proces má hodnotu <xref:System.IO.Pipes.PipeDirection> nastavenu na <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Nadřazený proces poté odešle řetězec zadaný uživatelem podřízenému procesu. Řetězec se zobrazí v konzole podřízeného procesu.  
  
 Následující příklad znázorňuje proces serveru.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje proces klienta. Proces serveru spustí proces klienta a poskytne tomuto procesu popisovač klienta. Výsledný spustitelný soubor z kódu klienta by měl být pojmenován jako `pipeClient.exe` a zkopírován do stejného adresáře jako spustitelný soubor serveru před spuštěním procesu serveru.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Viz také:

- [Pojmenované kanály](../../../docs/standard/io/pipe-operations.md)
- [Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
