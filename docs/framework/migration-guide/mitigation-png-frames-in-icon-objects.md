---
title: "Omezení rizik: PNG rámce v ikona objektů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc81484f55cabbdc86e7ba57e68f9e1c96a567f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="a8c6c-102">Omezení rizik: PNG rámce v ikona objektů</span><span class="sxs-lookup"><span data-stu-id="a8c6c-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="a8c6c-103">Od verze rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda převede úspěšně ikony s PNG rámce do <xref:System.Drawing.Bitmap> objekty.</span><span class="sxs-lookup"><span data-stu-id="a8c6c-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="a8c6c-104">V aplikacích, které cílí na rozhraní .NET Framework 4.5.2 a dřívějších verzích <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vrátí <xref:System.ArgumentOutOfRangeException> výjimka pokud <xref:System.Drawing.Icon> objekt má rámce PNG.</span><span class="sxs-lookup"><span data-stu-id="a8c6c-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a8c6c-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="a8c6c-105">Impact</span></span>  
 <span data-ttu-id="a8c6c-106">Tato změna ovlivňuje aplikace, která jsou překompilovat, jehož cílem je rozhraní .NET Framework 4.6 a které implementují zvláštní zpracování pro <xref:System.ArgumentOutOfRangeException> , když dojde <xref:System.Drawing.Icon> objekt má rámce PNG.</span><span class="sxs-lookup"><span data-stu-id="a8c6c-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="a8c6c-107">Při spuštění v rozhraní .NET Framework 4.6, převod proběhne úspěšně, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto už volána obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="a8c6c-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="a8c6c-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="a8c6c-108">Mitigation</span></span>  
 <span data-ttu-id="a8c6c-109">Pokud je toto chování žádoucí, můžete zachovat předchozí chování přidáním následující elementu, který chcete [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="a8c6c-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="a8c6c-110">Pokud již obsahuje soubor app.config `AppContextSwitchOverrides` elementu, nová hodnota má být sloučena s `value` atribut takto:</span><span class="sxs-lookup"><span data-stu-id="a8c6c-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8c6c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8c6c-111">See Also</span></span>  
 [<span data-ttu-id="a8c6c-112">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="a8c6c-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
