---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721281"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem

Od verze .NET Core 3,0 RC1 se přístupnost pro `AccessibleObject.RuntimeIDFirstItem` změnila z `protected` na `internal` .

#### <a name="change-description"></a>Popis změny

Od verze .NET Core 3,0 Preview 4 `AccessibleObject.RuntimeIDFirstItem` bylo pole `protected` . Od verze .NET Core 3,0 RC1 se změnila z verze `protected` na, `internal` aby byla zarovnaná s přístupností pole v .NET Framework.

#### <a name="version-introduced"></a>Představená verze

3,0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může mít vliv na to, zda jste vytvořili aplikaci .NET Core s typem, který je odvozen z <xref:System.Windows.Forms.AccessibleObject> a přistupuje k `RuntimeIDFirstItem` poli. V takovém případě můžete definovat místní konstantu následujícím způsobem:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Nedá se detekovat přes analýzu rozhraní API.

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
