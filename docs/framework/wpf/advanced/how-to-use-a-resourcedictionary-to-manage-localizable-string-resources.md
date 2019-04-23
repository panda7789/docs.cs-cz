---
title: 'Postupy: Správa lokalizovatelných řetězcových prostředků pomocí ResourceDictionary'
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
ms.openlocfilehash: b56a307ed31fc8f7573215eac70350ac5e4b9de1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772112"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="d5247-102">Postupy: Správa lokalizovatelných řetězcových prostředků pomocí ResourceDictionary</span><span class="sxs-lookup"><span data-stu-id="d5247-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="d5247-103">Tento příklad ukazuje způsob použití <xref:System.Windows.ResourceDictionary> do balíčku zdrojů lokalizovatelných řetězců prostředků pro aplikace Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d5247-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="d5247-104">Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary</span><span class="sxs-lookup"><span data-stu-id="d5247-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1. <span data-ttu-id="d5247-105">Vytvoření <xref:System.Windows.ResourceDictionary> , která obsahuje řetězce, které byste rádi lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="d5247-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="d5247-106">Následující kód ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="d5247-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="d5247-107">Tento kód definuje prostředek řetězce `localizedMessage`, typu <xref:System.String>, z <xref:System> obor názvů v knihovně mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="d5247-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2. <span data-ttu-id="d5247-108">Přidat <xref:System.Windows.ResourceDictionary> pro vaši aplikaci, pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="d5247-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3. <span data-ttu-id="d5247-109">Použít prostředek řetězce ze značek, pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="d5247-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4. <span data-ttu-id="d5247-110">Použijte prostředek řetězce z kódu, pomocí kódu, jako je následující.</span><span class="sxs-lookup"><span data-stu-id="d5247-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5. <span data-ttu-id="d5247-111">Lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5247-111">Localize the application.</span></span> <span data-ttu-id="d5247-112">Další informace najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="d5247-112">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>
