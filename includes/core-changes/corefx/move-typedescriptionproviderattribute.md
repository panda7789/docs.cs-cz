---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182041"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute přesunuté do jiného sestavení

<xref:System.ComponentModel.TypeDescriptionProviderAttribute> Třída byla přesunuta.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 2,2 a starších verzích <xref:System.ComponentModel.TypeDescriptionProviderAttribute> se Třída nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.TypeDescriptionProviderAttribute> k načtení typu voláním metody <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení. V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

### Affected APIs

- Not detectable via API analysis

-->