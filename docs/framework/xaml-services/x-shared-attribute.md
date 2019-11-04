---
title: x:Shared – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459924"
---
# <a name="xshared-attribute"></a>x:Shared – atribut
Když se nastaví na `false`, upraví chování při načítání prostředků WPF tak, aby požadavky na prostředek s atributem vytvořily novou instanci pro každý požadavek místo sdílení stejné instance pro všechny požadavky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Poznámky  
 `x:Shared` je mapován na obor názvů XAML jazyka XAML a je rozpoznán jako platný prvek jazyka XAML pomocí .NET Framework služeb XAML a jeho čtenářů XAML. Nicméně uvedené možnosti `x:Shared` jsou relevantní pouze pro aplikace WPF a pro analyzátor XAML WPF. V prostředí WPF je `x:Shared` užitečné pouze jako atribut, je-li použit pro objekt, který existuje v rámci <xref:System.Windows.ResourceDictionary>WPF. Další použití nevyvolává výjimky analýzy ani jiné chyby, ale nemají žádný vliv.  
  
 Význam `x:Shared` není zadán ve specifikaci jazyka XAML. Další implementace jazyka XAML, jako jsou například ty, které se sestavují na .NET Framework XAML Services, nutně neposkytují podporu pro sdílení prostředků. Taková implementace XAML by mohla poskytnout podobné chování v rozhraní podpory, které také používá `x:Shared` hodnoty.  
  
 V WPF je výchozí podmínkou `x:Shared` pro prostředky `true`. Tato podmínka znamená, že všechny dané žádosti o prostředky vždycky vrátí stejnou instanci.  
  
 Změna objektu, který je vrácen prostřednictvím rozhraní API prostředků, jako je například <xref:System.Windows.FrameworkElement.FindResource%2A>nebo úprava objektu přímo v rámci <xref:System.Windows.ResourceDictionary>, změní původní prostředek. Pokud byly odkazy na tento prostředek odkazy na dynamické prostředky, získají uživatelé tohoto prostředku změněný prostředek.  
  
 Pokud byly odkazy na prostředek odkazy na statické prostředky, změny prostředku po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] době zpracování nebudou důležité. Další informace o statických a dynamických odkazech na prostředky naleznete v tématu [prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Explicitní určení `x:Shared="true"` je jenom zřídka, protože to je už výchozí. Neexistuje žádný přímý ekvivalent kódu pro `x:Shared` v objektovém modelu WPF; dá se zadat jenom v použití XAML a musí se zpracovat buď pomocí výchozího chování WPF, nebo v zprostředkujícím datovém proudu uzlu XAML v cestě zatížení, pokud se zpracovává pomocí .NET Framework služby XAML a jejich čtecích zařízení XAML.  
  
 Scénář pro `x:Shared="false"` je při definování <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy jako prostředku a poté zavedete prostředek elementu do modelu obsahu. `x:Shared="false"` umožňuje, aby prostředek elementu byl ve stejné kolekci vícekrát zavedený (například <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` to je neplatné, protože kolekce vynutila jedinečnost jejího obsahu. Chování `x:Shared="false"` však vytvoří jinou identickou instanci prostředku místo vrácení stejné instance.  
  
 Dalším scénářem pro `x:Shared="false"` je použití prostředku <xref:System.Windows.Freezable> pro hodnoty animace, ale chcete upravit prostředek na základě animace.  
  
 Zpracování řetězce `false` nerozlišuje velká a malá písmena.  
  
 V WPF je `x:Shared` platný pouze za následujících podmínek:  
  
- <xref:System.Windows.ResourceDictionary> obsahující položky `x:Shared` musí být zkompilovány. <xref:System.Windows.ResourceDictionary> nemůže být ve volném XAML nebo použit pro motivy.  
  
- <xref:System.Windows.ResourceDictionary> obsahující položky nesmí být vnořené v jiném <xref:System.Windows.ResourceDictionary>. Například nemůžete použít `x:Shared` pro položky v <xref:System.Windows.ResourceDictionary>, které se nachází v <xref:System.Windows.Style>, která již <xref:System.Windows.ResourceDictionary> položka.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Základní elementy](../wpf/advanced/base-elements.md)
