---
title: 'Postupy: Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: e28086d8c97070b854ebdea35fe347c64c5cd7ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377934"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Postupy: Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary
Tento příklad ukazuje způsob použití <xref:System.Windows.ResourceDictionary> do balíčku zdrojů lokalizovatelných řetězců prostředků pro aplikace Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary  
  
1.  Vytvoření <xref:System.Windows.ResourceDictionary> , která obsahuje řetězce, které byste rádi lokalizovat. Následující kód ukazuje příklad.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Tento kód definuje prostředek řetězce `localizedMessage`, typu <xref:System.String>, z <xref:System> obor názvů v knihovně mscorlib.dll.  
  
2.  Přidat <xref:System.Windows.ResourceDictionary> pro vaši aplikaci, pomocí následujícího kódu.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Použít prostředek řetězce ze značek, pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobně jako následující.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Použijte prostředek řetězce z kódu, pomocí kódu, jako je následující.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Lokalizace aplikace. Další informace najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md).
