---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721269"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.

Počínaje rozhraním .NET Core 3,0 je vyvolána výjimka při pokusu o nastavení hodnoty ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli pomocí volání <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .

#### <a name="change-description"></a>Popis změny

V .NET Framework a verzích .NET Core před 3,0 jste mohli nastavit hodnotu statického pole, které je konstanta po inicializaci ([ReadOnly v jazyce C#](~/docs/csharp/language-reference/keywords/readonly.md)) voláním <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> . Nicméně nastavení takového pole tímto způsobem vedlo k nepředvídatelnému chování na základě cílové architektury a nastavení optimalizace.

V .NET Core 3,0 a novějších verzích při volání <xref:System.Reflection.FieldInfo.SetValue%2A> ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli <xref:System.FieldAccessException?displayProperty=nameWithType> je vyvolána výjimka.

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly>Pole je jedno, které lze nastavit pouze v okamžiku deklarace nebo v konstruktoru pro třídu, která ji obsahuje. Jinými slovy je konstanta po inicializaci.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Proveďte inicializaci statických <xref:System.Reflection.FieldAttributes.InitOnly> polí ve statickém konstruktoru. To platí pro dynamické i jiné než dynamické typy.

Alternativně můžete odebrat <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atribut z pole a pak zavolat <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
