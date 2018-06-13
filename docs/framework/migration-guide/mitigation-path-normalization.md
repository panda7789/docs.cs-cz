---
title: 'Omezení rizik: Cesta normalizaci'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36433dcce1e47b329f5407e86ce3923a44cb6444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389505"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="e4856-102">Omezení rizik: Cesta normalizaci</span><span class="sxs-lookup"><span data-stu-id="e4856-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="e4856-103">Počínaje aplikací cíl [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně cesty normalizace v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4856-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="e4856-104">Co je cesta normalizaci?</span><span class="sxs-lookup"><span data-stu-id="e4856-104">What is path normalization?</span></span>  
 <span data-ttu-id="e4856-105">Normalizace cestu zahrnuje úprava řetězec, který identifikuje cesta nebo soubor, který vyhovuje na cestu na cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="e4856-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="e4856-106">Normalizaci obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="e4856-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="e4856-107">Kanonizace oddělovače součásti a adresář.</span><span class="sxs-lookup"><span data-stu-id="e4856-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="e4856-108">Použití aktuálního adresáře na relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="e4856-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="e4856-109">Vyhodnocení adresáři relativní (`.`) nebo nadřazený adresář (`..`) v cestě.</span><span class="sxs-lookup"><span data-stu-id="e4856-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="e4856-110">Oříznutí zadané znaky.</span><span class="sxs-lookup"><span data-stu-id="e4856-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="e4856-111">Změny</span><span class="sxs-lookup"><span data-stu-id="e4856-111">The changes</span></span>  
 <span data-ttu-id="e4856-112">Počínaje aplikací cílených [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cesta normalizaci došlo ke změně následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="e4856-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="e4856-113">Modul runtime odkládat údaje v operačním systému [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) funkce, která má normalizuje cesty.</span><span class="sxs-lookup"><span data-stu-id="e4856-113">The runtime defers to the operating system's [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="e4856-114">Už normalizace zahrnuje ořezávání konec directory segmenty (například mezeru na konci názvu adresáře).</span><span class="sxs-lookup"><span data-stu-id="e4856-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="e4856-115">Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro soubor vstupně-výstupních operací rozhraní API v mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="e4856-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="e4856-116">Modul runtime neověřuje zařízení syntaxe cesty.</span><span class="sxs-lookup"><span data-stu-id="e4856-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="e4856-117">Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporováno.</span><span class="sxs-lookup"><span data-stu-id="e4856-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e4856-118">Dopad</span><span class="sxs-lookup"><span data-stu-id="e4856-118">Impact</span></span>  
 <span data-ttu-id="e4856-119">Pro aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější, jsou tyto změny na ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e4856-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="e4856-120">Jejich měli zlepšit výkon při povolení metody pro přístup k dřív nepřístupný cesty.</span><span class="sxs-lookup"><span data-stu-id="e4856-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="e4856-121">Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, ale jsou spuštěno [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější se tato změna nemá vliv.</span><span class="sxs-lookup"><span data-stu-id="e4856-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e4856-122">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="e4856-122">Mitigation</span></span>  
 <span data-ttu-id="e4856-123">Aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete zamítnutí této změny a použít starší verzi normalizace přidáním následujícího [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="e4856-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="e4856-124">Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo starší ale běží na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete povolit změny cesty normalizaci přidáním následující řádek do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část aplikace. konfigurační soubor:</span><span class="sxs-lookup"><span data-stu-id="e4856-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4856-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4856-125">See Also</span></span>  
 [<span data-ttu-id="e4856-126">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="e4856-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
