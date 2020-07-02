---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614516"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters. ParentWindowHandle teď očekává hodnotu HWND.

#### <a name="details"></a>Podrobnosti

<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>Hodnota zavedená v .NET Framework 2,0 umožňuje aplikaci registrovat nadřazené okno s hodnotou popisovače, takže jakékoli uživatelské rozhraní potřebné pro přístup ke klíči (například dialogové okno výzvy k zadání kódu PIN nebo vyjádření souhlasu) se otevře jako modální podřízená položka v zadaném okně. Počínaje aplikacemi, které cílí na .NET Framework 4,7, může model Windows Forms aplikace nastavit <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> vlastnost s kódem podobným následujícímu:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

V předchozích verzích .NET Framework se očekávala hodnota <xref:System.IntPtr?displayProperty=fullName> představující umístění v paměti, kde se nachází hodnota [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) . Nastavení vlastnosti na formu. Popisovač v systému Windows 7 a starších verzích neměl žádný účinek, ale v systému Windows 8 a novějších verzích má za následek &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : parametr je nesprávný.&quot;

#### <a name="suggestion"></a>Návrh

Aplikace cílené na .NET Framework 4,7 nebo vyšší, které chtějí registrovat relaci nadřazeného okna, jsou doporučovány pro použití zjednodušené formy:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

Uživatelé, kteří zjistili, že správná hodnota, která má být předána, byla adresa místa v paměti, která je schopná zadat hodnotu, a `form.Handle` to nastavením přepínače AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` na `true` :

- Díky programovému nastavení přepínačů kompatibility na AppContext, jak je popsáno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).
- Přidáním následujícího řádku do `<runtime>` části souboru app.config:

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

Naopak, uživatelé, kteří se chtějí vyjádřit k novému chování v prostředí .NET Framework 4,7 runtime v případě, že aplikace načte starší verze .NET Framework, může nastavit přepínač AppContext na `false` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,7         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
