---
title: 'Postupy: Naslouchání více požadavkům zrušení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: 3f92d1d9e8fec91475886e8bd7bffbc97bb632a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279392"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Postupy: Naslouchání více požadavkům zrušení
Tento příklad ukazuje, jak naslouchat dvěma tokeny zrušení současně, abyste mohli zrušit operaci, pokud ji buď vyžádá.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> Metoda používá pro spojení dvou tokenů do jednoho tokenu. To umožňuje předat token do metod, které jako argument přebírají pouze jeden token zrušení. Příklad ukazuje běžný scénář, ve kterém metoda musí sledovat token předaný z vnějšku třídy a token vygenerovaný uvnitř třídy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Když propojený token vyvolá výjimku <xref:System.OperationCanceledException> , token, který je předán do výjimky, je propojený token, nikoli buď tokeny předchůdce. Chcete-li zjistit, které z tokenů byly zrušeny, zkontrolujte stav tokenů předchůdce přímo.  
  
 V tomto příkladu <xref:System.AggregateException> by neměl být nikdy vyvolána, ale je zde zachycena z toho důvodu, že v reálných scénářích jakékoli jiné výjimky kromě těch <xref:System.OperationCanceledException> , které jsou vyvolány z delegáta úkolu, jsou zabaleny do <xref:System.AggregateException> .  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md)
