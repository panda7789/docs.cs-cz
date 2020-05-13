---
title: 'Postupy: Použití zdrojů v lokalizovatelných aplikacích'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212472"
---
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="04c36-102">Postupy: používání prostředků v lokalizovatelných aplikacích</span><span class="sxs-lookup"><span data-stu-id="04c36-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="04c36-103">Lokalizace znamená přizpůsobení uživatelského rozhraní pro různé jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="04c36-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="04c36-104">K tomu je nutné přeložit text, jako jsou názvy, popisky a položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="04c36-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="04c36-105">Aby bylo možné překlad usnadnit, jsou položky, které mají být přeloženy, shromažďovány do souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="04c36-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="04c36-106">Informace o tom, jak vytvořit soubor prostředků pro lokalizaci, najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md) .</span><span class="sxs-lookup"><span data-stu-id="04c36-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="04c36-107">Aby bylo možné aplikaci WPF lokalizovat, vývojáři potřebují sestavit všechny lokalizovatelné prostředky do sestavení prostředků.</span><span class="sxs-lookup"><span data-stu-id="04c36-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="04c36-108">Sestavení prostředků je lokalizováno do různých jazyků a kód na pozadí používá rozhraní API pro správu prostředků k načtení.</span><span class="sxs-lookup"><span data-stu-id="04c36-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="04c36-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="04c36-109">Example</span></span>

<span data-ttu-id="04c36-110">Jeden ze souborů vyžadovaných pro aplikaci WPF je soubor projektu (. proj).</span><span class="sxs-lookup"><span data-stu-id="04c36-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="04c36-111">Všechny prostředky, které ve vaší aplikaci používáte, by měly být zahrnuté do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="04c36-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="04c36-112">Následující příklad XAML ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="04c36-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="04c36-113">Chcete-li použít prostředek ve vaší aplikaci, vytvořte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="04c36-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="04c36-114">Následující kód jazyka C# ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="04c36-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="04c36-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="04c36-115">See also</span></span>

- [<span data-ttu-id="04c36-116">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="04c36-116">Localize an app</span></span>](how-to-localize-an-application.md)
