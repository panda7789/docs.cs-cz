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
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519471"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání
Pokud metoda je blokovaný, když se čeká na událost má být signalizován, nemůže kontrolu hodnoty tokenu zrušení a včas reagovat. První příklad ukazuje, jak tento problém vyřešit, při práci s událostmi, jako <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> , které nativně nepodporují rozhraní unified zrušení. Druhý příklad ukazuje jednodušší přístup, který používá <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, který nepodporuje sjednocený zrušení.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEvent> k předvedení jak odblokovat obslužné rutiny čekání, které nepodporují jednotné zrušení.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.ManualResetEventSlim> ukazují, jak odblokovat koordinaci primitiv, které podporují sloučený zrušení. Stejným způsobem lze použít s další zjednodušené koordinaci primitiv, jako například <xref:System.Threading.Semaphore> `Slim` a <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
