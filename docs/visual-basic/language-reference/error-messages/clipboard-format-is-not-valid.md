---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586218"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="10a8a-102">Formát schránky není platný.</span><span class="sxs-lookup"><span data-stu-id="10a8a-102">Clipboard format is not valid</span></span>
<span data-ttu-id="10a8a-103">Zadaný formát schránky není kompatibilní s metodu spouštěna.</span><span class="sxs-lookup"><span data-stu-id="10a8a-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="10a8a-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="10a8a-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="10a8a-105">Pomocí do schránky `GetText` nebo `SetText` metoda s formát schránky jinak než `vbCFText` nebo `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="10a8a-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="10a8a-106">Pomocí do schránky `GetData` nebo `SetData` metoda s formát schránky jinak než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="10a8a-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="10a8a-107">Pomocí `DataObject``GetData` metoda nebo `SetData` metoda s formát schránky v rozsahu vyhrazený systémem Microsoft Windows pro registrované formátů (& HC000 & HFFFF), když tento formát schránky nebyl zaregistrován v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="10a8a-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10a8a-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="10a8a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="10a8a-109">Odeberte neplatný formát a zadejte platný.</span><span class="sxs-lookup"><span data-stu-id="10a8a-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a8a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="10a8a-110">See Also</span></span>  
 [<span data-ttu-id="10a8a-111">Schránka: Přidání dalších formátů</span><span class="sxs-lookup"><span data-stu-id="10a8a-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
