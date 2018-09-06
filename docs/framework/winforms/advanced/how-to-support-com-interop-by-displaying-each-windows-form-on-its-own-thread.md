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
ms.openlocfilehash: d0d8dfd4a19b31be790d2643847396d136098278
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877515"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně
Vyřešíte problémy vzájemná funkční spolupráce modelu COM zobrazením formuláře ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] smyčky zpráv, které můžete vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Chcete-li pracovní formulář Windows správně z klientské aplikace modelu COM, musíte spustit formuláře na smyčku zpráv Windows Forms. K tomuto účelu použijte jednu z následujících postupů:  
  
-   Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows. Další informace najdete v tématu [postupy: podpora spolupráci s COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Každý formulář Windows pro zobrazení na samostatném vlákně.  
  
 Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.  
  
 Viz také [návod: podpora komunikace s objekty COM zobrazení každý formulář Windows na jeho vlastní vlákně](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak formulář pro zobrazení v samostatném vlákně a volání <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodu spustit pumpu zpráv Windows Forms v daném vláknu. Chcete-li tuto metodu použijte, musí zařaďte všechna volání do formuláře z nespravovaných aplikací s použitím <xref:System.Windows.Forms.Control.Invoke%2A> metody.  
  
 Tento přístup vyžaduje, že každá instance formuláře je spuštěna ve vlastním vlákně s použitím vlastní smyčky zpráv. Nemůžete mít více než jeden smyčky zpráv spuštěná na vlákno. Proto nelze změnit smyčky zpráv klientská aplikace. Však můžete změnit [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti spustit nové vlákno, která používá vlastní smyčku zpráv.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Kompilace `COMForm`, `Form1`, a `FormManager` typů do sestavení volá `COMWinform.dll`. Registrace sestavení zprostředkovatele komunikace s objekty modelu COM pomocí jedné z metod popsaných v [zabalení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Teď můžete použít sestavení a jeho odpovídající soubor knihovny (.tlb) typů v nespravované aplikace. Například můžete použít knihovnu typů jako odkaz v projektu jazyka Visual Basic 6.0 spustitelný soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Zabalení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrování sestav pomocí modelu COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Přehled modelu Windows Forms a nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
