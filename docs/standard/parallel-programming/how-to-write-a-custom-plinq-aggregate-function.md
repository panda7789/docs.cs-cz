---
title: 'Postupy: Psaní vlastní agregační funkce pro PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82e4ed0f93d7c41bc36427159442cc88b0a7867d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038830"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Postupy: Psaní vlastní agregační funkce pro PLINQ
Tento příklad ukazuje způsob použití <xref:System.Linq.ParallelEnumerable.Aggregate%2A> způsob, jak použít vlastní agregační funkce zdrojové sekvence.  
  
> [!WARNING]
>  V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá směrodatnou odchylku posloupnost celých čísel.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Tento příklad používá přetížení operátoru standardního dotazu, které jsou jedinečné pro PLINQ. Toto přetížení má speciální <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr. Tento delegát kombinuje výsledky ze všech vláken, než provede konečné výpočtu na agregované výsledky. V tomto příkladu jsme sečtení částek ze všech vláken.  
  
 Všimněte si, že tělo výrazu lambda sestává z jediného výrazu, návratová hodnota <xref:System.Func%602?displayProperty=nameWithType> delegát je hodnota výrazu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>  
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
