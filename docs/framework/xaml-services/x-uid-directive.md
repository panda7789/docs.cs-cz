---
title: x:Uid – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837178"
---
# <a name="xuid-directive"></a>x:Uid – direktiva
Poskytuje jedinečný identifikátor pro prvky značek. V mnoha scénářích se tento jedinečný identifikátor používá v procesech lokalizace a nástrojích jazyka XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`identifier`|Ručně vytvořený nebo automaticky generovaný řetězec, který by měl být jedinečný v souboru, pokud je interpretován `x:Uid` příjemcem.|  
  
## <a name="remarks"></a>Poznámky  
 V [MS-XAML] je `x:Uid` definováno jako direktiva. Další informace naleznete v tématu [\[MS-XAML\] oddílu 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 `x:Uid` je diskrétní od `x:Name` z důvodu uvedeného scénáře Lokalizace XAML a tak, že identifikátory používané pro lokalizaci nemají žádné závislosti na vlivu programovacího modelu `x:Name`. `x:Name` se také řídí pomocí XAML namescope; `x:Uid` se ale neřídí žádným konceptem vynucování jedinečnosti jazyka XAML. Procesory XAML v širokém smyslu (procesory, které nejsou součástí procesu lokalizace), neočekávají, aby vynutily jedinečnost hodnot `x:Uid`. Tato odpovědnost je koncepčně na původci hodnot. Očekává se jedinečnost hodnoty `x:Uid` v rámci jednoho zdroje XAML je vhodná pro uživatele hodnot, jako jsou například vyhrazené procesy globalizace nebo nástroje. Typický model jedinečnosti je, že `x:Uid` hodnoty jsou jedinečné v rámci souboru kódovaného XML, který představuje XAML.  
  
 Nástroje, které mají významné znalosti konkrétního schématu jazyka XAML, mohou zvolit použití `x:Uid` pouze pro skutečné lokalizovatelné řetězce místo pro všechny případy, kde je v kódu zaznamenána hodnota textového řetězce.  
  
 Rozhraní mohou určit určitou vlastnost v objektovém modelu tak, aby byla aliasem pro `x:Uid` použitím atributu <xref:System.Windows.Markup.UidPropertyAttribute> na definiční typ. Pokud rozhraní určuje konkrétní vlastnost, není platný pro zadání `x:Uid` a člena s aliasem na stejném objektu. Pokud je zadán jak `x:Uid`, tak člen s aliasem, rozhraní API služby .NET Framework XAML obvykle vyvolá <xref:System.Xaml.XamlDuplicateMemberException> pro tento případ.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Další informace o roli `x:Uid` v procesu lokalizace WPF a ve formátu BAML jazyka XAML naleznete v tématu [globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md) nebo <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md)
