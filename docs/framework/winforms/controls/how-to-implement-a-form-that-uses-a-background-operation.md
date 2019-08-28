---
title: 'Postupy: Implementace formuláře, který používá operaci na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046191"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Postupy: Implementace formuláře, který používá operaci na pozadí
Následující vzorový program vytvoří formulář, který vypočítá Fibonacci čísla. Výpočet se spustí ve vlákně, které je oddělené od vlákna uživatelského rozhraní, takže uživatelské rozhraní bude během výpočtu pokračovat bez prodlev.  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  
  
 Viz [také návod: Implementace formuláře, který používá operaci](walkthrough-implementing-a-form-that-uses-a-background-operation.md)na pozadí.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="robust-programming"></a>Robustní programování  
  
> [!CAUTION]
> Při použití multithreadingu s více vlákny můžete vystavit hodně závažných a složitých chyb. Před implementací jakéhokoli řešení, které používá multithreading, si Projděte [osvědčené postupy spravovaného vlákna](../../../standard/threading/managed-threading-best-practices.md) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Přehled asynchronních vzorů založených na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Doporučené postupy dělení na spravovaná vlákna](../../../standard/threading/managed-threading-best-practices.md)
