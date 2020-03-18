---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449392"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes

V .NET Core <xref:System.UnauthorizedAccessException> je vyvolána, když se volající pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET <xref:System.ArgumentException> Framework je vyvolána, když se volající <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu. V .NET Core <xref:System.UnauthorizedAccessException> je místo toho vyvolána. (V .NET Core, je <xref:System.ArgumentException> stále vyvolána, pokud volající pokusí nastavit atribut neplatný soubor.)

#### <a name="version-introduced"></a>Zavedená verze

1.0

#### <a name="recommended-action"></a>Doporučená akce

Upravte `catch` všechny příkazy zachytit <xref:System.UnauthorizedAccessException> místo nebo vedle <xref:System.ArgumentException>, podle potřeby.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
