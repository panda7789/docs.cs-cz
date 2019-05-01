---
title: BackgroundWorker – komponenta
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
ms.openlocfilehash: 0baf54d27cf33eef7e4df7019ee98b42eba40205
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011798"
---
# <a name="backgroundworker-component"></a>BackgroundWorker – komponenta
`BackgroundWorker` Komponenta povoluje formuláře nebo ovládacího prvku na spuštění operace asynchronně.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled komponenty BackgroundWorker](backgroundworker-component-overview.md)  
 Popisuje `BackgroundWorker` součásti, která vám dává možnost provádět časově náročná operace asynchronně ("na pozadí"), ve vlákně, která se liší od hlavního vlákna uživatelského rozhraní vaší aplikace.  
  
 [Návod: Spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md)  
 Popisuje způsob použití `BackgroundWorker` součásti v návrháři pro spuštění časově náročná operace na samostatném vlákně.  
  
 [Postupy: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)  
 Popisuje způsob použití `BackgroundWorker` komponentu pro spuštění časově náročná operace na samostatném vlákně.  
  
 [Návod: Implementace formuláře, který používá operaci na pozadí](walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 Vytvoří aplikaci s použitím návrháře, která provádí asynchronně matematických výpočtů.  
  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)  
 Vytvoří aplikaci, která provádí asynchronně matematických výpočtů.  
  
 [Postupy: Stahování souboru na pozadí](how-to-download-a-file-in-the-background.md)  
 Popisuje způsob použití `BackgroundWorker` součásti ke stažení souboru na samostatném vlákně.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ComponentModel.BackgroundWorker>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 Popisuje typ, který obsahuje data pro <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí.  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 Popisuje typ, který obsahuje data pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled asynchronních vzorů založených na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Popisuje, jak asynchronního zpracování zpřístupní výhody vícevláknové aplikace při skrytí mnoho složitých problémů vyplývající vícevláknový návrhu.
