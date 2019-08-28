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
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046110"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker – přehled komponenty
Existuje mnoho běžně prováděných operací, které mohou trvat dlouhou dobu. Příklad:  
  
- Stahování obrázků  
  
- Vyvolání webové služby  
  
- Stahování souborů a nahrávání (včetně pro aplikace peer-to-peer)  
  
- Komplexní místní výpočty  
  
- Transakce databáze  
  
- Přístup k místnímu disku s ohledem na jeho zpomalení vzhledem k přístupu k paměti  
  
 Tyto operace mohou způsobit, že vaše uživatelské rozhraní bude blokovat při jejich spuštění. Když chcete reagovat na uživatelské rozhraní s dlouhou dobou zpoždění spojené s těmito operacemi, <xref:System.ComponentModel.BackgroundWorker> komponenta nabízí pohodlné řešení.  
  
 <xref:System.ComponentModel.BackgroundWorker> Komponenta poskytuje možnost asynchronního provádění časově náročných operací ("na pozadí") na vlákně, které se liší od hlavního vlákna uživatelského rozhraní vaší aplikace. Chcete-li <xref:System.ComponentModel.BackgroundWorker>použít, jednoduše Řekněte mu, jakou časově náročnou metodu pracovního procesu spustit na pozadí a pak <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> zavolejte metodu. Volající vlákno pokračuje v normálním běhu, zatímco metoda Worker běží asynchronně. Až se metoda dokončí, <xref:System.ComponentModel.BackgroundWorker> upozorní volající vlákno <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> vyvoláním události, která volitelně obsahuje výsledky operace.  
  
 Součást je k dispozici v **sadě nástrojů**na kartě **součásti.** <xref:System.ComponentModel.BackgroundWorker> Chcete-li <xref:System.ComponentModel.BackgroundWorker> přidat do formuláře, <xref:System.ComponentModel.BackgroundWorker> přetáhněte komponentu do formuláře. Zobrazuje se v zásobníku komponent a jeho vlastnosti se zobrazí v okně **vlastnosti** .  
  
 Chcete-li spustit asynchronní operaci, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>převezme volitelný `object` parametr, který lze použít k předání argumentů metodě pracovního procesu. Třída zveřejňuje událost, ke které je pracovní <xref:System.ComponentModel.BackgroundWorker.DoWork> vlákno připojeno prostřednictvím obslužné rutiny události. <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker>  
  
 Obslužná rutina <xref:System.ComponentModel.DoWorkEventArgs> <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> události přebírá parametr, který má vlastnost. <xref:System.ComponentModel.BackgroundWorker.DoWork> Tato vlastnost přijímá parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a lze jej předat metodě pracovního procesu, která bude volána <xref:System.ComponentModel.BackgroundWorker.DoWork> v obslužné rutině události. Následující příklad ukazuje, jak přiřadit výsledek z volané `ComputeFibonacci`metody Worker. Je součástí většího příkladu, který můžete najít v [tématu Postup: Implementujte formulář, který používá operaci](how-to-implement-a-form-that-uses-a-background-operation.md)na pozadí.  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Další informace o použití obslužných rutin událostí naleznete v tématu [events](../../../standard/events/index.md).  
  
> [!CAUTION]
> Při použití multithreadingu s více vlákny můžete vystavit hodně závažných a složitých chyb. Před implementací jakéhokoli řešení, které používá multithreading, si Projděte [osvědčené postupy spravovaného vlákna](../../../standard/threading/managed-threading-best-practices.md) .  
  
 Další informace o použití <xref:System.ComponentModel.BackgroundWorker> třídy naleznete v tématu [How to: Spustí operaci na pozadí](how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Viz také:

- [Spravované podprocesy](../../../standard/threading/index.md)
- [Přehled asynchronních vzorů založených na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
