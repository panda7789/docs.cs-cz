---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302703"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector \<T> vždy vyvolá NotSupportedException pro nepodporované typy

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> nyní vždy vyvolá výjimku <xref:System.NotSupportedException> pro nepodporované parametry typu.

#### <a name="change-description"></a>Popis změny

Dřív členové by nemuseli <xref:System.Numerics.Vector%601> vždycky vyvolat výjimku, kdy se nejedná o <xref:System.NotSupportedException> `T` [nepodporovaný typ](#unsupported-types). Výjimka se vyvolala vždycky kvůli cestám kódu, které podporují hardwarovou akceleraci. Například `Vector<bool> + Vector<bool>` vrátí `default` místo vyvolání výjimky na platformách, které nemají žádnou hardwarovou akceleraci, jako je například ARM32. Pro nepodporované typy <xref:System.Numerics.Vector%601> Členové nakazují nekonzistentní chování napříč různými platformami a hardwarovými konfiguracemi.

Počínaje platformou .NET 5,0 <xref:System.Numerics.Vector%601> Členové vždy vyvolají <xref:System.NotSupportedException> u všech konfigurací hardwaru, pokud `T` není podporovaným typem.

##### <a name="unsupported-types"></a>Nepodporované typy

Podporované typy pro parametr typu <xref:System.Numerics.Vector%601> jsou:

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Podporované typy se nezměnily, ale mohou být v budoucnu změněny.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Nepoužívejte nepodporovaný typ pro parametr typu <xref:System.Numerics.Vector%601> .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Numerics.Vector%601?displayProperty=fullName> a všechny její členy

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
