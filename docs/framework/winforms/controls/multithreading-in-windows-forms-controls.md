---
title: Podpora více vláken v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012721"
---
# <a name="multithreading-in-windows-forms-controls"></a>Podpora více vláken v ovládacích prvcích Windows Forms
V mnoha aplikacích můžete provést uživatelského rozhraní (UI), které jsou rychlejší reakce provedením časově náročných operací v jiném vlákně. Různé nástroje jsou k dispozici pro multithreading své ovládací prvky Windows Forms, včetně <xref:System.Threading> obor názvů, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody a `BackgroundWorker` komponenty.  
  
> [!NOTE]
>  `BackgroundWorker` Komponenty nahradí a přidá funkce, které <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda; ale ty se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [přehled komponenty BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Bezpečné pro vlákna volání ovládacích prvků Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Ukazuje, jak provádět volání bezpečným pro vlákno pro ovládací prvky Windows Forms.  
  
 [Postupy: Použití vlákna na pozadí k vyhledávání souborů](how-to-use-a-background-thread-to-search-for-files.md)  
 Ukazuje způsob použití <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody k vyhledání souborů asynchronně.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumenty komponenty, která zapouzdřuje pracovní vlákno pro asynchronní operace.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Popisem asynchronní načítání zvuku.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumenty o načtení obrázku asynchronně.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)  
 Ukazuje, jak provádět časově náročná operace s <xref:System.ComponentModel.BackgroundWorker> komponenty.  
  
 [Přehled komponenty BackgroundWorker](backgroundworker-component-overview.md)  
 Obsahuje témata, které popisují způsob použití <xref:System.ComponentModel.BackgroundWorker> komponenty pro asynchronní operace.
