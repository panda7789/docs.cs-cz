---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021651"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue vyvolá výjimku pro statická pole pouze init.

Počínaje .NET Core 3.0, je vyvolána výjimka při pokusu <xref:System.Reflection.FieldAttributes.InitOnly> o nastavení <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>hodnoty na statické, pole voláním .

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Framework a verzích rozhraní .NET Core před verzí 3.0 můžete nastavit hodnotu statického pole, které <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>je konstantní po inicializování[(pouze pro čtení v C#](~/docs/csharp/language-reference/keywords/readonly.md)) voláním . Nastavení takového pole tímto způsobem však vedlo k nepředvídatelnému chování založenému na cílovém rozhraní a nastavení optimalizace.

V .NET Core 3.0 a novější <xref:System.Reflection.FieldInfo.SetValue%2A> verze při <xref:System.Reflection.FieldAttributes.InitOnly> volání na <xref:System.FieldAccessException?displayProperty=nameWithType> statické, pole je vyvolána výjimka.

> [!TIP]
> Pole <xref:System.Reflection.FieldAttributes.InitOnly> je pole, které lze nastavit pouze v době, kdy je deklarováno, nebo v konstruktoru pro obsahující třídu. Jinými slovy, je konstantní po inicializování.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Inicializovat <xref:System.Reflection.FieldAttributes.InitOnly> statické, pole ve statickém konstruktoru. To platí pro dynamické i nedynamické typy.

Případně můžete <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> odebrat atribut z pole a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>potom zavolat .

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
