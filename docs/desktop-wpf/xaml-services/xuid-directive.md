---
title: x:Uid – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071337"
---
# <a name="xuid-directive"></a>x:Uid – direktiva

Poskytuje jedinečný identifikátor pro prvky značek. V mnoha scénářích tento jedinečný identifikátor používá procesy a nástroje lokalizace XAML.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`identifier`|Ručně vytvořený nebo automaticky generovaný řetězec, který by měl být `x:Uid` jedinečný v souboru, pokud je interpretován spotřebitelem.|

## <a name="remarks"></a>Poznámky

V [MS-XAML], `x:Uid` je definována jako směrnice. Další informace naleznete [ \[v oddíle\] 5.3.6 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid`je diskrétní z `x:Name` obou z důvodu uvedeného scénáře lokalizace XAML a tak, aby identifikátory, které `x:Name`se používají pro lokalizaci nemají žádné závislosti na vlivů programovacího modelu . Také `x:Name` se řídí název xaml; však `x:Uid` se neřídí žádný jazyk XAML definované koncepce vynucení jedinečnosti. Očekává se, že procesory XAML v širokém slova smyslu (procesory, které `x:Uid` nejsou součástí procesu lokalizace) vynucují jedinečnost hodnot. Tato odpovědnost je koncepčně na původce hodnot. Očekávání jedinečnosti `x:Uid` hodnot v rámci jednoho zdroje XAML je pro spotřebitele hodnot, jako jsou vyhrazené globalizační procesy nebo nástroje, přiměřené. Typický model jedinečnosti `x:Uid` spočine na to, že hodnoty jsou jedinečné v rámci souboru xml kódovaného, který představuje XAML.

Nástroje, které mají významné znalosti o konkrétní schéma XAML můžete použít `x:Uid` pouze pro skutečné lokalizovatelné řetězce, nikoli pro všechny případy, kde je zjištěna hodnota textového řetězce v značky.

Architektury můžete určit konkrétní vlastnost v jejich objektový `x:Uid` model jako <xref:System.Windows.Markup.UidPropertyAttribute> alias pro použitím atribut u definující typ. Pokud framework určuje určitou vlastnost, není platný `x:Uid` pro určení obou a aliased člen na stejném objektu. Pokud `x:Uid` jsou zadány oba a aliased člen, rozhraní API <xref:System.Xaml.XamlDuplicateMemberException> služby .NET XAML služby obvykle vyvolá pro tento případ.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Další informace o roli `x:Uid` v procesu lokalizace WPF a ve formě BAML XAML naleznete v [tématu Globalizace pro WPF](../../framework/wpf/advanced/globalization-for-wpf.md) nebo<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizace pro WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
