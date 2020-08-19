---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557959"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption. Group nepřijímá hodnotu null.

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> již nepřijímá hodnotu `null` . Pokud nastavíte vlastnost na hodnotu `null` , <xref:System.ArgumentNullException> je vyvolána.

#### <a name="version-introduced"></a>Představená verze

5.0

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET můžete nastavit <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> vlastnost na `null` . Pokud <xref:System.Net.Sockets.MulticastOption> je později předán do <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , modul runtime vyvolá <xref:System.NullReferenceException> .

V rozhraní .NET 5,0 a novějším <xref:System.ArgumentNullException> je vyvolána výjimka, pokud nastavíte vlastnost na hodnotu `null` .

#### <a name="reason-for-change"></a>Důvod změny

Aby byly v souladu s pokyny návrhu rozhraní, byla vlastnost aktualizována, aby vyvolala, <xref:System.ArgumentNullException> Pokud je hodnota `null` .

#### <a name="recommended-action"></a>Doporučená akce

Ujistěte se, že nejste nastaveni <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> na `null` .

#### <a name="category"></a>Kategorie

Sítě

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
