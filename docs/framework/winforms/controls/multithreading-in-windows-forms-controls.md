---
title: "Podpora více vláken v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c4651ca9707dcf0fac2edea0f004275cfcf18cf2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a>Podpora více vláken v ovládacích prvcích Windows Forms
V mnoha aplikacích můžete nastavit vaše uživatelské rozhraní (UI), které jsou rychlejšího provedením časově náročná operace na jiné vlákno. Počet nástroje jsou k dispozici pro multithreading vaše ovládací prvky Windows Forms, včetně <xref:System.Threading> obor názvů, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda a `BackgroundWorker` součásti.  
  
> [!NOTE]
>  `BackgroundWorker` Součást nahrazuje a přidá funkce <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda; však tyto se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [BackgroundWorker – přehled komponenty](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: volání vláken ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Ukazuje, jak provádět volání bezpečného přístupu do Windows Forms – ovládací prvky.  
  
 [Postupy: použití vlákna na pozadí k vyhledávání souborů](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Ukazuje, jak používat <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody na hledání souborů asynchronně.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumenty komponentu, který zapouzdřuje pracovní vlákno pro asynchronní operace.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Obsahuje informace o tom, jak asynchronní načítání zvuku.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumenty jak načíst obrázek asynchronně.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Ukazuje, jak provést časově náročná operace s <xref:System.ComponentModel.BackgroundWorker> součásti.  
  
 [BackgroundWorker – přehled komponenty](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Obsahuje témata, která popisují způsob použití <xref:System.ComponentModel.BackgroundWorker> součásti pro asynchronní operace.
