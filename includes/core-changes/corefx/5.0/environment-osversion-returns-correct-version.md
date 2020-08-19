---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558170"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion vrátí správnou verzi operačního systému.

<xref:System.Environment.OSVersion?displayProperty=nameWithType> Vrátí skutečnou verzi operačního systému (OS), nikoli například operační systém, který je vybrán pro kompatibilitu aplikací.

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> vrátí verzi operačního systému, která může být nesprávná, pokud je aplikace spuštěna v režimu kompatibility systému Windows. Další informace naleznete v tématu [GetVersionExA Function poznámky](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).

Počínaje platformou .NET 5,0 <xref:System.Environment.OSVersion?displayProperty=nameWithType> vrátí aktuální verzi operačního systému.

#### <a name="reason-for-change"></a>Důvod změny

Uživatelé této vlastnosti očekávají, že vrátí skutečnou verzi operačního systému. Většina aplikací .NET neurčuje jejich podporovanou verzi v manifestu aplikace, a proto z hostitele dotnet Získá výchozí podporovanou verzi. V důsledku toho je překrytí kompatibility pro aplikaci, na které běží, zřídka smysluplné. Když systém Windows uvolní novou verzi a starší hostitel dotnet se pořád používá, můžou tyto aplikace získat nesprávnou verzi operačního systému. Vrácení skutečné verze je v rámci očekávání vývojářů tohoto rozhraní API více vložené.

#### <a name="version-introduced"></a>Představená verze

5.0

#### <a name="recommended-action"></a>Doporučená akce

Zkontrolujte a otestujte jakýkoli kód, který používá <xref:System.Environment.OSVersion?displayProperty=nameWithType> k zajištění toho, aby se choval podle potřeby.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
