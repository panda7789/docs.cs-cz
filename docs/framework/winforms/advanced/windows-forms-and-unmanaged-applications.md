---
title: Windows Forms a nespravované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: c51645fb64f512b5974000f89e8e98f884a7381d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526198"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms a nespravované aplikace
Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravovaných aplikací se některých aspektů. Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu Windows Forms a nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Poskytuje obecné informace o tom, jak použít a implementovat ovládací prvky Windows Forms, které pracují s nespravované aplikace.  
  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Poskytuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro spuštění Windows Form v nespravované aplikaci.  
  
 [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Poskytuje příklad kódu, který ukazuje, jak spustit formuláře Windows ve vlastním vlákně.  
  
 Viz také [návod: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Umožňuje vytvořit samostatný podproces pro formuláře systému Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Zahájí cyklus zpráv vlákna.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Zařazuje volání z aplikace bez správy do formuláře.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.
