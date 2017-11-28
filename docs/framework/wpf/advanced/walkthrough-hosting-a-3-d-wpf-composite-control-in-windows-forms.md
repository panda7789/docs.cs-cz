---
title: "Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms
Tento návod ukazuje, jak můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složené řízení a hostitele v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a formulářů pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek.  
  
 V tomto návodu budete implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> obsahující dva podřízené ovládací prvky. <xref:System.Windows.Controls.UserControl> Zobrazí trojrozměrné kuželový (3D). Vykreslování 3D objekty je mnohem snazší s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto má smysl hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> třídy za účelem vytvoření 3D grafiky ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
-   Vytvoření projektu hostitele Windows Forms.  
  
-   Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [hostování 3D WPF složeného ovládacího prvku Windows Forms ukázka](http://go.microsoft.com/fwlink/?LinkID=160001).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>Vytváření UserControl  
  
#### <a name="to-create-the-usercontrol"></a>Chcete-li vytvořit UserControl  
  
1.  Vytvoření projektu knihovny ovládacích prvků WPF uživatele s názvem `HostingWpfUserControlInWf`.  
  
2.  Otevřete UserControl1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
3.  Generovaného kódu nahraďte následujícím kódem.  
  
     Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> obsahující dva podřízené ovládací prvky. První podřízený ovládací prvek je <xref:System.Windows.Controls.Label?displayProperty=nameWithType> řízení; druhý je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazí 3D kuželový.  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>Vytváření projektu hostitele Windows Forms  
  
#### <a name="to-create-the-host-project"></a>Vytvoření projektu hostitele  
  
1.  Přidejte projekt aplikace Windows s názvem `WpfUserControlHost` k řešení. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  V Průzkumníku řešení přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.  
  
3.  Přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  Přidat odkaz na `HostingWpfUserControlInWf` projektu.  
  
5.  V Průzkumníku řešení, nastavte `WpfUserControlHost` projekt jako spouštěný projekt.  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>Hostování Windows Presentation Foundation UserControl  
  
#### <a name="to-host-the-usercontrol"></a>K hostování UserControl  
  
1.  V Návrháři formulářů Windows otevřete Form1.  
  
2.  V okně vlastností klikněte na tlačítko **události**a dvakrát <xref:System.Windows.Forms.Form.Load> událostí k vytvoření obslužné rutiny události.  
  
     Editor kódu otevře nově vygenerovaný `Form1_Load` obslužné rutiny události.  
  
3.  Nahraďte kód v Form1.cs následujícím kódem.  
  
     `Form1_Load` Obslužné rutiny události vytvoří instanci `UserControl1` a přidá itto <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku kolekce podřízených ovládacích prvků. <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Hostování složeného ovládacího prvku WPF ve Windows Forms – ukázka](http://go.microsoft.com/fwlink/?LinkID=160001)
