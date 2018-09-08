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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ba8000544d0b7d35a818d41a75f38e6fd0293d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178560"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Postupy: Naslouchání více požadavkům zrušení
Tento příklad ukazuje, jak tak, aby naslouchala na dvou tokeny zrušení současně tak, aby operace můžete zrušit, pokud buď token požadavku.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá pro připojení dvou tokeny do jednoho tokenu. To umožňuje token, který má předané do metod, které přijímají token jako argument pouze jeden zrušení. Tento příklad ukazuje běžný scénář, ve kterém metoda zachovávají i token předat z mimo třídu a token generuje uvnitř třídy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Pokud vyvolá propojené token <xref:System.OperationCanceledException>, token, který je předán výjimka je propojené token, není buď tokenů předchůdce. Pokud chcete zjistit, které tokenů byla zrušena, zkontrolujte stav předchůdce tokenů přímo.  
  
 V tomto příkladu <xref:System.AggregateException> by nikdy být vyvolána, ale to je zachycena zde protože ve skutečných scénářích všechny výjimky kromě <xref:System.OperationCanceledException> , které jsou vyvolány z delegátu úlohy jsou zabaleny v <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
