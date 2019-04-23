---
title: x:Shared – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: da35f209b632bdf9e4ab2298239a505df69d6048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125734"
---
# <a name="xshared-attribute"></a>x:Shared – atribut
Pokud je nastavena na `false`, upravuje chování načtení prostředku WPF, takže požadavky s atributy prostředku vytvoření nové instance pro každý požadavek místo sdílení stejné instanci pro všechny požadavky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Poznámky  
 `x:Shared` je mapován na obor názvů XAML jazyka XAML a je rozpoznán jako platný prvek jazyka XAML tak, že rozhraní .NET Framework XAML Services a jeho čtenáři XAML. Ale stanovených možnosti `x:Shared` jsou pouze relevantní pro aplikace WPF a pro analyzátor identifikátoru WPF XAML. V WPF `x:Shared` slouží pouze jako atribut při použití na objekt, který existuje v rámci WPF <xref:System.Windows.ResourceDictionary>. Další využití nevyvolají výjimky analýzy nebo jiné chyby, ale nemají žádný účinek.  
  
 Význam `x:Shared` není podle specifikace jazyka XAML. Jiné implementace XAML, jako jsou ty, které staví na rozhraní .NET Framework XAML Services, nemusí být nutně podporu sdílení prostředků. Tato implementace XAML může poskytují podobné chování v rámci podpory, který se používá také `x:Shared` hodnoty.  
  
 V WPF, výchozí `x:Shared` podmínku u prostředků je `true`. Tento stav znamená, že každá žádost o daný prostředek vždycky vrátí stejnou instanci.  
  
 Úpravy objektu, která je vrácena prostřednictvím prostředku rozhraní API, jako například <xref:System.Windows.FrameworkElement.FindResource%2A>, nebo úprava objektu přímo v rámci <xref:System.Windows.ResourceDictionary>, původní prostředek se změní. Odkazy na tento prostředek byl dynamický prostředek odkazy, získejte příjemci tento prostředek změněných prostředků.  
  
 Pokud nebyly odkazy na prostředek odkazy na statické prostředky, se změní na prostředek po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] doba zpracování nejsou relevantní. Další informace o statických a odkazy na dynamické prostředky, najdete v části [prostředky XAML](../wpf/advanced/xaml-resources.md).  
  
 Explicitní určení `x:Shared="true"` zřídka probíhá, protože to je již výchozí. Neexistuje žádné přímé kódu ekvivalentní `x:Shared` ve WPF objektu modelu; lze zadat pouze v XAML využití a je potřeba zpracovat výchozí chování WPF nebo zprostředkující proudu uzlu XAML v cestě zatížení Pokud zpracovány pomocí rozhraní .NET Framework XAML Se rvices a jeho čtenáři XAML.  
  
 Scénáře pro `x:Shared="false"` je, pokud definujete <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy jako prostředek a zaveďte elementu resource v obsahu modelu. `x:Shared="false"` Umožňuje prostředek element zavést více než jednou ve stejné kolekci (například <xref:System.Windows.Controls.UIElementCollection>). Bez `x:Shared="false"` to je neplatný, protože kolekce vynutí jedinečnost jeho obsah. Ale `x:Shared="false"` chování vytvoří jiná instance stejné prostředků místo vrácení stejnou instanci.  
  
 Další možností pro `x:Shared="false"` je, pokud používáte <xref:System.Windows.Freezable> prostředků pro hodnot animace, ale chcete upravit prostředek na základě za animace.  
  
 Zpracování řetězce `false` nerozlišuje malá a velká písmena.  
  
 V WPF `x:Shared` platí pouze za následujících podmínek:  
  
-   <xref:System.Windows.ResourceDictionary> , Který obsahuje položky s `x:Shared` musí být zkompilovány. <xref:System.Windows.ResourceDictionary> Nemůže být v rámci volný XAML nebo použít motivy.  
  
-   <xref:System.Windows.ResourceDictionary> , Který obsahuje položky nesmí být vnořen v rámci jiného <xref:System.Windows.ResourceDictionary>. Například nemůžete použít `x:Shared` pro položky v <xref:System.Windows.ResourceDictionary> , který je v rámci <xref:System.Windows.Style> , který je již <xref:System.Windows.ResourceDictionary> položky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky XAML](../wpf/advanced/xaml-resources.md)
- [Základní elementy](../wpf/advanced/base-elements.md)
