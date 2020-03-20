---
title: 'Zmírnění: Normalizace cesty'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181236"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="4c991-102">Zmírnění: Normalizace cesty</span><span class="sxs-lookup"><span data-stu-id="4c991-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="4c991-103">Počínaje aplikacemi cíl .NET Framework 4.6.2, cesta normalizace v rozhraní .NET Framework se změnil.</span><span class="sxs-lookup"><span data-stu-id="4c991-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="4c991-104">Co je normalizace cesty?</span><span class="sxs-lookup"><span data-stu-id="4c991-104">What is path normalization?</span></span>  
 <span data-ttu-id="4c991-105">Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby odpovídalplatné cestě v cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="4c991-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="4c991-106">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="4c991-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="4c991-107">Oddělovače komponent a adresářů canonicalizing.</span><span class="sxs-lookup"><span data-stu-id="4c991-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="4c991-108">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="4c991-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="4c991-109">Vyhodnocení relativního adresáře (`.`)`..`nebo nadřazeného adresáře ( ) v cestě.</span><span class="sxs-lookup"><span data-stu-id="4c991-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="4c991-110">Oříznutí určených znaků.</span><span class="sxs-lookup"><span data-stu-id="4c991-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="4c991-111">Změny</span><span class="sxs-lookup"><span data-stu-id="4c991-111">The changes</span></span>  
 <span data-ttu-id="4c991-112">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="4c991-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="4c991-113">Runtime odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému normalizovat cesty.</span><span class="sxs-lookup"><span data-stu-id="4c991-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="4c991-114">Normalizace již nezahrnuje oříznutí konce segmentů adresáře (například mezeru na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="4c991-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="4c991-115">Podpora syntaxe cesty zařízení v `\\.\` plném vztahu důvěryhodnosti, včetně rozhraní API vstupně-nosných souborů v souboru mscorlib.dll . `\\?\`</span><span class="sxs-lookup"><span data-stu-id="4c991-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="4c991-116">Runtime neověřuje cesty syntaxe zařízení.</span><span class="sxs-lookup"><span data-stu-id="4c991-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="4c991-117">Je podporováno použití syntaxe zařízení pro přístup k alternativním datovým proudům.</span><span class="sxs-lookup"><span data-stu-id="4c991-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4c991-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="4c991-118">Impact</span></span>  

<span data-ttu-id="4c991-119">U aplikací, které cílí na rozhraní .NET Framework 4.6.2 nebo novější, jsou tyto změny ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="4c991-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="4c991-120">Měly by zlepšit výkon a zároveň umožnit metodám přístup k dříve nepřístupným cestám.</span><span class="sxs-lookup"><span data-stu-id="4c991-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="4c991-121">Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rámci rozhraní .NET Framework 4.6.2 nebo novější, nejsou touto změnou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="4c991-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="4c991-122">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="4c991-122">Mitigation</span></span>  
 <span data-ttu-id="4c991-123">Aplikace, které cílí na rozhraní .NET Framework 4.6.2 nebo novější, se mohou odhlásit z této změny a používat starší normalizaci přidáním následujících položek do části konfigurace aplikace [ \<>runtime:](../configure-apps/file-schema/runtime/runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c991-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="4c991-124">Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší, ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novějším, mohou povolit změny normalizace cesty přidáním následujícího řádku do části [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru konfigurace aplikace:</span><span class="sxs-lookup"><span data-stu-id="4c991-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c991-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c991-125">See also</span></span>

- [<span data-ttu-id="4c991-126">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="4c991-126">Application compatibility</span></span>](application-compatibility.md)
