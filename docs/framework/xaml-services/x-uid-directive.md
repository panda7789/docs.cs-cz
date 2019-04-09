---
title: x:Uid – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: c8f0580c987b87193b5b6a38559043e50fc7cb89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152513"
---
# <a name="xuid-directive"></a>x:Uid – direktiva
Poskytuje jedinečný identifikátor pro elementy značek. V mnoha scénářích používá tento jedinečný identifikátor nástroje a procesy lokalizace XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`identifier`|A vytvořit ručně nebo automaticky generované řetězec, který by měl být jedinečný v souboru v případě, je interpretována `x:Uid` příjemce.|  
  
## <a name="remarks"></a>Poznámky  
 V [MS-XAML] `x:Uid` je definován jako směrnice. Další informace najdete v tématu [ \[MS-XAML\] části 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid` je diskrétní z `x:Name` i z důvodu stanovených scénář lokalizace XAML a tak, aby identifikátory, které se používají pro lokalizaci nemají žádné závislosti na programovacím modelu důsledcích `x:Name`. Navíc `x:Name` se řídí XAML namescope; však `x:Uid` neřídí žádné informace definované jazyka XAML jedinečnost výkonu. XAML procesorů v širokém smyslu (procesory, které nejsou součástí proces lokalizace) se nepředpokládá vynutit jedinečnost `x:Uid` hodnoty. Zodpovědnosti je téměř na odesílatel požadavku dostane informaci hodnoty. Očekávání jedinečnost `x:Uid` hodnot v rámci jednoho zdroje XAML je přijatelné pro spotřebitele hodnot, například vyhrazené globalizace procesů nebo nástroje. Typické jedinečnost modelu je, že `x:Uid` hodnoty jsou jedinečné v rámci souboru kódu XML, který představuje XAML.  
  
 Nástroje, které nemají důležité informace o konkrétní schématu XAML můžete zvolit použití `x:Uid` pouze pro true lokalizovatelných řetězců, místo pro všechny případy, ve kterém je došlo k textový řetězec v kódu.  
  
 Rozhraní můžete určit konkrétní vlastnost v modelu objektu jako alias pro `x:Uid` použitím atributu <xref:System.Windows.Markup.UidPropertyAttribute> k definování typu. Pokud rozhraní určuje konkrétní vlastnost, není platný pro zadání obou `x:Uid` a alias člena na stejný objekt. Pokud mají oba `x:Uid` a zadávají se člen alias, obvykle vyvolá rozhraní API .NET Framework XAML Services <xref:System.Xaml.XamlDuplicateMemberException> pro tento případ.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Další informace o roli `x:Uid` proces lokalizace WPF a BAML formu XAML najdete v tématu [globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md) nebo <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md)
