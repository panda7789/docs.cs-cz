---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147533"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute přesunutdo jiného sestavení

Třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> byla přesunuta.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> a starších verzích se třída nachází v sestavě *System.ComponentModel.TypeConverter.*

Počínaje rozhraním .NET Core 3.0 se nachází v sestavení *System.ObjectModel.*

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna má vliv pouze na <xref:System.ComponentModel.TypeDescriptionProviderAttribute> aplikace, které používají <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> reflexe <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> načíst typ voláním metody, jako je například nebo přetížení, které předpokládá, že typ je v určitém sestavení. Pokud tomu tak je, sestavení odkazované ve volání metody by měla být aktualizována tak, aby odrážela nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné.

<!--

### Affected APIs

- Not detectable via API analysis

-->
