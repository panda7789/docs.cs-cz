---
title: 'Zmírnění: normalizace cest'
description: Přečtěte si, jak se v .NET Framework změnila normalizace cesty v od aplikací, které cílí na .NET Framework 4.6.2.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475213"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="7f0b1-103">Zmírnění: normalizace cest</span><span class="sxs-lookup"><span data-stu-id="7f0b1-103">Mitigation: Path Normalization</span></span>
<span data-ttu-id="7f0b1-104">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se změnila normalizace cest v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="7f0b1-105">Co je normalizace cest?</span><span class="sxs-lookup"><span data-stu-id="7f0b1-105">What is path normalization?</span></span>  
 <span data-ttu-id="7f0b1-106">Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="7f0b1-107">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="7f0b1-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="7f0b1-108">Kanonizace součásti a oddělovače adresářů.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="7f0b1-109">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="7f0b1-110">Vyhodnocení relativního adresáře ( `.` ) nebo nadřazeného adresáře ( `..` ) v cestě.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="7f0b1-111">Ořezávání zadaných znaků.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="7f0b1-112">Změny</span><span class="sxs-lookup"><span data-stu-id="7f0b1-112">The changes</span></span>  
 <span data-ttu-id="7f0b1-113">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="7f0b1-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="7f0b1-114">Modul runtime se odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému k normalizaci cest.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="7f0b1-115">Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="7f0b1-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="7f0b1-116">Podpora syntaxe cest zařízení v úplném vztahu důvěryhodnosti, včetně `\\.\` a, pro vstupně-výstupní rozhraní API souborů v mscorlib.dll `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="7f0b1-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="7f0b1-117">Modul runtime neověřuje cestu k syntaxi zařízení.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="7f0b1-118">Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7f0b1-119">Dopad</span><span class="sxs-lookup"><span data-stu-id="7f0b1-119">Impact</span></span>  

<span data-ttu-id="7f0b1-120">U aplikací, které cílí na .NET Framework 4.6.2 nebo novějším, jsou tyto změny ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="7f0b1-121">Měli byste zvýšit výkon a zároveň povolit přístup k dříve nepřístupným cestám k těmto metodám.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="7f0b1-122">Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.</span><span class="sxs-lookup"><span data-stu-id="7f0b1-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="7f0b1-123">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="7f0b1-123">Mitigation</span></span>  
 <span data-ttu-id="7f0b1-124">Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="7f0b1-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="7f0b1-125">Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu souboru Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="7f0b1-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f0b1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f0b1-126">See also</span></span>

- [<span data-ttu-id="7f0b1-127">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="7f0b1-127">Application compatibility</span></span>](application-compatibility.md)
