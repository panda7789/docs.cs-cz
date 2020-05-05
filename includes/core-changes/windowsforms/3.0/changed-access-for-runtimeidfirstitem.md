---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644045"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem

Od verze .NET Core 3,0 RC1 se přístupnost `AccessibleObject.RuntimeIDFirstItem` pro změnila z `protected` na. `internal`

#### <a name="change-description"></a>Popis změny

Od verze .NET Core 3,0 Preview 4 bylo `AccessibleObject.RuntimeIDFirstItem` `protected`pole. Od verze .NET Core 3,0 RC1 se změnila z `protected` verze na `internal` , aby byla zarovnaná s přístupností pole v .NET Framework.

#### <a name="version-introduced"></a>Představená verze

3,0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může mít vliv na to, zda jste vytvořili aplikaci .NET Core s typem, který je odvozen <xref:System.Windows.Forms.AccessibleObject> z a přistupuje k `RuntimeIDFirstItem` poli. V takovém případě můžete definovat místní konstantu následujícím způsobem:

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
