---
title: 'Zmírnění: Png snímky v objektech ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: d661e45bfbbe5e1c5ca5b7eb123e71aa32a096ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181223"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="c3bc3-102">Zmírnění: Png snímky v objektech ikon</span><span class="sxs-lookup"><span data-stu-id="c3bc3-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="c3bc3-103">Počínaje rozhraním .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede <xref:System.Drawing.Bitmap> ikony s rámečky PNG na objekty.</span><span class="sxs-lookup"><span data-stu-id="c3bc3-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="c3bc3-104">V aplikacích, které cílí na rozhraní .NET Framework <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 4.5.2 a starší verze, metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> pokud <xref:System.Drawing.Icon> objekt má png rámce.</span><span class="sxs-lookup"><span data-stu-id="c3bc3-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c3bc3-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="c3bc3-105">Impact</span></span>  
 <span data-ttu-id="c3bc3-106">Tato změna má vliv na aplikace, které jsou překompilovány na cíl <xref:System.ArgumentOutOfRangeException> .NET Framework <xref:System.Drawing.Icon> 4.6 a které implementují speciální zpracování pro to, který je vyvolán, když má objekt png rámce.</span><span class="sxs-lookup"><span data-stu-id="c3bc3-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="c3bc3-107">Při spuštění v rámci rozhraní .NET Framework 4.6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolána a proto obslužná rutina výjimky již není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c3bc3-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="c3bc3-108">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="c3bc3-108">Mitigation</span></span>  
 <span data-ttu-id="c3bc3-109">Pokud je toto chování nežádoucí, můžete zachovat předchozí chování přidáním následujícího prvku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="c3bc3-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="c3bc3-110">Pokud soubor app.config již `AppContextSwitchOverrides` prvek obsahuje, měla by `value` být nová hodnota sloučena s atributem takto:</span><span class="sxs-lookup"><span data-stu-id="c3bc3-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3bc3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3bc3-111">See also</span></span>

- [<span data-ttu-id="c3bc3-112">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="c3bc3-112">Application compatibility</span></span>](application-compatibility.md)
