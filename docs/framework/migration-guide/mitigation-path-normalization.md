---
title: 'Omezení rizik: Normalizace cesta'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37241dd666a5d10eeb35bcbb4c9e09a5bc56f620
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176537"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="fc7ef-102">Omezení rizik: Normalizace cesta</span><span class="sxs-lookup"><span data-stu-id="fc7ef-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="fc7ef-103">Počínaje aplikací cíl [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně normalizace cestu v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="fc7ef-104">Co je cesta normalizace?</span><span class="sxs-lookup"><span data-stu-id="fc7ef-104">What is path normalization?</span></span>  
 <span data-ttu-id="fc7ef-105">Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="fc7ef-106">Normalizace obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="fc7ef-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="fc7ef-107">Kanonizace oddělovače komponentu a adresáře.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="fc7ef-108">Použití aktuální adresář pro relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="fc7ef-109">Hodnocení relativní adresáře (`.`) nebo nadřazený adresář (`..`) v cestě.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="fc7ef-110">Oříznutí zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="fc7ef-111">Změny</span><span class="sxs-lookup"><span data-stu-id="fc7ef-111">The changes</span></span>  
 <span data-ttu-id="fc7ef-112">Počínaje aplikací, které se zaměřují [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně normalizace cesta následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="fc7ef-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="fc7ef-113">Modul runtime odloží do operačního systému [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkce normalizace cesty.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="fc7ef-114">Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="fc7ef-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="fc7ef-115">Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro rozhraní API vstupně-výstupní operace souboru v mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="fc7ef-116">Modul runtime nelze ověřit zařízení syntaxe cesty.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="fc7ef-117">Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporované.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fc7ef-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="fc7ef-118">Impact</span></span>  
 <span data-ttu-id="fc7ef-119">Pro aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo později, tyto změny jsou standardně povoleny.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="fc7ef-120">By měl pomáhají zvýšit výkon při povolení metody pro přístup k dříve nedostupných cesty.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="fc7ef-121">Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, ale jsou spuštěna pod [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo později se tato změna nemá vliv.</span><span class="sxs-lookup"><span data-stu-id="fc7ef-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fc7ef-122">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="fc7ef-122">Mitigation</span></span>  
 <span data-ttu-id="fc7ef-123">Aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete vyjádřit výslovný nesouhlas tuto změnu a použít starší verzi normalizace přidáním následujícího kódu do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="fc7ef-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="fc7ef-124">Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo starší, ale jsou spuštěny na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části aplikace. konfigurační soubor:</span><span class="sxs-lookup"><span data-stu-id="fc7ef-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc7ef-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc7ef-125">See also</span></span>

- [<span data-ttu-id="fc7ef-126">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="fc7ef-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
