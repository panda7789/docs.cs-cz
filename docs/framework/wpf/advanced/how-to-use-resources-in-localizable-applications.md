---
title: 'Postupy: Použití zdrojů v lokalizovatelných aplikacích'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 82a24feb4008b6cfd7c1751c6449c0d8515ffe87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544700"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="9c072-102">Postupy: Použití zdrojů v lokalizovatelných aplikacích</span><span class="sxs-lookup"><span data-stu-id="9c072-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="9c072-103">Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c072-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="9c072-104">Chcete-li to provést, text, například názvy, muset přeložit titulků, položky seznamu pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9c072-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="9c072-105">V zájmu snazší překlad položky, které chcete přeložit se shromažďují do zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="9c072-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="9c072-106">V tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="9c072-106">See [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="9c072-107">Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný, vývojáři potřebujete k vytvoření lokalizovatelný prostředky do prostředku sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c072-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="9c072-108">Sestavení prostředků je lokalizované do různých jazyků a Správa prostředků používá modelu code-behind [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst.</span><span class="sxs-lookup"><span data-stu-id="9c072-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="9c072-109">Jeden z soubory potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (.proj).</span><span class="sxs-lookup"><span data-stu-id="9c072-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="9c072-110">Všechny prostředky, které používáte ve vaší aplikaci by měl být obsažen v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9c072-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="9c072-111">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="9c072-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c072-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c072-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="9c072-113">V aplikaci použít prostředek, můžete vytvořit instanci <xref:System.Resources.ResourceManager> a načtení prostředků, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="9c072-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="9c072-114">Následující ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="9c072-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
