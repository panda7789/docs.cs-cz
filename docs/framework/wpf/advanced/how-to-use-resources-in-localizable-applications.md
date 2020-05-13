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
# <a name="how-to-use-resources-in-localizable-apps"></a>Postupy: používání prostředků v lokalizovatelných aplikacích

Lokalizace znamená přizpůsobení uživatelského rozhraní pro různé jazykové verze. K tomu je nutné přeložit text, jako jsou názvy, popisky a položky seznamu. Aby bylo možné překlad usnadnit, jsou položky, které mají být přeloženy, shromažďovány do souborů prostředků. Informace o tom, jak vytvořit soubor prostředků pro lokalizaci, najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md) . Aby bylo možné aplikaci WPF lokalizovat, vývojáři potřebují sestavit všechny lokalizovatelné prostředky do sestavení prostředků. Sestavení prostředků je lokalizováno do různých jazyků a kód na pozadí používá rozhraní API pro správu prostředků k načtení.

## <a name="example"></a>Příklad

Jeden ze souborů vyžadovaných pro aplikaci WPF je soubor projektu (. proj). Všechny prostředky, které ve vaší aplikaci používáte, by měly být zahrnuté do souboru projektu. Následující příklad XAML ukazuje to.

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

Chcete-li použít prostředek ve vaší aplikaci, vytvořte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít. Následující kód jazyka C# ukazuje, jak to provést.

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>Viz také

- [Lokalizace aplikace](how-to-localize-an-application.md)
