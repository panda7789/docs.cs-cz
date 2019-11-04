---
title: Vložené styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460002"
---
# <a name="inline-styles-and-templates"></a>Vložené styly a šablony
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje objekty <xref:System.Windows.Style> a objekty šablon (<xref:System.Windows.FrameworkTemplate> podtříd) jako způsob, jak definovat vizuální vzhled prvku v prostředcích, aby je bylo možné použít několikrát. Z tohoto důvodu atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], které přebírají typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> téměř vždy provádějí odkazy na existující styly a šablony namísto definování nových vložených.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Omezení vložených stylů a šablon  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]lze vlastnosti stylu a šablony technicky nastavit jedním ze dvou způsobů. Můžete použít syntaxi atributu pro odkazování na styl, který byl definován v rámci prostředku, například `<`*objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`. Nebo můžete použít syntaxi elementu vlastnosti k definování vloženého stylu pro instanci:  
  
 *objekt* `<` `>`  
  
 *objekt* `<` `.Style>`  
  
 `<` `Style``.../>`  
  
 *objekt* `</` `.Style>`  
  
 *objekt* `</` `>`  
  
 Použití atributů je mnohem běžnější. Styl, který je definován jako vložený a není definován v prostředcích, je nutně vymezen pouze na obsahující prvek a nelze jej znovu použít stejně snadno, protože nemá žádný klíč prostředku. Obecně platí, že uživatelsky definované styly jsou všestrannější a užitečnější a je více v souladu s obecným principem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovacího modelu oddělení logiky programu v kódu z návrhu v označení.  
  
 Obvykle neexistuje důvod k nastavení vloženého stylu nebo šablony, a to i v případě, že v tomto umístění chcete použít pouze tento styl nebo šablonu. Většina prvků, které mohou mít styl nebo šablonu, také podporují vlastnost obsahu a obsahový model. Pokud používáte pouze jakýkoli logický strom, který vytvoříte pomocí stylů nebo šablonování jednou, bylo by ještě snazší vyplnit tuto vlastnost obsahu ekvivalentními podřízenými elementy v přímém kódu. To by mělo zcela obejít mechanismy stylu a šablony.  
  
 Jiné syntaxe, které jsou povoleny rozšířeními značek, které vracejí objekt, jsou také možné pro styly a šablony. Mezi dvě taková rozšíření, která mají možné scénáře, patří [TemplateBinding](templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
