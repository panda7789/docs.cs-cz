---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021811"
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

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
