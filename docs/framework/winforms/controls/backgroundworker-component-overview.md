---
title: BackgroundWorker – přehled komponenty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: d7d99cf87507237b23cb40c58b2308643f7f1056
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138484"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker – přehled komponenty
Existuje mnoho běžně provádí operace, které může trvat dlouhou dobu spuštění. Příklad:  
  
-   Soubory ke stažení bitové kopie  
  
-   Volání webové služby  
  
-   Soubor se stáhne a nahraje (včetně aplikace peer-to-peer)  
  
-   Komplexní místní výpočty  
  
-   Databázové transakce  
  
-   Místní disk, jeho pomalé vzhledem k přístupu do paměti udělený přístup  
  
 Operace, jako je to může způsobit uživatelského rozhraní přestane reagovat, když jsou spuštěné. Pokud chcete, aby responzivní uživatelské rozhraní a se potýkají s dlouhým zpožděním spojené s takovými operacemi <xref:System.ComponentModel.BackgroundWorker> součást poskytuje pohodlné řešení.  
  
 <xref:System.ComponentModel.BackgroundWorker> Komponenty vám dává možnost provádět časově náročná operace asynchronně ("na pozadí"), ve vlákně, která se liší od hlavního vlákna uživatelského rozhraní vaší aplikace. Použití <xref:System.ComponentModel.BackgroundWorker>, vám stačí určit, jakou metodu časově náročné pracovní provádět na pozadí, a poté zavoláte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda. Volající vlákno dál běží normálně při metodě pracovního podprocesu běží asynchronně. Po dokončení metody <xref:System.ComponentModel.BackgroundWorker> výstrahy volající vlákno s jeho spuštění <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí, který volitelně obsahuje výsledky operace.  
  
 <xref:System.ComponentModel.BackgroundWorker> Komponenta je k dispozici **nástrojů**v **součásti** kartu. Chcete-li přidat <xref:System.ComponentModel.BackgroundWorker> do formuláře, přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu do formuláře. Zobrazí se v panelu komponent a jeho vlastnosti se zobrazí v **vlastnosti** okna.  
  
 Chcete-li začít asynchronní operace, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> přijímá volitelný `object` parametr, který slouží k předání argumentů metodě pracovního procesu. <xref:System.ComponentModel.BackgroundWorker> Třídy zpřístupňuje <xref:System.ComponentModel.BackgroundWorker.DoWork> události, ke kterému je připojený pracovní podproces prostřednictvím <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužná rutina události <xref:System.ComponentModel.DoWorkEventArgs> parametr, který má <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost. Tato vlastnost přijímá parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a mohou být předány do metody pracovního procesu, která bude volána v <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Následující příklad ukazuje, jak přiřadit výsledek z pracovního procesu metodu nazvanou `ComputeFibonacci`. Je součástí většího příkladu, které můžete vyhledat v [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Další informace o používání obslužných rutin událostí, naleznete v tématu [události](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb. Poraďte [spravovaných vláken osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreading.  
  
 Další informace o používání <xref:System.ComponentModel.BackgroundWorker> najdete v tématu [postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Viz také:

- [Dělení na spravovaná vlákna](../../../../docs/standard/threading/index.md)
- [Přehled asynchronních vzorů založených na událostech](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
