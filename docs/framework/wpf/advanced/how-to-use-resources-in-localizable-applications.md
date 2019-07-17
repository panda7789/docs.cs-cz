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
# <a name="how-to-use-resources-in-localizable-applications"></a>Postupy: Použití prostředků v lokalizovatelných aplikacích
Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze. K tomu, text, například názvy, třeba přeložit popisků, seznam položek pole a tak dále. Pro usnadnění převodu se shromáždí položky, které chcete přeložit do souborů prostředků. Zobrazit [lokalizace aplikace](how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci. Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný vývojáři potřebují k vývoji všechny lokalizovatelné prostředky do sestavení prostředků aplikace. Sestavení prostředků je lokalizován do různých jazycích a modelu code-behind používá rozhraní API pro správu prostředků k načtení. Jeden ze souborů požadovaných pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (souborů .proj). Všechny prostředky, které používáte ve vaší aplikaci by měla být zahrnuty v souboru projektu. Následující příklad kódu ukazuje to.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Chcete-li použít prostředek ve vaší aplikaci, vytvoříte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít. Následující ukazuje, jak to provést.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
