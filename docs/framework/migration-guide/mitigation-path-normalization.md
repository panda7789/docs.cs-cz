---
title: 'Omezení rizik: Normalizace cesta'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1c704113c8e05e493cdb3ef24f6376ab54b1cb
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251117"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="0da3b-102">Omezení rizik: Normalizace cesta</span><span class="sxs-lookup"><span data-stu-id="0da3b-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="0da3b-103">Počínaje aplikací cílového rozhraní .NET Framework 4.6.2, cesta normalizace v rozhraní .NET Framework byl změněn.</span><span class="sxs-lookup"><span data-stu-id="0da3b-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="0da3b-104">Co je cesta normalizace?</span><span class="sxs-lookup"><span data-stu-id="0da3b-104">What is path normalization?</span></span>  
 <span data-ttu-id="0da3b-105">Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="0da3b-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="0da3b-106">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="0da3b-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="0da3b-107">Kanonizace oddělovače komponentu a adresáře.</span><span class="sxs-lookup"><span data-stu-id="0da3b-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="0da3b-108">Použití aktuální adresář pro relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="0da3b-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="0da3b-109">Hodnocení relativní adresáře (`.`) nebo nadřazený adresář (`..`) v cestě.</span><span class="sxs-lookup"><span data-stu-id="0da3b-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="0da3b-110">Oříznutí zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="0da3b-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="0da3b-111">Změny</span><span class="sxs-lookup"><span data-stu-id="0da3b-111">The changes</span></span>  
 <span data-ttu-id="0da3b-112">Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, cesta normalizace došlo ke změně následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="0da3b-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="0da3b-113">Modul runtime odloží do operačního systému [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkce normalizace cesty.</span><span class="sxs-lookup"><span data-stu-id="0da3b-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="0da3b-114">Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="0da3b-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="0da3b-115">Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro rozhraní API vstupně-výstupní operace souboru v mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="0da3b-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="0da3b-116">Modul runtime nelze ověřit zařízení syntaxe cesty.</span><span class="sxs-lookup"><span data-stu-id="0da3b-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="0da3b-117">Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporované.</span><span class="sxs-lookup"><span data-stu-id="0da3b-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0da3b-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="0da3b-118">Impact</span></span>  

<span data-ttu-id="0da3b-119">Pro aplikace, které cílí .NET Framework 4.6.2 nebo novější, tyto změny jsou standardně povoleny.</span><span class="sxs-lookup"><span data-stu-id="0da3b-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="0da3b-120">By měl pomáhají zvýšit výkon při povolení metody pro přístup k dříve nedostupných cesty.</span><span class="sxs-lookup"><span data-stu-id="0da3b-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="0da3b-121">Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější se tato změna nemá vliv.</span><span class="sxs-lookup"><span data-stu-id="0da3b-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0da3b-122">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="0da3b-122">Mitigation</span></span>  
 <span data-ttu-id="0da3b-123">Aplikace, které cílí .NET Framework 4.6.2 nebo novější můžete zrušit to změnit a použít starší verzi normalizace přidáním následujícího [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="0da3b-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="0da3b-124">Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část soubor .configuration aplikace:</span><span class="sxs-lookup"><span data-stu-id="0da3b-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0da3b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0da3b-125">See also</span></span>

- [<span data-ttu-id="0da3b-126">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="0da3b-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
