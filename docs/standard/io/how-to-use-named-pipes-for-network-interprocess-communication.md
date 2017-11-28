---
title: "Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 952600e71311184c4a4f906734addbf335d0358a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Postupy: Meziprocesová síťová komunikace pomocí pojmenovaných kanálů
Pojmenované kanály poskytují meziprocesovou komunikaci mezi serverem kanálu a jedním nebo několika klienty kanálu. Nabízejí větší počet funkcí než anonymní kanály, které poskytují meziprocesovou komunikaci v místním počítači. Pojmenované kanály podporují plně duplexní komunikaci přes síť a větší počet instancí serveru, komunikaci založenou na zprávách a zosobnění klienta, což umožňuje připojujícím se procesům použít vlastní sadu oprávnění na vzdálených serverech.  
  
 Chcete-li implementovat pojmenované kanály, použijte třídu <xref:System.IO.Pipes.NamedPipeServerStream> a třídu <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje způsob vytvoření pojmenovaného kanálu pomocí třídy <xref:System.IO.Pipes.NamedPipeServerStream>. V tomto příkladu vytvoří proces serveru čtyři vlákna. Jednotlivá vlákna mohou přijmout připojení klienta. Proces připojeného klienta poté serveru poskytne název souboru. Pokud má klient dostatečná oprávnění, proces serveru otevře soubor a odešle obsah zpět do klienta.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje proces klienta, který používá třídu <xref:System.IO.Pipes.NamedPipeClientStream>. Klient se připojí k procesu serveru a odešle serveru název souboru. Příklad používá zosobnění, takže identita, pod kterou je spuštěna klientská aplikace, musí mít oprávnění přístupu k souboru. Server poté odešle obsah souboru zpět do klienta. Obsah souboru je následně zobrazen v konzole.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Procesy klienta a serveru uvedené v tomto příkladu jsou určeny ke spuštění ve stejném počítači, takže název serveru předaný objektu <xref:System.IO.Pipes.NamedPipeClientStream> je `"."`. Pokud procesy klienta a serveru byly na různých počítačích, znak `"."` by měl být nahrazen síťovým názvem počítače, na kterém je spuštěn proces serveru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [Kanály](../../../docs/standard/io/pipe-operations.md)  
 [Postupy: místní meziprocesová komunikace pomocí anonymních kanálů](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
