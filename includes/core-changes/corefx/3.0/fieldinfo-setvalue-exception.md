---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449548"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.

Počínaje rozhraním .NET Core 3,0 je vyvolána výjimka při pokusu o nastavení hodnoty ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli voláním <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Změnit popis

V .NET Framework a verzích .NET Core před 3,0 jste mohli nastavit hodnotu statického pole, které je konstanta po inicializaci ([ReadOnly v C# ](~/docs/csharp/language-reference/keywords/readonly.md)), voláním <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>. Nicméně nastavení takového pole tímto způsobem vedlo k nepředvídatelnému chování na základě cílové architektury a nastavení optimalizace.

V .NET Core 3,0 a novějších verzích při volání <xref:System.Reflection.FieldInfo.SetValue%2A> ve statickém <xref:System.Reflection.FieldAttributes.InitOnly> poli je vyvolána výjimka <xref:System.FieldAccessException?displayProperty=nameWithType>.

> [!TIP]
> Pole <xref:System.Reflection.FieldAttributes.InitOnly> je jeden, který lze nastavit pouze v okamžiku, kdy je deklarován nebo v konstruktoru pro třídu, která ji obsahuje. Jinými slovy je konstanta po inicializaci.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Proveďte inicializaci statických <xref:System.Reflection.FieldAttributes.InitOnly> polí ve statickém konstruktoru. To platí pro dynamické i jiné než dynamické typy.

Případně můžete z pole odebrat atribut <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> a potom volat <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
