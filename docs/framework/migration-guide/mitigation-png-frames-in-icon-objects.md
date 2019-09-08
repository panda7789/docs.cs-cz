---
title: Zmírnění Snímky PNG v objektech ikon
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789971"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="9a434-102">Zmírnění Snímky PNG v objektech ikon</span><span class="sxs-lookup"><span data-stu-id="9a434-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="9a434-103">Počínaje .NET Framework 4,6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikony s snímky PNG do <xref:System.Drawing.Bitmap> objektů.</span><span class="sxs-lookup"><span data-stu-id="9a434-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="9a434-104">V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> vyvolá metoda výjimku, pokud <xref:System.Drawing.Icon> objekt obsahuje snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="9a434-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9a434-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="9a434-105">Impact</span></span>  
 <span data-ttu-id="9a434-106">Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují <xref:System.ArgumentOutOfRangeException> speciální zpracování pro výjimku <xref:System.Drawing.Icon> , která je vyvolána, když objekt má snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="9a434-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="9a434-107">Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9a434-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="9a434-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="9a434-108">Mitigation</span></span>  
 <span data-ttu-id="9a434-109">Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do [ \<oddílu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="9a434-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="9a434-110">Pokud soubor App. config již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena `value` s atributem takto:</span><span class="sxs-lookup"><span data-stu-id="9a434-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a434-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a434-111">See also</span></span>

- [<span data-ttu-id="9a434-112">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="9a434-112">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
