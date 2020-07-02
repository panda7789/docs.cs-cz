---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614543"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Nesprávná implementace MemberDescriptor. Equals

#### <a name="details"></a>Podrobnosti

Původní implementace <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porovnává dvě různé vlastnosti řetězce z porovnávaných objektů: název kategorie a řetězec s popisem. Tato oprava slouží k porovnání <xref:System.ComponentModel.MemberDescriptor.Category> prvního objektu s <xref:System.ComponentModel.MemberDescriptor.Category> druhým a <xref:System.ComponentModel.MemberDescriptor.Description> od prvního k <xref:System.ComponentModel.MemberDescriptor.Description> druhému.

#### <a name="suggestion"></a>Návrh

Pokud vaše aplikace závisí na tom <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> `false` , kde se někdy vrátí, když jsou popisovače ekvivalentní a že cílíte na .NET Framework 4.6.2 nebo novější, máte k dispozici několik možností:

- Udělejte změny kódu pro porovnání <xref:System.ComponentModel.MemberDescriptor.Category> polí a <xref:System.ComponentModel.MemberDescriptor.Description> také při volání <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.
- Odsouhlasit tuto změnu přidáním následující hodnoty do souboru app.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

Pokud vaše aplikace cílí na .NET Framework 4.6.1 nebo starší verze a běží na .NET Framework 4.6.2 nebo novějším a chcete povolit tuto změnu, můžete nastavit přepínač kompatibility na `false` hodnotu přidáním následující hodnoty do souboru app.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
