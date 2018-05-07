---
title: 'Návod: Přiřazování obsahu WPF ve Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: abdeb2e77486d4f94f3d0543d94186168baae31c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>Návod: Přiřazování obsahu WPF ve Windows Forms během návrhu
Tento názorný postup ukazují, jak vyberte typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři. Můžete vybrat všechny typy ovládacích prvků WPF, které jsou součástí projektu.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Typy ovládacích prvků WPF vytvořte.  
  
-   Vyberte ovládacích prvků WPF.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Vytváření typy ovládacích prvků grafického subsystému WPF  
 Po přidání typy ovládacích prvků WPF k projektu, můžete je hostovat v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky.  
  
#### <a name="to-create-wpf-control-types"></a>Chcete-li vytvořit typy ovládacích prvků grafického subsystému WPF  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> projektu k řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána. Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.  
  
4.  Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.  
  
5.  Přidat druhý WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl2.xaml`.  
  
6.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.  
  
7.  Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu 2**.  
  
 **Poznámka:** obecně by měl hostitel sofistikovanější obsahu WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Řízení tady je použita pouze pro ilustraci.  
  
1.  Sestavte projekt.  
  
## <a name="selecting-wpf-controls"></a>Výběr ovládacích prvků grafického subsystému WPF  
 Můžete přiřadit různé obsahu WPF <xref:System.Windows.Forms.Integration.ElementHost> řízení, které je již hostitelem obsahu.  
  
#### <a name="to-select-wpf-controls"></a>Chcete-li vybrat ovládacích prvků WPF  
  
1.  Otevřete `Form1` v Návrháři formulářů.  
  
2.  V **sada nástrojů**, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` na formuláři.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3.  V panelu inteligentních značek pro `elementHost1`, otevřete **vyberte hostované obsahu** rozevíracího seznamu.  
  
4.  Vyberte **UserControl2** z rozevíracího seznamu.  
  
     `elementHost1` Řízení nyní hostitelem instance `UserControl2` typu.  
  
5.  V **vlastnosti** okně potvrďte, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl2**.  
  
6.  Z **sada nástrojů**v **WPF interoperabilita** skupiny, přetáhněte <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek na formuláři.  
  
     Výchozí název pro nový ovládací prvek je `elementHost2`.  
  
7.  V panelu inteligentních značek pro `elementHost2`, otevřete **vyberte hostované obsahu** rozevíracího seznamu.  
  
8.  Vyberte **UserControl1** z rozevíracího seznamu.  
  
9. `elementHost2` Řízení nyní hostitelem instance `UserControl1` typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
