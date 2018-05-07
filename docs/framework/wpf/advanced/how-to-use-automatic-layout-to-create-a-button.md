---
title: 'Postupy: Vytvoření tlačítka pomocí automatického rozložení'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Postupy: Vytvoření tlačítka pomocí automatického rozložení
Tento příklad popisuje postup k vytvoření tlačítka v lokalizovatelný aplikaci, použijte postup automatického rozložení.  
  
 Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces. Často překladatelům při lokalizaci potřeba jeho velikost a umístění elementy kromě překlad textu. V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy. Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které se potřeby pro úpravu. Přístup pro zápis aplikace, které může být snadněji změněnou a přemístěných nazývá `automatic layout`.  
  
 Následující dva [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady vytvářet aplikace, které doložit tlačítko; jednu anglické textem a jednu s španělské text. Všimněte si, že kód je stejný, s výjimkou textu. tlačítko upraví podle textu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup ukázky kódu.  
  
 ![Tlačítko stejné s textem v různých jazycích](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Tlačítko automaticky s možností změny velikosti  
  
## <a name="see-also"></a>Viz také  
 [Přehled automatického rozložení](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Automatické rozložení použitím mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
