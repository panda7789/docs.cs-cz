---
title: 'Zmírnění: normalizace cest'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 9ec34d8215c88329066b1cb86da018db82e16c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126214"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="c694c-102">Zmírnění: normalizace cest</span><span class="sxs-lookup"><span data-stu-id="c694c-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="c694c-103">Počínaje aplikacemi cílíte na .NET Framework 4.6.2, normalizace cest v .NET Framework se změnila.</span><span class="sxs-lookup"><span data-stu-id="c694c-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="c694c-104">Co je normalizace cest?</span><span class="sxs-lookup"><span data-stu-id="c694c-104">What is path normalization?</span></span>  
 <span data-ttu-id="c694c-105">Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="c694c-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="c694c-106">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="c694c-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="c694c-107">Kanonizace součásti a oddělovače adresářů.</span><span class="sxs-lookup"><span data-stu-id="c694c-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="c694c-108">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="c694c-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="c694c-109">Vyhodnocení relativního adresáře (`.`) nebo nadřazeného adresáře (`..`) v cestě.</span><span class="sxs-lookup"><span data-stu-id="c694c-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="c694c-110">Ořezávání zadaných znaků.</span><span class="sxs-lookup"><span data-stu-id="c694c-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="c694c-111">Změny</span><span class="sxs-lookup"><span data-stu-id="c694c-111">The changes</span></span>  
 <span data-ttu-id="c694c-112">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="c694c-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="c694c-113">Modul runtime se odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému k normalizaci cest.</span><span class="sxs-lookup"><span data-stu-id="c694c-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="c694c-114">Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="c694c-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="c694c-115">Podpora syntaxe cesty zařízení v úplném vztahu důvěryhodnosti, včetně `\\.\` a, pro vstupně-výstupní rozhraní API souborů v knihovně Mscorlib. dll `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="c694c-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="c694c-116">Modul runtime neověřuje cestu k syntaxi zařízení.</span><span class="sxs-lookup"><span data-stu-id="c694c-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="c694c-117">Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.</span><span class="sxs-lookup"><span data-stu-id="c694c-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c694c-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="c694c-118">Impact</span></span>  

<span data-ttu-id="c694c-119">U aplikací, které cílí na .NET Framework 4.6.2 nebo novějším, jsou tyto změny ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="c694c-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="c694c-120">Měli byste zvýšit výkon a zároveň povolit přístup k dříve nepřístupným cestám k těmto metodám.</span><span class="sxs-lookup"><span data-stu-id="c694c-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="c694c-121">Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.</span><span class="sxs-lookup"><span data-stu-id="c694c-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c694c-122">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="c694c-122">Mitigation</span></span>  
 <span data-ttu-id="c694c-123">Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do části [\<modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="c694c-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="c694c-124">Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do části [> modulu runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) souboru Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="c694c-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c694c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c694c-125">See also</span></span>

- [<span data-ttu-id="c694c-126">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="c694c-126">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
