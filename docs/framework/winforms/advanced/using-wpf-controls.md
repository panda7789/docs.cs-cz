---
title: Používání ovládacích prvků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 8dcf79d449a8f8443774b133904e819dfd925288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-wpf-controls"></a>Používání ovládacích prvků WPF
Ovládací prvky Windows Presentation Foundation (WPF) můžete použít ve svých aplikacích pomocí formulářů Windows. I když jsou tyto dvě technologie jiné zobrazení, budou spolupracovat bez problémů.  
  
 Návrhář formulářů Windows poskytuje prostředí visual návrhu pro hostování ovládacích prvků Windows Presentation Foundation. Ovládací prvek WPF hostován ve speciální ovládacího prvku Windows Forms, který je pojmenován <xref:System.Windows.Forms.Integration.ElementHost>. Tento ovládací prvek umožňuje ovládací prvek WPF zapojit se do rozvržení a aby se zprávy klávesnici a myš. V době návrhu, můžete uspořádat <xref:System.Windows.Forms.Integration.ElementHost> řízení stejně jako libovolný ovládací prvek Windows Forms.  
  
 Windows Forms – ovládací prvky můžete použít také v aplikacích grafického subsystému WPF. Další informace najdete v tématu [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Ukazuje, jak zkopírovat Windows Presentation Foundation ovládací prvek na formuláři Windows.  
  
 [Návod: Uspořádání obsahu WPF v modelu Windows Forms během návrhu](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje, jak funkce rozložení Windows Forms, jako je například ukotvení a zarovnávací čáry, používat k uspořádání ovládacích prvků Windows Presentation Foundation.  
  
 [Návod: Změna vlastností hostovaného prvku WPF během návrhu](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Ukazuje pracovní postup mezi Návrhář formulářů Windows a [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pro změnu vlastností ovládacích prvků WPF.  
  
 [Návod: Vytvoření nového obsahu WPF v modelu Windows Forms během návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje postup vytvoření ovládacího prvku Windows Presentation Foundation pro použití v aplikacích Windows formulářů.  
  
 [Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného modelu Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Ukazuje, jak kopírovat ovládacího prvku Windows Presentation Foundation z jednoho formuláře Windows do jiného.  
  
 [Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation, které chcete zobrazit ve formuláři.  
  
 [Návod: Určení stylu obsahu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Ukazuje pracovní postup mezi Návrhář formulářů Windows a [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] použití styly pro ovládací prvky Windows Presentation Foundation.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Popisuje třídu, která vám pomůže Windows Presentation Foundation hostitelské ovládací prvky v aplikacích Windows formulářů.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Popisuje třídy, který můžete použít k hostitelské ovládací prvky Windows Forms v aplikaci na základě Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Popisuje vzájemná spolupráce mezi technologie Windows Presentation Foundation a systém Windows Forms.  
  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 Popisuje postup návrhu Windows Presentation Foundation ovládacích prvků v sadě Visual Studio.
