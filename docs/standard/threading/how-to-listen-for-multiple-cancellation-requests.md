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
ms.openlocfilehash: e35472040b6ee1263ebc4c4968fa1822045a2064
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138014"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Postupy: Naslouchání více požadavkům zrušení
Tento příklad ukazuje, jak poslouchat dva tokeny zrušení současně, takže můžete zrušit operaci, pokud jeden token požaduje.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá k připojení dvou tokenů do jednoho tokenu. To umožňuje token, který má být předán metodám, které berou pouze jeden token zrušení jako argument. Příklad ukazuje běžný scénář, ve kterém musí metoda sledovat token předaný mimo třídu a token generovaný uvnitř třídy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Když propojený token vyvolá <xref:System.OperationCanceledException>, token, který je předán do výjimky je propojený token, nikoli jeden z tokenů předchůdce. Chcete-li zjistit, který z tokenů byl zrušen, zkontrolujte stav tokenů předchůdce přímo.  
  
 V tomto <xref:System.AggregateException> příkladu by nikdy být vyvolána, ale je zachycen zde, <xref:System.OperationCanceledException> protože v reálném scénářích všechny jiné <xref:System.AggregateException>výjimky kromě toho, které jsou vyvolány z delegáta úkolu jsou zabaleny do .  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
