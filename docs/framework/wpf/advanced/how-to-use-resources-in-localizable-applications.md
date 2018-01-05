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
ms.workload: dotnet
ms.openlocfilehash: e025b42a72def81420de7d82dcf027405669ce78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Postupy: Použití zdrojů v lokalizovatelných aplikacích
Lokalizace znamená přizpůsobení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro různé jazykové verze. Chcete-li to provést, text, například názvy, muset přeložit titulků, položky seznamu pole a tak dále. V zájmu snazší překlad položky, které chcete přeložit se shromažďují do zdrojových souborů. V tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) informace o tom, jak vytvořit soubor prostředků pro lokalizaci. Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizovatelný, vývojáři potřebujete k vytvoření lokalizovatelný prostředky do prostředku sestavení aplikace. Sestavení prostředků je lokalizované do různých jazyků a Správa prostředků používá modelu code-behind [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] načíst. Jeden z soubory potřebné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je soubor projektu (.proj). Všechny prostředky, které používáte ve vaší aplikaci by měl být obsažen v souboru projektu. Následující příklad kódu ukazuje to.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 V aplikaci použít prostředek, můžete vytvořit instanci <xref:System.Resources.ResourceManager> a načtení prostředků, kterou chcete použít. Následující ukazuje, jak to udělat.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
