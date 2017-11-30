---
title: "Postupy: Použití zdrojů v lokalizovatelných aplikacích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d803989292e2fc6b0945c397df5ce32d318147fc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="4495e-102">Postupy: Použití zdrojů v lokalizovatelných aplikacích</span><span class="sxs-lookup"><span data-stu-id="4495e-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="4495e-103">Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="4495e-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="4495e-104">Chcete-li to provést, text, například názvy, muset přeložit titulků, položky seznamu pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4495e-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="4495e-105">V zájmu snazší překlad položky, které chcete přeložit se shromažďují do zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="4495e-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="4495e-106">V tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="4495e-106">See [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="4495e-107">Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný, vývojáři potřebujete k vytvoření lokalizovatelný prostředky do prostředku sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="4495e-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="4495e-108">Sestavení prostředků je lokalizované do různých jazyků a Správa prostředků používá modelu code-behind [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst.</span><span class="sxs-lookup"><span data-stu-id="4495e-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="4495e-109">Jeden z soubory potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (.proj).</span><span class="sxs-lookup"><span data-stu-id="4495e-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="4495e-110">Všechny prostředky, které používáte ve vaší aplikaci by měl být obsažen v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4495e-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="4495e-111">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="4495e-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4495e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4495e-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="4495e-113">V aplikaci použít prostředek, můžete vytvořit instanci <xref:System.Resources.ResourceManager> a načtení prostředků, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4495e-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="4495e-114">Následující ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="4495e-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
