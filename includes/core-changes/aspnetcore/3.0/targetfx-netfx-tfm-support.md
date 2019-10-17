---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394158"
---
### <a name="target-framework-net-framework-support-dropped"></a>Cílová architektura: Zahozená podpora .NET Framework

Počínaje ASP.NET Core 3,0 .NET Framework je Nepodporovaná Cílová architektura.

#### <a name="change-description"></a>Změnit popis

.NET Framework 4,8 je poslední hlavní verzí .NET Framework. Nové aplikace ASP.NET Core by měly být postavené na .NET Core. Od verze .NET Core 3,0 můžete si představit ASP.NET Core 3,0 jako součást .NET Core.

Zákazníci, kteří používají ASP.NET Core s .NET Framework, můžou v plně podporovaném způsobem i nadále používat [LTS vydání verze 2,1](https://www.microsoft.com/net/download/dotnet-core/2.1). Podpora a údržba pro 2,1 pokračuje do 21. srpna 2021. Toto datum je tři roky po deklaraci verze LTS podle [zásady podpory .NET](https://www.microsoft.com/net/platform/support-policy). Podpora pro balíčky ASP.NET Core 2,1 **v .NET Framework** se nebude zobrazovat po neomezenou dobu, podobně jako [zásady údržby pro jiné ASP.NET architektury založené na balíčku](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Další informace o přenosech z .NET Framework do .NET Core najdete v tématu [přenos do .NET Core](~/docs/core/porting/index.md).

balíčky `Microsoft.Extensions` (například protokolování, vkládání závislostí a konfigurace) a Entity Framework Core nejsou ovlivněny. Budou dál podporovat .NET Standard.

Další informace o motivaci této změny najdete v [původním blogovém příspěvku](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Aplikace ASP.NET Core mohou běžet buď na rozhraní .NET Core, nebo v .NET Framework.

#### <a name="new-behavior"></a>Nové chování

Aplikace ASP.NET Core lze spustit pouze v .NET Core.

#### <a name="recommended-action"></a>Doporučená akce

Proveďte jednu z následujících akcí:

- Udržujte svou aplikaci na ASP.NET Core 2,1.
- Migrujte svoji aplikaci a závislosti do .NET Core.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
