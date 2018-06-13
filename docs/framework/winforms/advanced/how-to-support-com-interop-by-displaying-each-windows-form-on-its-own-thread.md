---
title: 'Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: c78bcc8d784fc481af2449f2d81cfde42891e7fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522886"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně
Můžete vyřešit problémy vzájemná funkční spolupráce COM zobrazení formuláře v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, které můžete vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.  
  
 Chcete-li pracovní formuláře Windows správně z klientské aplikace modelu COM, musíte spustit formuláře ve smyčce zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows. Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Zobrazení jednotlivých formulářů Windows na samostatné vlákno.  
  
 Rozsáhlá podpora pro tuto funkci v sadě Visual Studio není k dispozici.  
  
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
 [Vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Zabalení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrování sestav pomocí modelu COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Přehled modelu Windows Forms a nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
