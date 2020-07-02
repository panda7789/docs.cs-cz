---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614461"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="89a94-101">Změny normalizace cesty</span><span class="sxs-lookup"><span data-stu-id="89a94-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="89a94-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="89a94-102">Details</span></span>

<span data-ttu-id="89a94-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, způsob, jakým se změnily cesty modulu runtime normalizovat. Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="89a94-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="89a94-104">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="89a94-104">Normalization typically involves:</span></span>

- <span data-ttu-id="89a94-105">Kanonizace součásti a oddělovače adresářů.</span><span class="sxs-lookup"><span data-stu-id="89a94-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="89a94-106">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="89a94-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="89a94-107">Vyhodnocuje se relativní adresář (.) nebo nadřazený adresář (..) v cestě.</span><span class="sxs-lookup"><span data-stu-id="89a94-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="89a94-108">Ořezávání zadaných znaků.</span><span class="sxs-lookup"><span data-stu-id="89a94-108">Trimming specified characters.</span></span>
<span data-ttu-id="89a94-109">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, jsou ve výchozím nastavení povolené následující změny normalizace cesty:</span><span class="sxs-lookup"><span data-stu-id="89a94-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="89a94-110">Modul runtime se odkládá na funkci [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) operačního systému k normalizaci cest.</span><span class="sxs-lookup"><span data-stu-id="89a94-110">The runtime defers to the operating system's [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="89a94-111">Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="89a94-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="89a94-112">Podpora syntaxe cest zařízení v úplném vztahu důvěryhodnosti, včetně `\\.\` a, pro vstupně-výstupní rozhraní API souborů v mscorlib.dll `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="89a94-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="89a94-113">Modul runtime neověřuje cestu k syntaxi zařízení.</span><span class="sxs-lookup"><span data-stu-id="89a94-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="89a94-114">Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.</span><span class="sxs-lookup"><span data-stu-id="89a94-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="89a94-115">Tyto změny zlepšují výkon a zároveň umožňují přístup k dříve nepřístupným cestám metod.</span><span class="sxs-lookup"><span data-stu-id="89a94-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="89a94-116">Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.</span><span class="sxs-lookup"><span data-stu-id="89a94-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="89a94-117">Návrh</span><span class="sxs-lookup"><span data-stu-id="89a94-117">Suggestion</span></span>

<span data-ttu-id="89a94-118">Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do `<runtime>` oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="89a94-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="89a94-119">Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do `<runtime>` oddílu souboru Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="89a94-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="89a94-120">Name</span><span class="sxs-lookup"><span data-stu-id="89a94-120">Name</span></span>    | <span data-ttu-id="89a94-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="89a94-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="89a94-122">Rozsah</span><span class="sxs-lookup"><span data-stu-id="89a94-122">Scope</span></span>   | <span data-ttu-id="89a94-123">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="89a94-123">Minor</span></span>       |
| <span data-ttu-id="89a94-124">Verze</span><span class="sxs-lookup"><span data-stu-id="89a94-124">Version</span></span> | <span data-ttu-id="89a94-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="89a94-125">4.6.2</span></span>       |
| <span data-ttu-id="89a94-126">Typ</span><span class="sxs-lookup"><span data-stu-id="89a94-126">Type</span></span>    | <span data-ttu-id="89a94-127">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="89a94-127">Retargeting</span></span> |
