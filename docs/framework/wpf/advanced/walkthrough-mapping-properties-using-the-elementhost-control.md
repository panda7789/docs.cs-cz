---
title: "Návod: Mapování vlastností použitím ovládacího prvku ElementHost"
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
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dae954012d15431d2019d3d9cbe61747a8646d4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Návod: Mapování vlastností použitím ovládacího prvku ElementHost
Tento postup vám ukáže, jak používat <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Definování nového mapování vlastností.  
  
-   Odebrání výchozí vlastnost mapování.  
  
-   Rozšíření výchozí vlastnost mapování.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [mapování vlastností pomocí Ukázka ovládacího prvku ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).  
  
 Po dokončení bude možné mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti k odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti hostované elementu.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projekt aplikace s názvem `PropertyMappingWithElementHost`. Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  V Průzkumníku řešení přidáte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  Zkopírujte následující kód do horní části `Form1` souboru kódu.  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Otevřete `Form1` v Návrháři formulářů. Klikněte dvakrát na formuláři pro přidání obslužné rutiny události pro <xref:System.Windows.Forms.Form.Load> událostí.  
  
5.  Vraťte se na správce systému Windows Forms a přidání obslužné rutiny události pro daný formulář <xref:System.Windows.Forms.Control.Resize> události. Další informace najdete v tématu [postupy: vytvoření události obslužné rutiny pomocí návrháře](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
6.  Deklarace <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a>Definování nového mapování vlastností  
 <xref:System.Windows.Forms.Integration.ElementHost> Řízení poskytuje několik výchozí mapování vlastností. Přidat nové mapování vlastností voláním <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-define-new-property-mappings"></a>Chcete-li definovat nové mapování vlastností  
  
1.  Zkopírujte následující kód do definice pro `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Margin%2A> vlastnost.  
  
     `OnMarginChange` Metoda přeloží <xref:System.Windows.Forms.Control.Margin%2A> vlastnost, která má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.  
  
2.  Zkopírujte následující kód do definice pro `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Region%2A> vlastnost.  
  
     `OnRegionChange` Metoda přeloží <xref:System.Windows.Forms.Control.Region%2A> vlastnost, která má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> vlastnost.  
  
     `Form1_Resize` Metoda zpracovává formuláře <xref:System.Windows.Forms.Control.Resize> událostí a velikosti oblast ořezu podle hostované elementu.  
  
## <a name="removing-a-default-property-mapping"></a>Odebrání výchozí vlastnost mapování  
 Odebrání výchozí vlastnost mapování voláním <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Chcete-li odebrat mapování výchozí vlastnosti  
  
-   Zkopírujte následující kód do definice pro `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.  
  
## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozí vlastnost mapování  
 Můžete použít výchozí vlastnost mapování a také ho rozšířit pomocí vlastního mapování.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Chcete-li rozšířit výchozí vlastnost mapování  
  
-   Zkopírujte následující kód do definice pro `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping` Metoda přidá převaděče vlastní vlastnost ke stávající <xref:System.Windows.Forms.Control.BackColor%2A> mapování vlastností.  
  
     `OnBackColorChange` Metoda přiřadí konkrétní image do ovládacího prvku hostované <xref:System.Windows.Controls.Control.Background%2A> vlastnost. `OnBackColorChange` Metoda je volána, pokud je použita výchozí vlastnost mapování.  
  
## <a name="initializing-your-property-mappings"></a>Inicializace mapování vlastností  
  
#### <a name="to-initialize-your-property-mappings"></a>K chybě při inicializaci mapování vlastností  
  
1.  Zkopírujte následující kód do definice pro `Form1` třídy.  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load` Metoda zpracovává <xref:System.Windows.Forms.Form.Load> událostí a provede následující inicializace.  
  
    -   Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.  
  
    -   Volá metody, které jste definovali dříve v tomto návodu nastavit mapování vlastností.  
  
    -   Přiřadí počáteční hodnoty pro vlastnosti namapované.  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
