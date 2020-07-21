---
title: 'Zmírnění: snímky PNG v objektech ikon'
description: Naučte se konfigurovat chování snímků PNG v objektech ikon, pokud nové chování zahrnuté v .NET Framework 4,6 a novějším je nežádoucí.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: b7ba2951a38ee2d1c7a9b1fc45c5a81d24986a85
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475434"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="627fd-103">Zmírnění: snímky PNG v objektech ikon</span><span class="sxs-lookup"><span data-stu-id="627fd-103">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="627fd-104">Počínaje .NET Framework 4,6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda úspěšně převede ikony s snímky PNG do <xref:System.Drawing.Bitmap> objektů.</span><span class="sxs-lookup"><span data-stu-id="627fd-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="627fd-105">V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda <xref:System.ArgumentOutOfRangeException> výjimku, pokud <xref:System.Drawing.Icon> objekt obsahuje snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="627fd-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="627fd-106">Dopad</span><span class="sxs-lookup"><span data-stu-id="627fd-106">Impact</span></span>  
 <span data-ttu-id="627fd-107">Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují speciální zpracování pro <xref:System.ArgumentOutOfRangeException> výjimku, která je vyvolána, když <xref:System.Drawing.Icon> objekt má snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="627fd-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="627fd-108">Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="627fd-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="627fd-109">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="627fd-109">Mitigation</span></span>  
 <span data-ttu-id="627fd-110">Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="627fd-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="627fd-111">Pokud app.config soubor již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena s `value` atributem takto:</span><span class="sxs-lookup"><span data-stu-id="627fd-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="627fd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="627fd-112">See also</span></span>

- [<span data-ttu-id="627fd-113">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="627fd-113">Application compatibility</span></span>](application-compatibility.md)
