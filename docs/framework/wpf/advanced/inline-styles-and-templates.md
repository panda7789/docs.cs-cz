---
title: "Vložené styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2acb455db8f8bdc5a95bfd2462b651cebbb692c3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="inline-styles-and-templates"></a>Vložené styly a šablony
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje <xref:System.Windows.Style> objekty a objekty šablony (<xref:System.Windows.FrameworkTemplate> podtřídy) jako způsob, jak definovat vzhled elementu v prostředků, tak, aby bylo možné několikrát. Z tohoto důvodu atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které přebírají typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> definovat nové vložené místo prostředků odkazuje na existující styly a šablony téměř vždy.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Omezení vložené styly a šablony  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], styl a šablony vlastnosti technicky jde nastavit v jednom ze dvou způsobů. Můžete tak, aby odkazovaly styl, který byl definován v rámci prostředku, například pomocí syntaxe atribut `<` *objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`. Nebo můžete definovat vložené styl pro instanci pomocí syntaxe element vlastnost:  
  
 `<`*objekt*`>`  
  
 `<`*objekt*`.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</`*objekt*`.Style>`  
  
 `</`*objekt*`>`  
  
 Používání atributu je mnohem víc běžné. Styl, který je definována vložením a není definovaná v prostředky nutně rozsah obsahující element jenom a nelze znovu použít tak snadno, protože nemá žádné klíč prostředku. Obecně je univerzální a užitečné styl definované prostředků a je v souladu s obecné Další [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovací model zásada oddělování program logiku v kódu z návrhu v kódu.  
  
 Obvykle neexistuje žádný důvod k nastavení vložené styl nebo šablony, i když chcete používat tento styl nebo šablony v daném umístění. Většina elementů, které může provádět styl nebo šablony také podporují vlastnost obsahu a obsahu modelu. Pokud používáte pouze ať logického stromu vytvoříte jednou prostřednictvím stylů nebo ukázka, bylo by to bylo ještě jednodušší právě vyplníte vlastnost tohoto obsahu ekvivalentní podřízených elementů v přímé značek. To by zcela nepoužívat mechanismy style a šablony.  
  
 Ostatních syntaxí povolené rozšíření značek, které vracejí objekt je také možné styly a šablony. Dva taková rozšíření, které mají možné scénáře zahrnují [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Viz také  
 [Stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md)
