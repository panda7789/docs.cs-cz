---
title: Používání ovládacích prvků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747612"
---
# <a name="using-wpf-controls"></a>Používání ovládacích prvků WPF
Ovládací prvky Windows Presentation Foundation (WPF) můžete použít ve svých aplikacích pomocí formulářů Windows. I když jsou dvě technologie jiné zobrazení, jejich vzájemnou spolupráci plynule.  
  
 Návrhář formulářů Windows poskytuje vizuální návrhové prostředí pro hostování ovládacích prvků Windows Presentation Foundation. Ovládací prvek WPF je hostitelem speciální ovládacího prvku Windows Forms, který je pojmenován <xref:System.Windows.Forms.Integration.ElementHost>. Tento ovládací prvek umožňuje ovládacího prvku WPF se účastnit rozložení formuláře a přijímat zprávy klávesnice a myši. V době návrhu, můžete uspořádat <xref:System.Windows.Forms.Integration.ElementHost> řídit stejně jako libovolný ovládací prvek Windows Forms.  
  
 Můžete také použít ovládací prvky Windows Forms ve svých aplikacích založeného na WPF. Další informace najdete v tématu [návrh XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Kopírování a vložení ovládacího prvku ElementHost během návrhu](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation ve formuláři Windows.  
  
 [Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje způsob použití funkcí rozložení Windows Forms, jako je například ukotvení a zarovnávacích čar, k uspořádání ovládacích prvků Windows Presentation Foundation.
  
 [Návod: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation pro použití ve svých aplikacích pomocí formulářů Windows.
  
 [Návod: Přiřazení obsahu WPF ve Windows Forms v době návrhu](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation, který chcete zobrazit ve formuláři.  
  
 [Návod: Určení stylu obsahu WPF](walkthrough-styling-wpf-content.md)  
 Zobrazuje pracovní postupy mezi návrháři formulářů Windows a [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pro aplikování stylů pro ovládací prvky Windows Presentation Foundation.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Popisuje třídy, která vám pomůže hostitelských ovládacích prvků Windows Presentation Foundation ve svých aplikacích pomocí formulářů Windows.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Popisuje třídy, která vám pomůže hostitelské ovládací prvky Windows Forms v aplikaci založené na Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)  
 Popisuje interoperabilitu mezi Windows Presentation Foundation a Windows Forms technologií.  
  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 Popisuje postup návrhu ovládacích prvků Windows Presentation Foundation v sadě Visual Studio.
