---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622346"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Pozadí pásu karet je v lokalizovaných sestaveních nastaveno na transparentní

#### <a name="details"></a>Podrobnosti

<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>pozadí v lokalizovaných sestaveních se vždycky vykresluje pomocí transparentního štětce, což má za následek špatné prostředí uživatelského rozhraní. To je opraveno ve .NET Framework 4,7 WPF oprava aktualizací lokalizovaných prostředků pro <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> , což zase zajišťuje výběr správného štětce.

#### <a name="suggestion"></a>Návrh

Upgradovat na .NET Framework 4,7

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.2|
|Typ|Modul runtime|
