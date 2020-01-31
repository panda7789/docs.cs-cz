---
title: Multithreading v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742140"
---
# <a name="multithreading-in-windows-forms-controls"></a>Podpora více vláken v ovládacích prvcích Windows Forms
V mnoha aplikacích můžete své uživatelské rozhraní (UI) lépe reagovat tím, že provádíte časově náročné operace v jiném vlákně. K dispozici je řada nástrojů pro multithreading model Windows Forms ovládacích prvků, včetně oboru názvů <xref:System.Threading>, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody a součásti `BackgroundWorker`.  
  
> [!NOTE]
> Komponenta `BackgroundWorker` nahrazuje a přidává funkce do oboru názvů <xref:System.Threading> a do metody <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>; jsou ale zachovaná pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace najdete v tématu [Přehled komponent BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání (bezpečná pro přístup z více vláken) ovládacích prvků Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Ukazuje, jak učinit volání bezpečná pro přístup z více vláken na ovládací prvky model Windows Forms.  
  
 [Postupy: Použití vlákna na pozadí k vyhledávání souborů](how-to-use-a-background-thread-to-search-for-files.md)  
 Ukazuje, jak použít <xref:System.Threading> obor názvů a metodu <xref:System.Windows.Forms.Control.BeginInvoke%2A> pro asynchronní hledání souborů.  
  
## <a name="reference"></a>Odkaz  
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
 Poskytuje témata, které popisují, jak používat součást <xref:System.ComponentModel.BackgroundWorker> pro asynchronní operace.
