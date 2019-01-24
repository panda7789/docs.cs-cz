---
title: 'Omezení rizik: PNG rámce v objektech ikonu'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d67b2fac0c1d55bfa5594e90998d9613de4ad271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659784"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="46c8d-102">Omezení rizik: PNG rámce v objektech ikonu</span><span class="sxs-lookup"><span data-stu-id="46c8d-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="46c8d-103">Od verze rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikony PNG snímky do <xref:System.Drawing.Bitmap> objekty.</span><span class="sxs-lookup"><span data-stu-id="46c8d-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="46c8d-104">V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.5.2 a starší verze <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda výjimku <xref:System.ArgumentOutOfRangeException> výjimka pokud <xref:System.Drawing.Icon> objekt má snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="46c8d-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="46c8d-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="46c8d-105">Impact</span></span>  
 <span data-ttu-id="46c8d-106">Tato změna ovlivní aplikace, které jsou rekompilovány cílit na rozhraní .NET Framework 4.6 a které implementují zvláštní zacházení <xref:System.ArgumentOutOfRangeException> , která je vyvolána, když <xref:System.Drawing.Icon> objekt má snímky PNG.</span><span class="sxs-lookup"><span data-stu-id="46c8d-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="46c8d-107">Při spuštění v rozhraní .NET Framework 4.6, převod je úspěšný, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto je již vyvolána obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="46c8d-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="46c8d-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="46c8d-108">Mitigation</span></span>  
 <span data-ttu-id="46c8d-109">Pokud toto chování nežádoucí, můžete zachovat předchozí chování tak, že přidáte následující element na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="46c8d-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="46c8d-110">Pokud již obsahuje soubor app.config `AppContextSwitchOverrides` elementu, nová hodnota mají sloučit s `value` atribut následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="46c8d-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="46c8d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46c8d-111">See also</span></span>
- [<span data-ttu-id="46c8d-112">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="46c8d-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
