---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568238"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute přesunuté do jiného sestavení

Třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> byla přesunuta.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 2,2 a starších verzích se třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.TypeDescriptionProviderAttribute> typu voláním metody, jako je například <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, která předpokládá, že typ je v konkrétním sestavení. V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!--

### Affected APIs

- Not detectable via API analysis

-->
