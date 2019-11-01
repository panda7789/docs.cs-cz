---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198395"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Národní prostředí jazyka C se mapuje na neutrální národní prostředí.

.NET Core 2,2 a starší verze závisí na výchozím chování ICU, které mapuje národní prostředí "C" na národní prostředí en_US_POSIX. Národní prostředí en_US_POSIX má nežádoucí chování kolace, protože nepodporuje porovnávání řetězců bez rozlišování velkých a malých písmen. Vzhledem k tomu, že některá distribuce systému Linux nastavila národní prostředí "C" jako výchozí národní prostředí, došlo k neočekávanému chování uživatelů.

#### <a name="change-description"></a>Změnit popis

Počínaje rozhraním .NET Core 3,0 se mapování národního prostředí "C" změnilo na použití neutrálního národního prostředí namísto en_US_POSIX. Národní prostředí "C" na invariantní mapování je také použito pro systém Windows pro zajištění konzistence.

Mapování "C" na jazykovou verzi en_US_POSIX způsobilo nejasnost zákazníka, protože en_US_POSIX nepodporuje řazení a vyhledávání řetězců bez rozlišení velkých a malých písmen. Vzhledem k tomu, že národní prostředí "C" se používá jako výchozí národní prostředí v některých distribuceích Linux, zákazníci narazili na toto neočekávané chování na tyto operační systémy.

#### <a name="version-introduced"></a>Představená verze

3.0

### <a name="recommended-action"></a>Doporučená akce

Nic nespecifické pro víc, než je povědomí o této změně. Tato změna ovlivní pouze aplikace, které používají mapování národního prostředí "C".

### <a name="category"></a>Kategorie

Globalizace

### <a name="affected-apis"></a>Ovlivněná rozhraní API

Tato změna ovlivní všechna rozhraní API pro kolaci a kulturu.

<!--

-->
