---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721722"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute přesunuté do jiného sestavení

<xref:System.ComponentModel.TypeDescriptionProviderAttribute>Třída byla přesunuta.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2,2 a starších verzích se <xref:System.ComponentModel.TypeDescriptionProviderAttribute> Třída nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.TypeDescriptionProviderAttribute> typu voláním metody, jako <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení. V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

- Not detectable via API analysis

-->
