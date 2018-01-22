---
title: "Návod: Mapování vlastností použitím elementu WindowsFormsHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaab6b7724a1e6145dfce3998ccf75904df01802
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Návod: Mapování vlastností použitím elementu WindowsFormsHost
Tento postup vám ukáže, jak používat <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Definování rozložení aplikace.  
  
-   Definování nového mapování vlastností.  
  
-   Odebrání výchozí vlastnost mapování.  
  
-   Nahrazení výchozí vlastnost mapování.  
  
-   Rozšíření výchozí vlastnost mapování.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [mapování vlastností pomocí ukázka prvky WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).  
  
 Po dokončení bude možné mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu  
  
1.  Vytvořte projekt aplikace WPF s názvem `PropertyMappingWithWfhSample`.  
  
2.  V Průzkumníku řešení přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.  
  
3.  V Průzkumníku řešení přidejte odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
## <a name="defining-the-application-layout"></a>Definování rozložení aplikace  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– Na základě používá aplikace <xref:System.Windows.Forms.Integration.WindowsFormsHost> element hostitele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-define-the-application-layout"></a>Chcete-li definovat rozložení aplikace  
  
1.  Otevřete Window1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Existujícího kódu nahraďte následujícím kódem.  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  Otevřete Window1.xaml.cs v editoru kódu.  
  
4.  V horní části souboru importujte následujících oborů názvů.  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a>Definování nového mapování vlastností  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element poskytuje několik výchozí mapování vlastností. Přidat nové mapování vlastností voláním <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-define-a-new-property-mapping"></a>Chcete-li definovat nové mapování vlastností  
  
-   Zkopírujte následující kód do definice pro `Window1` třídy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     `AddClipMapping` Metoda přidá nové mapování <xref:System.Windows.UIElement.Clip%2A> vlastnost.  
  
     `OnClipChange` Metoda přeloží <xref:System.Windows.UIElement.Clip%2A> vlastnost, která má [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> vlastnost.  
  
     `Window1_SizeChanged` Metoda zpracovává okna <xref:System.Windows.FrameworkElement.SizeChanged> událostí a velikosti oblast ořezu velikosti okna aplikace.  
  
## <a name="removing-a-default-property-mapping"></a>Odebrání výchozí vlastnost mapování  
 Odebrání výchozí vlastnost mapování voláním <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Chcete-li odebrat mapování výchozí vlastnosti  
  
-   Zkopírujte následující kód do definice pro `Window1` třídy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     `RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost.  
  
## <a name="replacing-a-default-property-mapping"></a>Nahrazení výchozí vlastnost mapování  
 Nahraďte odebráním výchozí mapování a volání výchozí vlastnosti mapování <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-replace-a-default-property-mapping"></a>Chcete-li nahradit výchozí vlastnost mapování  
  
-   Zkopírujte následující kód do definice pro `Window1` třídy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     `ReplaceFlowDirectionMapping` Metoda nahrazuje výchozí mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost.  
  
     `OnFlowDirectionChange` Metoda přeloží <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost, která má [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost.  
  
     `cb_CheckedChanged` Metoda zpracovává <xref:System.Windows.Forms.CheckBox.CheckedChanged> událostí na <xref:System.Windows.Forms.CheckBox> ovládacího prvku. Přiřadí <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost podle hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost  
  
## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozí vlastnost mapování  
 Můžete použít výchozí vlastnost mapování a také ho rozšířit pomocí vlastního mapování.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Chcete-li rozšířit výchozí vlastnost mapování  
  
-   Zkopírujte následující kód do definice pro `Window1` třídy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     `ExtendBackgroundMapping` Metoda přidá převaděče vlastní vlastnost ke stávající <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.  
  
     `OnBackgroundChange` Metoda přiřadí konkrétní image do ovládacího prvku hostované <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost. `OnBackgroundChange` Metoda je volána, pokud je použita výchozí vlastnost mapování.  
  
## <a name="initializing-your-property-mappings"></a>Inicializace mapování vlastností  
 Nastavit mapování vlastností voláním výše uvedené postupy v <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  
  
#### <a name="to-initialize-your-property-mappings"></a>K chybě při inicializaci mapování vlastností  
  
1.  Zkopírujte následující kód do definice pro `Window1` třídy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     `WindowLoaded` Metoda zpracovává <xref:System.Windows.FrameworkElement.Loaded> událostí a provede následující inicializace.  
  
    -   Vytvoří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> ovládacího prvku.  
  
    -   Volá metody, které jste definovali dříve v tomto návodu nastavit mapování vlastností.  
  
    -   Přiřadí počáteční hodnoty pro vlastnosti namapované.  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Klikněte na zaškrtávací políčko zobrazíte účinku <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapování. Po kliknutí na tlačítko zaškrtnutí políčka, rozložení obrátí její orientace zleva doprava.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
