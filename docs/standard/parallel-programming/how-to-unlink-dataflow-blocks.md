---
title: 'Postupy: Zrušení propojení bloků toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
ms.openlocfilehash: b49cfc9730ba154202baf15093a54ba3ce0e2a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139298"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Postupy: Zrušení propojení bloků toku dat
Tento dokument popisuje, jak odpojit cílový blok toku dat od jeho zdroje.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> tři objekty, `TrySolution` z nichž každý volá metodu k výpočtu hodnoty. Tento příklad vyžaduje pouze výsledek z `TrySolution` první volání do konce.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Chcete-li získat hodnotu z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, `ReceiveFromAny(T)` který dokončí, tento příklad definuje metodu. Metoda `ReceiveFromAny(T)` přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a propojuje každý <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> z těchto objektů s objektem. Při použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody k propojení bloku zdrojového toku dat s cílovým blokem zdroj rozšíří zprávy do cíle, jakmile budou data k dispozici. Vzhledem <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> k tomu, že třída přijímá pouze `ReceiveFromAny(T)` první zprávu, která je <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> nabízena, metoda vytvoří svůj výsledek voláním metody. Tím se vytvoří první zpráva, která <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> je nabízena k objektu. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> má přetížené verze, <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> která přebírá <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> objekt s vlastností, `1`která, když je nastavena na , pokyn zdrojový blok odpojit od cíle poté, co cíl obdrží jednu zprávu ze zdroje. Je důležité, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> aby se objekt odpojil od svých zdrojů, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> protože vztah mezi <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> polem zdrojů a objektem již není vyžadován poté, co objekt obdrží zprávu.  
  
 Chcete-li povolit `TrySolution` zbývající volání do konce po jednom `TrySolution` z nich <xref:System.Threading.CancellationToken> vypočítá hodnotu, metoda `ReceiveFromAny(T)` trvá objekt, který je zrušen po volání vrátí. Metoda <xref:System.Threading.SpinWait.SpinUntil%2A> vrátí při <xref:System.Threading.CancellationToken> zrušení tohoto objektu.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
