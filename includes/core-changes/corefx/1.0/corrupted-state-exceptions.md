---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135620"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>Zpracování výjimek poškozených stavů se nepodporuje.

Manipulace s poškozenými výjimkami stavu procesu v rozhraní .NET Core není podporována.

#### <a name="change-description"></a>Popis změny

Dříve mohly být poškozené výjimky stavu procesu zachyceny a zpracovány obslužnými rutinami výjimek spravovaného kódu, například pomocí příkazu [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) v jazyce C#.

Počínaje rozhraním .NET Core 1,0 nemohou výjimky stavu poškozeného procesu zpracovat spravovaným kódem. Modul CLR (Common Language Runtime) neposkytuje do spravovaného kódu výjimky nepoškozených stavových procesů.

#### <a name="version-introduced"></a>Představená verze

1.0

#### <a name="recommended-action"></a>Doporučená akce

Vyhněte se nutnosti zpracovat výjimky poškozeného procesu tím, že se postarou o situace, které k nim mají zájem. Pokud je nezbytně nutné pro zpracování výjimek stavu poškozeného procesu, napište obslužnou rutinu výjimky v kódu C nebo C++.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [element legacyCorruptedStateExceptionsPolicy](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
