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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6543c2e5ea953887e699ee6f9ca3b70e08e5ae85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání
Pokud metoda je blokovaný, když se čeká na signál události, nelze ho zkontrolujte hodnotu token zrušení a odpověď včas. V prvním příkladu ukazuje, jak chcete tento problém vyřešit, při práci s událostmi, jako <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> který nativně nepodporují rozhraní jednotná zrušení. Druhý příklad ukazuje zefektivnění přístup, který používá <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, který nepodporuje unified zrušení.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEvent> abychom ukázali, jak odblokovat obslužné rutiny čekání, které nepodporují jednotná zrušení.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEventSlim> ukazují, jak odblokovat koordinaci primitivních elementů, které podporují sloučený zrušení. Ve stejný přístup lze použít s další primitiv lightweight spolupráce, jako <xref:System.Threading.Semaphore> `Slim` a <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
