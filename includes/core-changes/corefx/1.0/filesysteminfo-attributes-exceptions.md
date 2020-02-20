---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449392"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException vyvolaná atributy SystemInfo.

V rozhraní .NET Core je vyvolána <xref:System.UnauthorizedAccessException>, když se volající pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu.

#### <a name="change-description"></a>Změnit popis

V .NET Framework je vyvolána <xref:System.ArgumentException> při pokusu volajícího o nastavení hodnoty atributu souboru v <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, ale nemá oprávnění k zápisu. V .NET Core je místo toho vyvolána <xref:System.UnauthorizedAccessException>. (V rozhraní .NET Core je <xref:System.ArgumentException> stále vyvolána, pokud se volající pokusí nastavit neplatný atribut souboru.)

#### <a name="version-introduced"></a>Představená verze

1.0

#### <a name="recommended-action"></a>Doporučená akce

V případě potřeby upravte jakékoli příkazy `catch` k zachytávání <xref:System.UnauthorizedAccessException> namísto, případně i <xref:System.ArgumentException>.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
