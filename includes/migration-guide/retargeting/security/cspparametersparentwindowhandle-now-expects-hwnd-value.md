---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614516"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="0c61b-101">CspParameters. ParentWindowHandle teď očekává hodnotu HWND.</span><span class="sxs-lookup"><span data-stu-id="0c61b-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="0c61b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0c61b-102">Details</span></span>

<span data-ttu-id="0c61b-103"><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>Hodnota zavedená v .NET Framework 2,0 umožňuje aplikaci registrovat nadřazené okno s hodnotou popisovače, takže jakékoli uživatelské rozhraní potřebné pro přístup ke klíči (například dialogové okno výzvy k zadání kódu PIN nebo vyjádření souhlasu) se otevře jako modální podřízená položka v zadaném okně. Počínaje aplikacemi, které cílí na .NET Framework 4,7, může model Windows Forms aplikace nastavit <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> vlastnost s kódem podobným následujícímu:</span><span class="sxs-lookup"><span data-stu-id="0c61b-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="0c61b-104">V předchozích verzích .NET Framework se očekávala hodnota <xref:System.IntPtr?displayProperty=fullName> představující umístění v paměti, kde se nachází hodnota [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) .</span><span class="sxs-lookup"><span data-stu-id="0c61b-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="0c61b-105">Nastavení vlastnosti na formu. Popisovač v systému Windows 7 a starších verzích neměl žádný účinek, ale v systému Windows 8 a novějších verzích má za následek &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : parametr je nesprávný.&quot;</span><span class="sxs-lookup"><span data-stu-id="0c61b-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0c61b-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="0c61b-106">Suggestion</span></span>

<span data-ttu-id="0c61b-107">Aplikace cílené na .NET Framework 4,7 nebo vyšší, které chtějí registrovat relaci nadřazeného okna, jsou doporučovány pro použití zjednodušené formy:</span><span class="sxs-lookup"><span data-stu-id="0c61b-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="0c61b-108">Uživatelé, kteří zjistili, že správná hodnota, která má být předána, byla adresa místa v paměti, která je schopná zadat hodnotu, a `form.Handle` to nastavením přepínače AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` na `true` :</span><span class="sxs-lookup"><span data-stu-id="0c61b-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="0c61b-109">Díky programovému nastavení přepínačů kompatibility na AppContext, jak je popsáno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="0c61b-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="0c61b-110">Přidáním následujícího řádku do `<runtime>` části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="0c61b-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="0c61b-111">Naopak, uživatelé, kteří se chtějí vyjádřit k novému chování v prostředí .NET Framework 4,7 runtime v případě, že aplikace načte starší verze .NET Framework, může nastavit přepínač AppContext na `false` .</span><span class="sxs-lookup"><span data-stu-id="0c61b-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="0c61b-112">Name</span><span class="sxs-lookup"><span data-stu-id="0c61b-112">Name</span></span>    | <span data-ttu-id="0c61b-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0c61b-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0c61b-114">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0c61b-114">Scope</span></span>   | <span data-ttu-id="0c61b-115">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="0c61b-115">Minor</span></span>       |
| <span data-ttu-id="0c61b-116">Verze</span><span class="sxs-lookup"><span data-stu-id="0c61b-116">Version</span></span> | <span data-ttu-id="0c61b-117">4,7</span><span class="sxs-lookup"><span data-stu-id="0c61b-117">4.7</span></span>         |
| <span data-ttu-id="0c61b-118">Typ</span><span class="sxs-lookup"><span data-stu-id="0c61b-118">Type</span></span>    | <span data-ttu-id="0c61b-119">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0c61b-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0c61b-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0c61b-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
