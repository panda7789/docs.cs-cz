---
title: "Postupy: Vytvoření textu osnovy"
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
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41254d8f93174c896923b1c070e6bf9b5b7c863c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-outlined-text"></a>Postupy: Vytvoření textu osnovy
Ve většině případů při přidávání dekoru na textové řetězce ve vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, používáte text z hlediska kolekci diskrétní znaků nebo glyfů. Můžete například vytvořit lineární štětce přechodu a použijte ho k <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.TextBox> objektu. Při zobrazení nebo upravte pole, lineární štětce přechodu automaticky použita pro aktuální sadu znaků v textovém řetězci.  
  
 ![Text zobrazovaný štětcem lineárního přechodu](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Příklad lineární štětce přechodu použít textového pole  
  
 Ale můžete také převést text do <xref:System.Windows.Media.Geometry> objekty, umožňuje vytvářet jiné typy vizuálně formátovaným textem. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrys textového řetězce.  
  
 ![Osnova text použití štětce přechodu lineární](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Příklad lineární štětce přechodu u geometrie osnovy textu  
  
 Když se text bude převeden na <xref:System.Windows.Media.Geometry> objektu je již kolekce znaků – nelze upravit znaků v textovém řetězci. Však může ovlivnit vzhled text převedený změnou vlastností tahu a výplně. Tahu odkazuje na obrys text převedený; výplně odkazuje na oblasti uvnitř obrys text převedený.  
  
 Následující příklady znázorňují několika způsoby vytváření vizuálních efektů úpravou tahu a výplně převedený textu.  
  
 ![Text pomocí různých barev pro výplně a tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Příklad nastavení tahu a vyplňte pro různé barev  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Příklad štětce bitové kopie u tahu  
  
 Je také možné upravit ohraničující obdélník pole nebo zvýraznění převedený textu. Následující příklad ilustruje způsob, jak vytváření vizuálních efektů úpravou tahu a zvýraznění převedený textu.  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Příklad štětce obrázku použita pro tahu a zvýraznění  
  
## <a name="example"></a>Příklad  
 Klíč k převodu text, který má <xref:System.Windows.Media.Geometry> objekt, je použít <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření tohoto objektu, můžete použít <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> a <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody pro převod textu na <xref:System.Windows.Media.Geometry> objekty. Vrátí první metoda geometrie formátovaný text; Druhá metoda vrátí že geometrie formátovaného textu je ohraničujícího pole. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a k načítání geometrie formátovaného textu a jeho ohraničující pole.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby bylo možné zobrazit načtený <xref:System.Windows.Media.Geometry> objekty, je třeba získat přístup <xref:System.Windows.Media.DrawingContext> objektu, který je zobrazení převedeného textového. V těchto příkladech, kódu se provádí tak, že vytvoříte vlastní ovládací prvek objekt, který je odvozen od třídy, která podporuje vlastní vykreslení.  
  
 Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty v ovládacím prvku vlastní poskytují přepsání pro <xref:System.Windows.UIElement.OnRender%2A> metoda. Přepsaná metoda by měla použít <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metoda kreslení <xref:System.Windows.Media.Geometry> objekty.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>Viz také  
 [Kreslení formátovaného textu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
