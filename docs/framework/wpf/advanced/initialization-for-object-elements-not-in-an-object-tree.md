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
ms.openlocfilehash: 1a1d956ee7f41ac1ac0fc9bd051a18b9ff438930
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459831"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicializace elementů objektu, které nejsou obsaženy ve stromu objektů
Některé aspekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inicializace jsou odvoditelné na procesy, které se obvykle spoléhají na tento prvek, který je připojen k logickému stromu nebo vizuálnímu stromu. Toto téma popisuje kroky, které mohou být nezbytné k inicializaci prvku, který není připojen k žádnému stromu.  

## <a name="elements-and-the-logical-tree"></a>Elementy a logický strom  
 Při vytváření instance třídy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v kódu, je třeba si uvědomit, že několik aspektů inicializace objektů pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy není záměrně součástí kódu, který je proveden při volání konstruktoru třídy. Zejména pro třídu ovládacího prvku není většina vizuální reprezentace daného ovládacího prvku definována konstruktorem. Namísto toho je vizuální reprezentace definována šablonou ovládacího prvku. Šablona potenciálně pochází z nejrůznějších zdrojů, ale většinou je šablona získaná ze stylů motivů. Šablony jsou efektivně pozdní vazbou; potřebná šablona není připojena k ovládacímu prvku, dokud je ovládací prvek připraven k rozložení. A ovládací prvek není připraven pro rozložení, dokud není připojen k logickému stromu, který se připojuje k povrchu vykreslování v kořenovém adresáři. Je to prvek na úrovni root, který iniciuje vykreslování všech jeho podřízených elementů, jak jsou definovány v logickém stromu.  
  
 Vizuální strom se také účastní tohoto procesu. Prvky, které jsou součástí vizuálního stromu prostřednictvím šablon, také nejsou plně vytvořeny, dokud se nepřipojí.  
  
 Důsledky tohoto chování jsou, že některé operace, které spoléhají na dokončené vizuální charakteristiky prvku, vyžadují další kroky. Příkladem je, že se pokoušíte získat vizuální vlastnosti třídy, která byla vytvořena, ale ještě není připojena ke stromu. Například pokud chcete volat <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> v <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a vizuál, který předáváte, je prvek, který není připojen ke stromu, tento prvek není vizuálně dokončen, dokud nejsou dokončeny další inicializační kroky.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Použití BeginInit a EndInit k inicializaci elementu  
 Různé třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementují rozhraní <xref:System.ComponentModel.ISupportInitialize>. Použijete metody <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> a <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> rozhraní k označení oblasti v kódu, který obsahuje kroky inicializace (například nastavení hodnot vlastností, které ovlivňují vykreslování). Po volání <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> v sekvenci může systém rozložení zpracovat element a začít hledat implicitní styl.  
  
 Pokud prvek, který nastavujete vlastnosti, je <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy, můžete volat verze třídy <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> spíše než přetypování do <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Vzorový kód  
 V následujícím příkladu je ukázkový kód pro konzolovou aplikaci, která používá rozhraní API pro vykreslování a <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> volného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru k ilustraci správného umístění <xref:System.Windows.FrameworkElement.BeginInit%2A> a <xref:System.Windows.FrameworkElement.EndInit%2A> k dalším voláním rozhraní API, která upravují vlastnosti, které ovlivňují vykreslování.  
  
 Příklad ukazuje pouze hlavní funkce. Funkce `Rasterize` a `Save` (nezobrazený) jsou funkce nástrojů, které se postará o zpracování obrazu a vstupně-výstupní operace.  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Viz také:

- [Stromy v subsystému WPF](trees-in-wpf.md)
- [Přehled vykreslování grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
