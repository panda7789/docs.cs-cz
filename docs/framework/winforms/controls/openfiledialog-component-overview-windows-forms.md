---
title: "OpenFileDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35c947e3efbb9b2e5df775f83ffc6068e49c84e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.OpenFileDialog> součást je předem nakonfigurovaný dialogové okno. Stejná **otevření souboru** dialogové okno vystavené operačního systému Windows. Dědí z <xref:System.Windows.Forms.CommonDialog> třídy.  
  
## <a name="using-this-component"></a>Pomocí této součásti  
 Použijte tuto součást v rámci vaší aplikace systému Windows jako jednoduchým řešením pro výběr souboru místo dialogové okno Vlastní konfigurace. Podle standardní dialogová okna Windows, můžete vytvořit aplikace, jehož základní funkce je dobře obeznámeni uživatele. Nezapomeňte však, že v případě pomocí <xref:System.Windows.Forms.OpenFileDialog> součást, musíte napsat vlastní logiky otevírání souboru.  
  
 Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu. Můžete povolit uživatelům vybrat víc souborů otevřít pomocí <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> vlastnost. Kromě toho můžete použít <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> vlastnosti k určení, pokud se v dialogovém okně zobrazí zaškrtávací políčko jen pro čtení. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Vlastnost určuje, zda je zaškrtnuto políčko jen pro čtení. Nakonec <xref:System.Windows.Forms.FileDialog.Filter%2A> vlastnost nastaví aktuální soubor název řetězec filtru, která určuje možnosti, které se zobrazují v poli "Soubory typu" v dialogovém okně.  
  
 Při jejím přidání do formuláře <xref:System.Windows.Forms.OpenFileDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog – komponenta](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
