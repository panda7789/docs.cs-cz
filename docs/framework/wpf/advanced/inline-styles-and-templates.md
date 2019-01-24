---
title: Vložené styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 7f619985e909b772d8c7b86d8393341999288cba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496910"
---
# <a name="inline-styles-and-templates"></a>Vložené styly a šablony
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Style> objekty a objekty šablony (<xref:System.Windows.FrameworkTemplate> podtřídy) jako způsob, jak definovat vzhled elementu v prostředky, takže je možné použít víc než jednou. Z tohoto důvodu atributů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která přijímá typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> téměř vždy ujistěte se, odkazy na prostředky na stávající – styly a šablony spíše než definovat nové značky vložené.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Omezení vložené styly a šablony  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], styl a šablony vlastnosti lze nastavit technicky v jednom ze dvou způsobů. Syntaxe atributu slouží k odkazování styl, který byl definován v rámci prostředku, třeba `<` *objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`. Nebo syntax prvku vlastnosti můžete použít k definování vložených styl, například:  
  
 `<` *objekt* `>`  
  
 `<` *objekt* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *objekt* `.Style>`  
  
 `</` *objekt* `>`  
  
 Použití atributu je mnohem častější. Styl, který je definována vložením a není definováno v prostředků nutně působí na nadřazeného elementu a nejde znovu použít, stejně snadno, protože nemá klíč prostředku. Obecně definován prostředek stylu je univerzální a užitečné a další podle obecného [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovací model Princip oddělení logiku programu v kódu z návrhu v kódu.  
  
 Obvykle neexistuje žádný důvod nastavit styl nebo šablona vložené, i v případě, že chcete použít tento styl nebo šablona v dané oblasti. Většinu prvků, které mohou provádět styl nebo šablona také podporují vlastnost obsahu a obsahu modelu. Pokud používáte pouze libovolné Logická stromová struktura jednou vytvořit pomocí stylu nebo šablony, by bylo ještě jednodušší právě vyplníte vlastnost tohoto obsahu ekvivalentní podřízené elementy v kódu s přímým přístupem. To by úplně obejít mechanismy věnovaný stylu a šablon.  
  
 Styly a šablony existují také jiné syntaxe ve – rozšíření značek, které vracejí objekt povolené. Dva taková rozšíření, kterých je možné scénáře zahrnují [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Viz také:
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
