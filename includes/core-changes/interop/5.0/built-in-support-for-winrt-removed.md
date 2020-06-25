---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365640"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>Integrovaná podpora WinRT se odebere z rozhraní .NET.

Odeberou se Vestavěná podpora pro využití rozhraní API pro [Windows Runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) v rozhraní .NET.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 6

#### <a name="change-description"></a>Popis změny

Dřív CoreCLR mohl využívat [soubory Windows metadata (WinMD)](/uwp/winrt-cref/winmd-files) k aktivnímu a využívání typů WinRT. Od rozhraní .NET 5,0 nemůže CoreCLR nadále využívat soubory WinMD přímo.

Pokud se pokusíte odkazovat na nepodporované sestavení, získáte <xref:System.IO.FileNotFoundException> . Pokud aktivujete třídu WinRT, získáte <xref:System.PlatformNotSupportedException> .

Tato změna byla provedena z následujících důvodů:

- Takže WinRT se dá vyvíjet a zdokonalovat odděleně od .NET Runtime.
- Pro symetrie se systémy spolupráce, které jsou k dispozici pro jiné operační systémy, jako jsou iOS a Android.
- Pro využití dalších funkcí rozhraní .NET, jako jsou funkce C#, propojení mezilehlého jazyka (IL) a kompilace před časem (AOT).
- Pro zjednodušení základu kódu .NET Runtime.

#### <a name="recommended-action"></a>Doporučená akce

- Odeberte odkazy na [balíček Microsoft. Windows. SDK. Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) a nahraďte je odkazy na [balíček Microsoft.Windows.SDK.NET](https://www.nuget.org/packages/microsoft.windows.sdk.net).

- Použijte řetězec nástroje [C#/WinRT](/windows/uwp/csharp-winrt/) ke generování nebo přizpůsobení rozhraní API a typů WinRT v rozhraní .NET 5,0 a novějších verzích.

#### <a name="category"></a>Kategorie

Zprostředkovatel komunikace

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
