---
title: Zmírnění Normalizace cest
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5ea69d80a225adfc2f409e8303ee1c241398db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779345"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="85ee4-102">Zmírnění Normalizace cest</span><span class="sxs-lookup"><span data-stu-id="85ee4-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="85ee4-103">Počínaje aplikacemi cílíte na .NET Framework 4.6.2, normalizace cest v .NET Framework se změnila.</span><span class="sxs-lookup"><span data-stu-id="85ee4-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="85ee4-104">Co je normalizace cest?</span><span class="sxs-lookup"><span data-stu-id="85ee4-104">What is path normalization?</span></span>  
 <span data-ttu-id="85ee4-105">Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="85ee4-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="85ee4-106">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="85ee4-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="85ee4-107">Kanonizace součásti a oddělovače adresářů.</span><span class="sxs-lookup"><span data-stu-id="85ee4-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="85ee4-108">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="85ee4-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="85ee4-109">Vyhodnocení relativního adresáře (`.`) nebo nadřazeného adresáře (`..`) v cestě.</span><span class="sxs-lookup"><span data-stu-id="85ee4-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="85ee4-110">Ořezávání zadaných znaků.</span><span class="sxs-lookup"><span data-stu-id="85ee4-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="85ee4-111">Změny</span><span class="sxs-lookup"><span data-stu-id="85ee4-111">The changes</span></span>  
 <span data-ttu-id="85ee4-112">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="85ee4-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="85ee4-113">Modul runtime se odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému k normalizaci cest.</span><span class="sxs-lookup"><span data-stu-id="85ee4-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="85ee4-114">Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="85ee4-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="85ee4-115">Podpora syntaxe cesty zařízení v úplném vztahu důvěryhodnosti, `\\.\` včetně a, pro vstupně-výstupní rozhraní API souborů v knihovně Mscorlib `\\?\`. dll.</span><span class="sxs-lookup"><span data-stu-id="85ee4-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="85ee4-116">Modul runtime neověřuje cestu k syntaxi zařízení.</span><span class="sxs-lookup"><span data-stu-id="85ee4-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="85ee4-117">Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.</span><span class="sxs-lookup"><span data-stu-id="85ee4-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="85ee4-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="85ee4-118">Impact</span></span>  

<span data-ttu-id="85ee4-119">U aplikací, které cílí na .NET Framework 4.6.2 nebo novějším, jsou tyto změny ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="85ee4-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="85ee4-120">Měli byste zvýšit výkon a zároveň povolit přístup k dříve nepřístupným cestám k těmto metodám.</span><span class="sxs-lookup"><span data-stu-id="85ee4-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="85ee4-121">Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.</span><span class="sxs-lookup"><span data-stu-id="85ee4-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="85ee4-122">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="85ee4-122">Mitigation</span></span>  
 <span data-ttu-id="85ee4-123">Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do [ \<části > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) v konfiguračním souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="85ee4-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="85ee4-124">Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do [ \<oddílu > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) v aplikaci. konfigurace souborů</span><span class="sxs-lookup"><span data-stu-id="85ee4-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85ee4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ee4-125">See also</span></span>

- [<span data-ttu-id="85ee4-126">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="85ee4-126">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
