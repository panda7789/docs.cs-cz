---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644045"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Změna přístupu pro AccessibleObject.RuntimeIDFirstItem

Počínaje rozhraním .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1 `protected` se `internal`přístupnost nástroje změnila z na .

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3.0 `protected`Preview 4 bylo `AccessibleObject.RuntimeIDFirstItem` pole . Počínaje rozhraním .NET Core 3.0 RC1 `internal` se změnil z `protected` na zarovnat s usnadněním přístupu pole v rozhraní .NET Framework.

#### <a name="version-introduced"></a>Zavedená verze

3.0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Změna může ovlivnit vás, pokud jste vyvinuli aplikaci .NET Core <xref:System.Windows.Forms.AccessibleObject> s typem, který je odvozen od pole a přistupuje k němu. `RuntimeIDFirstItem` Pokud se jedná o tento případ, můžete definovat místní konstantu takto:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Nelze zjistit pomocí analýzy rozhraní API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
