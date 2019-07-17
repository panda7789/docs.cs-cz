---
title: 'Postupy: Použití prostředků v lokalizovatelných aplikacích'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 3634bb72cbacfb02b0a1230a47a1664cb8ce5009
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238465"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="beb21-102">Postupy: Použití prostředků v lokalizovatelných aplikacích</span><span class="sxs-lookup"><span data-stu-id="beb21-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="beb21-103">Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="beb21-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="beb21-104">K tomu, text, například názvy, třeba přeložit popisků, seznam položek pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="beb21-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="beb21-105">Pro usnadnění převodu se shromáždí položky, které chcete přeložit do souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="beb21-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="beb21-106">Zobrazit [lokalizace aplikace](how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="beb21-106">See [Localize an Application](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="beb21-107">Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný vývojáři potřebují k vývoji všechny lokalizovatelné prostředky do sestavení prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="beb21-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="beb21-108">Sestavení prostředků je lokalizován do různých jazycích a modelu code-behind používá rozhraní API pro správu prostředků k načtení.</span><span class="sxs-lookup"><span data-stu-id="beb21-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span> <span data-ttu-id="beb21-109">Jeden ze souborů požadovaných pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (souborů .proj).</span><span class="sxs-lookup"><span data-stu-id="beb21-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="beb21-110">Všechny prostředky, které používáte ve vaší aplikaci by měla být zahrnuty v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="beb21-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="beb21-111">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="beb21-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beb21-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="beb21-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="beb21-113">Chcete-li použít prostředek ve vaší aplikaci, vytvoříte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="beb21-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="beb21-114">Následující ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="beb21-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
