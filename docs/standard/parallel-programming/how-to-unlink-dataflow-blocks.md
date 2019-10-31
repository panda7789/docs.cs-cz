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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139298"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Postupy: Zrušení propojení bloků toku dat
Tento dokument popisuje, jak odpojit cílový blok toku dat od jeho zdroje.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři objekty <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, z nichž každá volá metodu `TrySolution` pro výpočet hodnoty. Tento příklad vyžaduje pouze výsledek z prvního volání `TrySolution` k dokončení.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Chcete-li získat hodnotu z prvního objektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, který skončí, tento příklad definuje metodu `ReceiveFromAny(T)`. Metoda `ReceiveFromAny(T)` přijímá pole objektů <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a propojí každý z těchto objektů s objektem <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. Použijete-li metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> k propojení bloku zdrojového toku dat s cílovým blokem, zdroj šíří zprávy do cíle, protože data budou k dispozici. Vzhledem k tomu, že třída <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> přijímá pouze první zprávu, která je nabízena, metoda `ReceiveFromAny(T)` vytvoří svůj výsledek voláním metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>. Tím se vytvoří první zpráva, která je nabídnuta objektu <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> má přetíženou verzi, která přebírá objekt <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> s vlastností <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages>, která, pokud je nastavena na `1`, instruuje zdrojový blok k odpojení od cíle poté, co cíl přijme jednu zprávu ze zdroje. Je důležité, aby objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> odpojování od zdrojů, protože vztah mezi polem zdrojů a objektem <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> již není vyžadován poté, co objekt <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> obdrží zprávu.  
  
 Chcete-li povolit zbývající volání `TrySolution` do konce po jednom z nich vypočítá hodnotu, metoda `TrySolution` převezme objekt <xref:System.Threading.CancellationToken>, který je zrušen po volání metody `ReceiveFromAny(T)` vrátí. Metoda <xref:System.Threading.SpinWait.SpinUntil%2A> vrátí, když je tento objekt <xref:System.Threading.CancellationToken> zrušen.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
