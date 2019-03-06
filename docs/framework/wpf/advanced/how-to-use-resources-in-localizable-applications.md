---
title: 'Postupy: Použití zdrojů v lokalizovatelných aplikacích'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376155"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Postupy: Použití zdrojů v lokalizovatelných aplikacích
Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze. K tomu, text, například názvy, třeba přeložit popisků, seznam položek pole a tak dále. Pro usnadnění převodu se shromáždí položky, které chcete přeložit do souborů prostředků. Zobrazit [lokalizace aplikace](how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci. Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný vývojáři potřebují k vývoji všechny lokalizovatelné prostředky do sestavení prostředků aplikace. Sestavení prostředků je lokalizován do různých jazycích a modelu code-behind používá správu prostředků [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst. Jeden ze souborů požadovaných pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (souborů .proj). Všechny prostředky, které používáte ve vaší aplikaci by měla být zahrnuty v souboru projektu. Následující příklad kódu ukazuje to.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Chcete-li použít prostředek ve vaší aplikaci, vytvoříte instanci <xref:System.Resources.ResourceManager> a načtěte prostředek, který chcete použít. Následující ukazuje, jak to provést.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
