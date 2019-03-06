---
title: 'Postupy: Automatické rozložení použitím mřížky'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 5fa023002ac66a65e3c179434841c975287d170c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357479"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Postupy: Automatické rozložení použitím mřížky
Tento příklad popisuje, jak pomocí mřížky automatické rozložení přístupu k vytvoření lokalizovatelné aplikace.  
  
 Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces. Lokalizátoři často potřeba změnit velikost a umístění prvků kromě překlad textu. V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy. Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které tak snížit potřeba úpravy. Přístup k vytváření aplikací, které se dají snadno změně velikosti a přemístěných se nazývá `auto layout`.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje použití tabulky na pozici některá tlačítka a text. Všimněte si, že výšku a šířku buňky jsou nastaveny na `Auto`; proto nastaví na buňku, která obsahuje tlačítko s imagí podle obrázku. Vzhledem k tomu, <xref:System.Windows.Controls.Grid> element můžete upravit na jeho obsah, může být užitečné, když se vezme automatické rozložení přístup k návrhu aplikací, které může být lokalizována.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí mřížky.  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Následující obrázek znázorňuje výstup tohoto ukázkového kódu.  
  
 ![Grid – příklad](./media/glob-grid.png "glob_grid")  
Mřížka  
  
## <a name="see-also"></a>Viz také:
- [Přehled automatického rozložení](use-automatic-layout-overview.md)
- [Vytvoření tlačítka pomocí automatického rozložení](how-to-use-automatic-layout-to-create-a-button.md)
