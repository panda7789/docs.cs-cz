---
title: Nespravované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746367"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms a nespravované aplikace
Model Windows Forms aplikace a ovládací prvky mohou spolupracovat s nespravovanými aplikacemi, s některými upozorněními. V následujících částech najdete popis scénářů a konfigurací, které model Windows Forms aplikace a ovládací prvky podporují, a ty, které nepodporují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled modelu Windows Forms a nespravovaných aplikací](windows-forms-and-unmanaged-applications-overview.md)  
 Nabízí Obecné informace o použití a implementaci model Windows Formsch ovládacích prvků, které fungují s nespravovanými aplikacemi.  
  
 [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)  
 Obsahuje příklad kódu, který ukazuje, jak použít metodu <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> ke spuštění formuláře Windows v nespravované aplikaci.  
  
 [Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Obsahuje příklad kódu, který ukazuje, jak spustit formulář Windows ve vlastním vlákně.  
  
 Viz také [Návod: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Slouží k vytvoření samostatného vlákna pro formulář Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Spustí smyčku zpráv pro vlákno.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Zařazování volání z nespravované aplikace do formuláře.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vystavení komponent architektury .NET Framework pro COM](../../interop/exposing-dotnet-components-to-com.md)  
 Obsahuje obecné informace o tom, jak používat typy .NET Framework v nespravovaných aplikacích.
