---
title: "Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f01fc82be38f7c5acb02c28960785e97a782909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog
Modelu COM (Component Object) interoperabilita problémy můžete vyřešit zobrazení formuláře Windows v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, která je vytvořena pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.  
  
 Chcete-li formuláře fungování z klientské aplikace modelu COM, musíte ji provést ve smyčce zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows;  
  
-   Zobrazení jednotlivých formulářů Windows na samostatné vlákno. Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Postup  
 Pomocí <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda může být nejjednodušší způsob, jak zobrazit formulář na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zpráva smyčky, protože všechny přístupů, vyžaduje minimálně kód pro implementaci.  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Metoda pozastaví nespravovaná aplikace zpráva smyčky a zobrazí formulář jako dialogové okno. Protože byla pozastavena hostitelskou aplikaci zpráva smyčky, <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda vytvoří novou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zpráva smyčky ke zpracování zpráv formuláře.  
  
 Nevýhodou použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda je, že formulář otevřou jako modální dialogové okno. Toto chování bloků žádné uživatelské rozhraní (UI) v volající aplikace při otevřeném formuláři Windows. Při ukončení formuláře, uživatelem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] smyčky zavře a starší aplikace zpráva smyčky spustí znovu zpráv.  
  
 Můžete vytvořit knihovny tříd ve Windows Forms, který má metodu pro zobrazení formuláře a následně vytvořit knihovny tříd pro zprostředkovatel komunikace s objekty COM. Tento soubor knihovny DLL z Visual Basic 6.0 nebo Microsoft Foundation třídy (MFC) můžete použít, a pomocí kteréhokoli z těchto prostředí můžete volat <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Pro podporu zprostředkovatele komunikace s objekty COM zobrazením windows form pomocí metody ShowDialog  
  
-   Nahraďte všechna volání <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> metoda pomocí volání <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda v vaší [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti.  
  
## <a name="see-also"></a>Viz také  
 [Vystavení součástí .NET Framework do modelu COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
