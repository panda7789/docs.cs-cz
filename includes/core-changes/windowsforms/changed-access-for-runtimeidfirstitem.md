---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003020"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem

Od verze .NET Core 3,0 RC1 se dostupnost `AccessibleObject.RuntimeIDFirstItem` změnila z `protected` na `internal`.

#### <a name="change-description"></a>Změnit popis

Od verze .NET Core 3,0 Preview 4 bylo pole `AccessibleObject.RuntimeIDFirstItem` `protected`. Od verze .NET Core 3,0 RC1 se změnila z `protected` na `internal`, aby se zarovnala přístupnosti pole v .NET Framework.

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
