---
title: "BackgroundWorker – přehled komponenty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96fc5e1929589321872ba30d8c3821b4fd47ca8b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker – přehled komponenty
Existuje mnoho běžně provádět operace, které může trvat dlouhou dobu spuštění. Příklad:  
  
-   Soubory ke stažení bitové kopie  
  
-   Volání webové služby  
  
-   Soubor se stáhne a odešle (včetně pro aplikace peer-to-peer)  
  
-   Komplexní místní výpočty  
  
-   Databázové transakce  
  
-   Místní disk přístupu, vzhledem k jeho nízká rychlost relativně k přístupu do paměti  
  
 Operace, jako je to může způsobit přesah při spuštění uživatelského rozhraní. Pokud chcete, aby citlivé uživatelské rozhraní a se potýkají s velká zpoždění spojené s takové operace, <xref:System.ComponentModel.BackgroundWorker> součást nabízí pohodlný řešení.  
  
 <xref:System.ComponentModel.BackgroundWorker> Součásti budete moci provést časově náročná operace asynchronně ("v pozadí"), na vlákno, která se liší od hlavního vlákna uživatelského rozhraní aplikace. Použít <xref:System.ComponentModel.BackgroundWorker>, jednoduše nedostane jakou metodu časově náročné pracovním provést na pozadí, a poté zavoláte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda. Volající vlákno dál normálně spustit, když pracovní metoda běží asynchronně. Po dokončení metody <xref:System.ComponentModel.BackgroundWorker> výstrahy volající vlákno vypálením <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí, který volitelně obsahuje výsledky operace.  
  
 <xref:System.ComponentModel.BackgroundWorker> Součást má k dispozici **sada nástrojů**v **součásti** kartě. Chcete-li přidat <xref:System.ComponentModel.BackgroundWorker> do svého formuláře, přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti do formuláře. Zobrazí se na hlavním panelu součástí a její vlastnosti se zobrazí v **vlastnosti** okno.  
  
 Chcete-li začít asynchronní operaci, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>přijímá volitelný `object` parametr, který slouží k předání argumentů metodu pracovního procesu. <xref:System.ComponentModel.BackgroundWorker> Třídy zpřístupňuje <xref:System.ComponentModel.BackgroundWorker.DoWork> událostí, ke kterému je pracovní vlákno připojená prostřednictvím <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Trvá obslužné rutiny události <xref:System.ComponentModel.DoWorkEventArgs> parametr, který má <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost. Tato vlastnost přijímá parametru z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a se dá předat do pracovního procesu metodu, která bude volána v <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Následující příklad ukazuje, jak přiřadit výsledku z pracovní metodu s názvem `ComputeFibonacci`. Je součástí většího příkladu, které můžete najít v [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Další informace o používání obslužných rutin událostí najdete v tématu [události](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Při použití jakékoli více vláken, potenciálně vystavit sami na velmi závažnou a komplexní chyby. Obrátit [spravované dělení na vlákna osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací řešení, která používá více vláken.  
  
 Další informace o používání <xref:System.ComponentModel.BackgroundWorker> třídy najdete v tématu [postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Viz také  
 [NENÍ v sestavení: Více vláken v jazyce Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
