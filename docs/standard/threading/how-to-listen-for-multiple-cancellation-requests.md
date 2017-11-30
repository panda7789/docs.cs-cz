---
title: "Postupy: Naslouchání více požadavkům zrušení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Postupy: Naslouchání více požadavkům zrušení
Tento příklad ukazuje, jak pro naslouchání na dva zrušení tokenů současně tak, aby operace můžete zrušit, pokud se požaduje buď token.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá pro připojení dvě tokeny do jednoho tokenu. To umožňuje token, který má být předán metod, které přijímají pouze jeden zrušení tokenu jako argument. Příklad ukazuje, běžný scénář, ve kterém musí odpovídat metodu obou token předané z mimo třídu a token vygenerovaný v třídě.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Když vyvolá propojené token <xref:System.OperationCanceledException>, token, který je předán výjimka je propojené token, není buď předchůdce tokenů. Pokud chcete zjistit, které tokenů byla zrušena, zkontrolujte stav tokenů předchůdce přímo.  
  
 V tomto příkladu <xref:System.AggregateException> by měl být nikdy vyvolána, ale je zachycena jako zde protože ve scénářích reálného světa jakékoli výjimky kromě <xref:System.OperationCanceledException> , jsou vyvolány z delegáta úlohy jsou uzavřen do <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Viz také  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
