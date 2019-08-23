---
title: Podpora více vláken v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952685"
---
# <a name="multithreading-in-windows-forms-controls"></a>Podpora více vláken v ovládacích prvcích Windows Forms
V mnoha aplikacích můžete své uživatelské rozhraní (UI) lépe reagovat tím, že provádíte časově náročné operace v jiném vlákně. K dispozici je řada nástrojů pro multithreading model Windows Forms ovládacích prvků, včetně <xref:System.Threading> oboru názvů <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> , metody a `BackgroundWorker` součásti.  
  
> [!NOTE]
> Komponenta nahrazuje a přidává funkce <xref:System.Threading> do oboru názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody; nicméně jsou zachovány pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. `BackgroundWorker` Další informace najdete v tématu [Přehled komponent BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Provádění volání bezpečných pro přístup z více vláken na ovládací prvky model Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Ukazuje, jak učinit volání bezpečná pro přístup z více vláken na ovládací prvky model Windows Forms.  
  
 [Postupy: Použití vlákna na pozadí k hledání souborů](how-to-use-a-background-thread-to-search-for-files.md)  
 Ukazuje, jak použít <xref:System.Threading> obor názvů <xref:System.Windows.Forms.Control.BeginInvoke%2A> a metodu k asynchronnímu hledání souborů.  
  
## <a name="reference"></a>Reference  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumentuje komponentu, která zapouzdřuje pracovní vlákno pro asynchronní operace.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Dokumentuje asynchronní načítání zvuku.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumentuje asynchronní načtení obrázku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)  
 Ukazuje, jak provést časově náročnou operaci s <xref:System.ComponentModel.BackgroundWorker> komponentou.  
  
 [Přehled komponenty BackgroundWorker](backgroundworker-component-overview.md)  
 Poskytuje témata, která popisují, jak používat <xref:System.ComponentModel.BackgroundWorker> komponentu pro asynchronní operace.
