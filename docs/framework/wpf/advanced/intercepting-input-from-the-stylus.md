---
title: "Přijetí vstupu z pera"
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
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5fde62e2e1ab17b26c91051f68b7d4225450c60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="intercepting-input-from-the-stylus"></a>Přijetí vstupu z pera
<xref:System.Windows.Input.StylusPlugIns> Architektura poskytuje mechanismus pro implementaci nízké úrovně řízení přes <xref:System.Windows.Input.Stylus> vstup a vytvoření digitálního <xref:System.Windows.Ink.Stroke> objekty. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Třída poskytuje mechanismus pro implementaci vlastního chování a použijte ho pro datový proud dat pocházejících z pera zařízení k zajištění optimálního výkonu.  
  
 Toto téma obsahuje následující témata:  
  
-   [Architektura](#Architecture)  
  
-   [Implementace modulů plug-in pera](#ImplementingStylusPlugins)  
  
-   [Přidávání do InkCanvas vaše modulu Plug-in](#AddingYourPluginToAnInkCanvas)  
  
-   [Uzavření](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Je vývoj [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) rozhraní API, které jsou popsané v [přístup k a manipulace s vstup pera](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)v [Microsoft Windows XP Tablet PC Edition softwaru Development Kit 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Každý <xref:System.Windows.UIElement> má <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Můžete přidat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> na element <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost k manipulaci s <xref:System.Windows.Input.StylusPoint> data, protože byla vygenerována. <xref:System.Windows.Input.StylusPoint>data se skládá ze všech vlastnostech podporovaných zprostředkovatelem digitizéru systému, včetně <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> bodu dat, a také <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> data.  
  
 Vaše <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty jsou vloženy přímo do datového proudu dat pocházejících z <xref:System.Windows.Input.Stylus> zařízení, když přidáte <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> k <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost. Pořadí, ve kterém jsou moduly plug-in přidány do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce určuje pořadí, ve kterém bude přijímat <xref:System.Windows.Input.StylusPoint> data. Například pokud přidáte modul plug-in filtr, který omezuje vstup pro konkrétní oblasti a pak přidat modul plug-in, který rozpoznává gesta, ve kterém byla zapsána, modul plug-in, který rozpoznává gesta obdrží filtrované <xref:System.Windows.Input.StylusPoint> data.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementace modulů plug-in pera  
 Pokud chcete implementovat modul plug-in, odvození třídy z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Tato třída je použité o datový proud, jak jsou doručovány z <xref:System.Windows.Input.Stylus>. V této třídě můžete upravit hodnoty <xref:System.Windows.Input.StylusPoint> data.  
  
> [!CAUTION]
>  Pokud <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vyvolá nebo způsobí výjimku, aplikace nebude zavřete. Měli byste důkladně otestovat ovládací prvky, které využívají <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a používat jenom ovládacího prvku, pokud jste si jisti, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nebude vyvolat výjimku.  
  
 Následující příklad ukazuje, modul plug-in, který omezuje vstup pera změnou <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> hodnoty ve <xref:System.Windows.Input.StylusPoint> pocházejí data jak <xref:System.Windows.Input.Stylus> zařízení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Přidávání do InkCanvas vaše modulu Plug-in  
 Nejjednodušší způsob, jak používat vaše vlastní modul plug-in je implementovat třídu odvozenou od InkCanvas a přidejte ho do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost.  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> který filtruje rukopisu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Pokud přidáte `FilterInkCanvas` aplikaci a spustit, si všimnete, že není rukopisu s omezeným přístupem v oblasti až poté, co uživatel vykoná tah. Důvodem je, že <xref:System.Windows.Controls.InkCanvas> má <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a je již členem <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> jste přidali do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce obdrží <xref:System.Windows.Input.StylusPoint> dat po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> přijímá data. V důsledku toho <xref:System.Windows.Input.StylusPoint> data se nebudou filtrovat až poté, co uživatel zruší pera na konec tahu. Chcete-li filtrovat rukopisu jako uživatel nevykresluje ho, je nutné vložit `FilterPlugin` před <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Následující kód C# ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> který filtruje rukopisu při kreslení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Odvozením vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> třídy a jejich vložení do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcí, může výrazně zvýšit chování digitálního pera. Máte přístup k <xref:System.Windows.Input.StylusPoint> data, jako je generován, budete moci přizpůsobit <xref:System.Windows.Input.Stylus> vstupní. Vzhledem k tomu, že máte takový nízké úrovně přístup k <xref:System.Windows.Input.StylusPoint> data, rozpoznávání rukopisu a vykreslování s optimální výkon můžete implementovat pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé zpracování rukopisu](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Přístup k informacím a manipulace s vstup pomocí pera](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
