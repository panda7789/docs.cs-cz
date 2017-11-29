---
title: "Windows Forms a nespravované aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8166ab6a69ce9a774e83e6dbc7278a41805f7a83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms a nespravované aplikace
Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravovaných aplikací se některých aspektů. Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Windows Forms a přehled nespravovaných aplikací](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Poskytuje obecné informace o tom, jak použít a implementovat ovládací prvky Windows Forms, které pracují s nespravované aplikace.  
  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Poskytuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro spuštění Windows Form v nespravované aplikaci.  
  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
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
 [Vystavení součástí .NET Framework do modelu COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.
