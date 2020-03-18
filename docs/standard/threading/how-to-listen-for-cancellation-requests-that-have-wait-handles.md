---
title: 'Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137978"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání
Pokud je metoda blokována, zatímco čeká na signalizaci události, nemůže zkontrolovat hodnotu tokenu zrušení a reagovat včas. První příklad ukazuje, jak tento problém vyřešit při <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> práci s událostmi, jako jsou například nepodporují sjednocené zrušení rámce. Druhý příklad ukazuje efektivnější přístup, <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>který používá , který podporuje jednotné zrušení.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEvent> a chcete-li ukázat, jak odblokovat popisovače čekání, které nepodporují jednotné zrušení.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEventSlim> a demonstrovat, jak odblokovat koordinaci primitiv, které podporují jednotné zrušení. Stejný přístup lze použít s jinými lehkými <xref:System.Threading.Semaphore> `Slim` <xref:System.Threading.CountdownEvent>prvky koordinace, jako jsou například a .  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
