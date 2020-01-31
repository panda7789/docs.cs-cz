---
title: 'Postupy: Povolení vizuálních stylů v hybridní aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: dd52313e9100f9c6a1141b53ccc5a23a4b54410a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789923"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Postupy: Povolení vizuálních stylů v hybridní aplikaci
Toto téma ukazuje, jak povolit vizuální styly v ovládacím prvku model Windows Forms hostovaném v aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pokud vaše aplikace volá metodu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, většina ovládacích prvků model Windows Forms bude automaticky používat vizuální styly. Další informace naleznete v tématu [vykreslování ovládacích prvků pomocí vizuálních stylů](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Úplný výpis kódu úloh, které jsou znázorněny v tomto tématu, naleznete v tématu [Povolení vizuálních stylů v ukázce hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Povolení model Windows Formsch vizuálních stylů  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Povolení model Windows Formsch vizuálních stylů  
  
1. Vytvořte projekt aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s názvem `HostingWfWithVisualStyles`.  
  
2. V Průzkumník řešení přidejte odkazy na následující sestavení.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Na panelu nástrojů poklikejte na ikonu <xref:System.Windows.Controls.Grid> a umístěte <xref:System.Windows.Controls.Grid> prvek na návrhovou plochu.  
  
4. V okno Vlastnosti nastavte hodnoty vlastností <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> na **auto**.  
  
5. V zobrazení zobrazení Návrh nebo XAML vyberte <xref:System.Windows.Window>.  
  
6. V okno Vlastnosti klikněte na kartu **události** .  
  
7. Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.
  
8. V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs vložte následující kód pro zpracování události <xref:System.Windows.FrameworkElement.Loaded>.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.  
  
     Ovládací prvek model Windows Forms je vykreslen pomocí vizuálních stylů.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Zákaz model Windows Formsch vizuálních stylů  
 Chcete-li zakázat vizuální styly, jednoduše odeberte volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Zakázání vizuálních stylů model Windows Forms  
  
1. V editoru kódu otevřete MainWindow. XAML. vb nebo MainWindow.xaml.cs.  
  
2. Odkomentujte volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
3. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.  
  
     Ovládací prvek model Windows Forms je vykreslen s výchozím stylem systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Vykreslování ovládacích prvků s vizuálními styly](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
