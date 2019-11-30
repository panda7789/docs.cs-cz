---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644045"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem

Od verze .NET Core 3,0 RC1 se dostupnost `AccessibleObject.RuntimeIDFirstItem` změnila z `protected` na `internal`.

#### <a name="change-description"></a>Změnit popis

Počínaje rozhraním .NET Core 3,0 Preview 4 bylo `protected`pole `AccessibleObject.RuntimeIDFirstItem`. Počínaje platformou .NET Core 3,0 RC1 se změnila z `protected` na `internal`, aby se zarovnala přístupnost pole v .NET Framework.

#### <a name="version-introduced"></a>Představená verze

3,0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může mít vliv na to, jestli jste vyvinuli aplikaci .NET Core s typem, který je odvozený od <xref:System.Windows.Forms.AccessibleObject> a přistupuje k poli `RuntimeIDFirstItem`. V takovém případě můžete definovat místní konstantu následujícím způsobem:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Nedá se detekovat přes analýzu rozhraní API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
