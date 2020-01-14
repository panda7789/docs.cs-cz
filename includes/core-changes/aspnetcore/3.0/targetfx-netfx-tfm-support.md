---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937281"
---
### <a name="target-framework-net-framework-support-dropped"></a>Target framework: .NET Framework support dropped

Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.

#### <a name="change-description"></a>Popis změny

.NET Framework 4.8 is the last major version of .NET Framework. New ASP.NET Core apps should be built on .NET Core. Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.

Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1). Support and servicing for 2.1 continues until at least August 21, 2021. This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy). Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).

For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected. They'll continue to support .NET Standard.

For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Version introduced

3,0

#### <a name="old-behavior"></a>Old behavior

ASP.NET Core apps could run on either .NET Core or .NET Framework.

#### <a name="new-behavior"></a>New behavior

ASP.NET Core apps can only be run on .NET Core.

#### <a name="recommended-action"></a>Doporučená akce

Proveďte jednu z následujících akcí:

- Keep your app on ASP.NET Core 2.1.
- Migrate your app and dependencies to .NET Core.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
