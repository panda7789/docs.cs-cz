---
title: "Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů"
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
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5d617176852e72b4b46e48ff9a4528bec373272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů
Některé aspekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inicializace odložit procesy, které se zpravidla spoléhají na daný element připojené k logického stromu nebo vizuálním stromu. Toto téma popisuje kroky, které může být nutné za účelem inicializace element, který není připojen k buď stromu.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Elementy a logickém stromu.  
 Při vytváření instance [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] – třída v kódu, je třeba si uvědomit, že několik aspektů objektu inicializace pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy jsou záměrně není součástí kód, který se spustí při volání metody konstruktoru třídy. Platí to hlavně o třídu ovládacího prvku většinu vizuální reprezentace tento ovládací prvek není definované konstruktoru. Místo toho je vizuální reprezentace definované šablony ovládacího prvku. Šablona potenciálně pochází z různých zdrojů, ale nejčastěji šabloně se získávají z styly motivů. Šablony jsou efektivně vazby; nezbytné šablony není připojen na ovládací prvek, dokud je připraven pro rozložení ovládacího prvku. A ovládací prvek není připraven pro rozložení, dokud je připojen k logické stromové struktury, která se připojuje k vykreslování prostor v kořenovém adresáři. Je daný element úrovni kořenového adresáře, který iniciuje vykreslování všech jeho podřízených elementů, jak jsou definovány v logickém stromu.  
  
 Tento proces účastní také vizuálním stromu. Elementy, které jsou součástí vizuálním stromu prostřednictvím šablony také není plně instance dokud připojen.  
  
 Důsledky toto chování se, že určité operace, které jsou závislé na dokončené visual charakteristiky elementu vyžadují další kroky. Příkladem je, pokud se pokoušíte získat vizuální vlastnosti třídy, která byla vytvořená, ale ještě nebyla připojit ke stromu. Například pokud chcete volat <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a visual předáváte je element není připojeno k strom, daný element není vizuálně dokončena, dokud inicializace další kroky.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Pomocí BeginInit a EndInit k chybě při inicializaci elementu  
 Různé třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementovat <xref:System.ComponentModel.ISupportInitialize> rozhraní. Můžete použít <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> a <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> metody rozhraní k označení oblast ve vašem kódu, který obsahuje kroků inicializace (například nastavení vlastnosti hodnoty tohoto vliv vykreslování). Po <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> je volána v sekvenci, systém rozložení může zpracovat elementu a spusťte hledání implicitní styl.  
  
 Pokud element jsou nastavení vlastnosti na <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy, pak můžete volat třída verzích <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> místo přetypování k <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Ukázkový kód  
 Následující příklad je ukázkový kód pro konzolovou aplikaci, která používá vykreslování [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] a <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> samostatných [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor pro ilustraci správné umístění <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> kolem dalších [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání Upravte vlastnosti, které ovlivňují vykreslování.  
  
 Tento příklad znázorňuje hlavní funkce. Funkce `Rasterize` a `Save` (není vidět) jsou funkcí nástroje, které postará o zpracování obrázků a vstupně-výstupní operace.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Viz také  
 [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
