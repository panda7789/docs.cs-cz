---
title: "Postupy: Zrušení propojení bloků toku dat"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3c0d3a6d94e2e9eb65046267f14feff0c056cb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a>Postupy: Zrušení propojení bloků toku dat
Tento dokument popisuje, jak zrušení propojení cíl bloku toku dat z její zdroj.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekty, každý o voláních, která `TrySolution` metoda k výpočtu hodnoty. Tento příklad vyžaduje pouze výsledky z prvního volání `TrySolution` ukončíte.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Získat hodnotu z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, který dokončí, tento příklad definuje `ReceiveFromAny(T)` metoda. `ReceiveFromAny(T)` Metoda přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a každý z těchto objektů do odkazů <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu. Při použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda propojení bloku toku dat zdrojového na cílový blok, zdroj rozšíří zprávy do cílové, jakmile data k dispozici. Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třída přijímá pouze první zprávy, které nabízí, `ReceiveFromAny(T)` metoda vytváří svůj výsledek voláním <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metoda. Tímto se vytvoří první zprávu, která se nabízí na <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda má přetížené verze, která přijímá <xref:System.Boolean> parametr `unlinkAfterOne` , když je nastavená na `True`, dá pokyn blok zdroj, který má zrušit propojení s cílem po cíl přijme jeden zprávu ze zdroje. Je důležité pro <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt, který chcete zrušit propojení její zdroje, protože vztah mezi poli zdroje a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt již není vyžadován po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt přijme nějakou zprávu.  
  
 Povolit zbývající volání `TrySolution` na konec po jeden z nich vypočítá hodnotu, `TrySolution` metoda trvá <xref:System.Threading.CancellationToken> objekt, který je zrušit po zavolání `ReceiveFromAny(T)` vrátí. <xref:System.Threading.SpinWait.SpinUntil%2A> Metoda vrátí, když to <xref:System.Threading.CancellationToken> objektu je zrušená.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  

## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
