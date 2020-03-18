---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567760"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Národní prostředí "C" mapuje na invariantní národní prostředí

.NET Core 2.2 a starší verze závisí na výchozí chování JIP, který mapuje národní prostředí "C" na en_US_POSIX národní prostředí. Národní prostředí en_US_POSIX má nežádoucí řazení chování, protože nepodporuje porovnání řetězců bez rozlišování velkých a malých písmen. Vzhledem k tomu, že některé distribuce Linuxu nastavují národní prostředí "C" jako výchozí národní prostředí, uživatelé měli neočekávané chování.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3.0 se mapování národního prostředí "C" změnilo tak, aby místo en_US_POSIX používalo národní prostředí Invariant. Národní prostředí "C" invariantní mapování je také použita pro windows konzistence.

Mapování "C" na en_US_POSIX kultury způsobilzmatek zákazníka, protože en_US_POSIX nepodporuje operace řazení a vyhledávání bez rozlišování malých a velkých písmen. Vzhledem k tomu, že národní prostředí "C" se používá jako výchozí národní prostředí v některých distribucích Linuxu, zákazníci zažili toto nežádoucí chování v těchto operačních systémech.

#### <a name="version-introduced"></a>Zavedená verze

3.0

### <a name="recommended-action"></a>Doporučená akce

Nic konkrétního víc než povědomí o této změně. Tato změna se týká pouze aplikací, které používají mapování národního prostředí "C".

### <a name="category"></a>Kategorie

Globalizace

### <a name="affected-apis"></a>Ovlivněná rozhraní API

Všechna kolace a jazyková prostředí API jsou ovlivněny touto změnou.

<!--

-->
