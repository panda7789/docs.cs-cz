---
title: "Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c772f547dc87af6618b92603ed1e709efc511b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně
Můžete vyřešit problémy vzájemná funkční spolupráce COM zobrazení formuláře v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, které můžete vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.  
  
 Chcete-li pracovní formuláře Windows správně z klientské aplikace modelu COM, musíte spustit formuláře ve smyčce zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows. Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Zobrazení jednotlivých formulářů Windows na samostatné vlákno.  
  
 Je rozsáhlá podpora pro tuto funkci v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Viz také [návod: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zobrazit formulář na samostatné vlákno a volání <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda zahájíte zprávy odeslané Windows Forms v daném vláknu. Chcete-li použít tuto metodu, musí zařazování žádné volání do formuláře z nespravované aplikace pomocí <xref:System.Windows.Forms.Control.Invoke%2A> metoda.  
  
 Tento postup vyžaduje, že každá instance ve tvaru, který spouští ve vlastním vlákně pomocí vlastní zpráva smyčky. Nemůže mít více než jeden smyčku zpráva spuštěna na vlákno. Proto nelze změnit smyčce zpráv klientské aplikace. Však můžete upravit [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti spustit nové vlákno, která používá vlastní zpráva smyčky.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Kompilace `COMForm`, `Form1`, a `FormManager` názvem typy v sestavení `COMWinform.dll`. Registrace sestavení pro zprostředkovatel komunikace s objekty modelu COM pomocí jedné z metod popsaných v [balení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Teď můžete použít sestavení a jeho odpovídající soubor typu knihovny (.tlb) v nespravovaných aplikacích. Například můžete použít knihovny typů jako odkaz v projektu jazyka Visual Basic 6.0 spustitelný soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vystavení součástí .NET Framework do modelu COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Balení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrace sestavení modelu COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Windows Forms a přehled nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
