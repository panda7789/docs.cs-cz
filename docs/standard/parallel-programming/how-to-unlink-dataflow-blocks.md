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
ms.openlocfilehash: 8af978ca2ca237988dae8328656d70574dbc1f14
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288053"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Postupy: Zrušení propojení bloků toku dat
Tento dokument popisuje, jak odpojit cílový blok toku dat od jeho zdroje.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekty, z nichž každý volá `TrySolution` metodu pro výpočet hodnoty. Tento příklad vyžaduje pouze výsledek od prvního volání do `TrySolution` dokončení.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Chcete-li získat hodnotu z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, který je dokončen, tento příklad definuje `ReceiveFromAny(T)` metodu. `ReceiveFromAny(T)`Metoda přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a propojí každý z těchto objektů s <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektem. Použijete-li <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metodu k propojení zdrojového bloku toku dat s cílovým blokem, zdroj šíří zprávy do cíle, protože data budou k dispozici. Vzhledem k tomu, že <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> Třída přijímá pouze první zprávu, která je nabízena, `ReceiveFromAny(T)` Metoda vytvoří svůj výsledek voláním <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody. Tím se vytvoří první zpráva, která je nabídnuta <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>Metoda má přetíženou verzi, která přebírá <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> objekt s <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> vlastností, která, pokud je nastavena na `1` , instruuje zdrojový blok k odpojení od cíle poté, co cíl přijme jednu zprávu ze zdroje. Je důležité, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> aby objekt mohl odkázat z jeho zdrojů, protože vztah mezi polem zdrojů a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektem již není požadován poté, co <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt obdrží zprávu.  
  
 Chcete-li povolit zbývající volání na `TrySolution` konec, poté, co jeden z nich vypočítá hodnotu, `TrySolution` Metoda převezme <xref:System.Threading.CancellationToken> objekt, který je zrušen po volání metody `ReceiveFromAny(T)` return. <xref:System.Threading.SpinWait.SpinUntil%2A>Metoda vrátí, když <xref:System.Threading.CancellationToken> je tento objekt zrušen.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
