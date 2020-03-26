---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549593"
---
### <a name="target-framework-net-framework-support-dropped"></a>Cílová architektura: Podpora rozhraní .NET Framework byla vynechána.

Počínaje ASP.NET jádrem 3.0 je rozhraní .NET Framework nepodporovanou cílovou architekturou.

#### <a name="change-description"></a>Popis změny

Rozhraní .NET Framework 4.8 je poslední hlavní verzí rozhraní .NET Framework. Nové aplikace ASP.NET Core by měly být postaveny na .NET Core. Počínaje verzí .NET Core 3.0 si můžete myslet, ASP.NET Core 3.0 jako součást .NET Core.

Zákazníci používající ASP.NET Core s rozhraním .NET Framework mohou pokračovat plně podporovaným způsobem pomocí [verze 2.1 LTS](https://dotnet.microsoft.com/download/dotnet-core/2.1). Podpora a servis pro 2.1 pokračuje nejméně do srpna 21, 2021. Toto datum je tři roky po prohlášení o vydání LTS podle [zásad podpory .NET](https://dotnet.microsoft.com/platform/support-policy). Podpora balíčků ASP.NET Core 2.1 **v rozhraní .NET Framework** se rozšíří na neurčito, podobně jako [zásady údržby pro jiné ASP.NET architektury založené na balíčcích](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Další informace o přenosu z rozhraní .NET Framework do jádra .NET naleznete v [tématu Porting to .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions`balíčky (například protokolování, vkládání závislostí a konfigurace) a jádro entity frameworku nejsou ovlivněny. Budou i nadále podporovat standard .NET.

Další informace o motivaci k této změně naleznete [v původním příspěvku blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

ASP.NET core aplikace může běžet na rozhraní .NET Core nebo .NET Framework.

#### <a name="new-behavior"></a>Nové chování

ASP.NET základní aplikace lze spustit pouze na .NET Core.

#### <a name="recommended-action"></a>Doporučená akce

Proveďte jednu z následujících akcí:

- Mějte svou aplikaci na ASP.NET Core 2.1.
- Migrujte aplikaci a závislosti do jádra .NET Core.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
