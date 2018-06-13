---
title: x:Shared – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: bee37735382249d2919ef870ca495e6096532352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563794"
---
# <a name="xshared-attribute"></a>x:Shared – atribut
Pokud nastavíte hodnotu `false`, mění chování WPF načtení prostředků tak, aby požadavky pro prostředek s atributy vytvoření nové instance pro každý požadavek místo sdílení stejné instanci pro všechny požadavky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Poznámky  
 `x:Shared` je namapovaná na oboru názvů jazyka XAML jazyka XAML a je rozpoznat jako platný element jazyka XAML rozhraní .NET Framework XAML Services a jeho čtečky XAML. Ale stanovené možnosti `x:Shared` jsou pouze relevantní pro aplikace WPF a pro analyzátor WPF XAML. V grafickém subsystému WPF `x:Shared` je užitečné jako atribut pouze při použití objektu, která existuje v rámci WPF <xref:System.Windows.ResourceDictionary>. Další použití nevyvolá výjimku, analýzy výjimky nebo jiné chyby, ale nemají žádný účinek.  
  
 Význam `x:Shared` není zadané v specifikace jazyka XAML. Jiných implementacích XAML, jako jsou ty, které sestavení v rozhraní .NET Framework XAML Services neposkytují nutně sdílení prostředků podpory. Implementace takových XAML poskytovat podobné chování v podpůrné framework, který používá `x:Shared` hodnoty.  
  
 V grafickém subsystému WPF, výchozí `x:Shared` podmínka pro prostředky je `true`. Tento stav znamená, že každá žádost daného prostředku vždy vrátí stejné instanci.  
  
 Objekt, který je vrácen prostřednictvím API, prostředků, jako úprava <xref:System.Windows.FrameworkElement.FindResource%2A>, nebo úprava objektu přímo v rámci <xref:System.Windows.ResourceDictionary>, změní původní prostředků. Dynamické prostředků odkazy kdyby odkazy na tento prostředek uživatelé prostředku získat změněné prostředků.  
  
 Změní-li odkazy na prostředek měla odkazy statické prostředků, k prostředku po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] doba zpracování jsou důležité. Další informace o statických a dynamických prostředků odkazy najdete v tématu [XAML prostředky](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Explicitní určení `x:Shared="true"` nevyužívá, protože již výchozí. Neexistuje žádné přímé kód ekvivalentní `x:Shared` v WPF objektu modelu, lze zadat pouze využití XAML a musí být zpracován jako výchozí chování WPF nebo v zprostředkující datový proud uzlu XAML v cestě zatížení Pokud zpracované pomocí rozhraní .NET Framework XAML Se rvices a jeho čtečky XAML.  
  
 Scénář pro `x:Shared="false"` je, pokud definujete <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy jako prostředek a potom zavedení element prostředků do modelu obsahu. `x:Shared="false"` Umožňuje prostředek element potřeba zavést vícekrát ve stejné kolekci (například <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` to je neplatný, protože kolekce vyžaduje jedinečnost její obsah. Ale `x:Shared="false"` chování vytvoří jiná instance stejné prostředku místo vrací stejnou instanci.  
  
 Jiné scénáře `x:Shared="false"` je, pokud použijete <xref:System.Windows.Freezable> prostředku pro animace hodnoty, ale chcete upravit prostředek na základě za animace.  
  
 Řetězec ošetření `false` není velká a malá písmena.  
  
 V grafickém subsystému WPF `x:Shared` je platný pouze za následujících podmínek:  
  
-   <xref:System.Windows.ResourceDictionary> Obsahující položky s `x:Shared` musí být zkompilovány. <xref:System.Windows.ResourceDictionary> Nemůže být v rámci přijít XAML nebo použít pro motivy.  
  
-   <xref:System.Windows.ResourceDictionary> Obsahuje položky nesmí být vnořený v rámci jiného <xref:System.Windows.ResourceDictionary>. Například nemůžete použít `x:Shared` pro položky v <xref:System.Windows.ResourceDictionary> se v rámci <xref:System.Windows.Style> který je už <xref:System.Windows.ResourceDictionary> položky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ResourceDictionary>  
 [Prostředky XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Základní elementy](../../../docs/framework/wpf/advanced/base-elements.md)
