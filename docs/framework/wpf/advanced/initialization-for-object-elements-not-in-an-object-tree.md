---
title: Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: ed1f7781453503682648d740b57dd7af0a1715c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524127"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů
Některé aspekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inicializace odkládat procesů, které se zpravidla spoléhají na tento prvek připojení logického stromu nebo vizuálního stromu. Toto téma popisuje kroky, které mohou být nezbytné, aby se inicializovat element, který není připojený k buď stromu.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Elementy a logického stromu  
 Při vytváření instance [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy v kódu, je třeba si uvědomit, že několik aspektů objektu inicializace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy nejsou záměrně část kódu, který se spouští při volání konstruktoru třídy. Zejména pro třídu ovládacího prvku není definován většinu bude obsahovat vizuální reprezentaci tohoto ovládacího prvku pomocí konstruktoru. Místo toho bude obsahovat vizuální reprezentaci definované šablony ovládacího prvku. Šablona potenciálně pochází z nejrůznějších zdrojů, ale nejčastěji se šablona získá ze stylů motivů. Šablony jsou účinně pozdní vazby; nezbytné šablony není připojen na ovládací prvek, dokud nebude připravené pro rozložení ovládacího prvku. A ovládací prvek není připravený na rozložení, dokud je připojen k logické stromové struktury, která se připojuje k vykreslovací plochu v kořenovém adresáři. Je tento prvek úrovni kořenového adresáře, který iniciuje vykreslování všechny jeho podřízené prvky definované v logickém stromu.  
  
 Tento proces účastní také vizuálního stromu. Prvky, které jsou součástí vizuálního stromu prostřednictvím šablony jsou plně vytvořena instance také není dokud se nepřipojí.  
  
 Důsledky toto chování se, že určité operace, které závisí na dokončení vizuální vlastnosti elementu vyžadují další kroky. Příkladem je, pokud se pokoušíte získat vizuální vlastnosti třídy, která byla vytvořena, ale ještě není připojen ke stromu. Například pokud chcete volat <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a vizuál předáváte je element není připojen ke stromu, tento prvek není vizuálně kompletní až do dokončení inicializace dalších kroků.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Použití BeginInit a EndInit pro inicializaci elementu  
 Různé třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementovat <xref:System.ComponentModel.ISupportInitialize> rozhraní. Můžete použít <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> a <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> metody rozhraní k označení oblast v kódu, který obsahuje kroky inicializace (např. nastavení vlastnosti hodnoty tohoto vliv vykreslování). Po <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> je volána v sekvenci, systém rozložení zpracování elementu a začít hledat implicitní styl.  
  
 Pokud element vlastnosti na je <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy, pak můžete volat třída verzích <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> místo přetypování na <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Vzorový kód  
 V následujícím příkladu je ukázkový kód pro konzolovou aplikaci, která používá vykreslování [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] a <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> samostatných [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru pro ilustraci správné umístění <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> kolem jiné [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání který upravit vlastnosti, které ovlivňují vykreslování.  
  
 Tento příklad znázorňuje pouze hlavní funkci. Funkce `Rasterize` a `Save` (není vidět) jsou funkcí nástroje, které se postará o zpracování obrázků a vstupně-výstupních operací.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Viz také:
- [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
- [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
