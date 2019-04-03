---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817172"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="e4cfe-102">Formát schránky není platný.</span><span class="sxs-lookup"><span data-stu-id="e4cfe-102">Clipboard format is not valid</span></span>
<span data-ttu-id="e4cfe-103">Zadaný formát schránky není kompatibilní s metoda se spouští.</span><span class="sxs-lookup"><span data-stu-id="e4cfe-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="e4cfe-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="e4cfe-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="e4cfe-105">Pomocí do schránky `GetText` nebo `SetText` metodu s formát schránky jiných než `vbCFText` nebo `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="e4cfe-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="e4cfe-106">Pomocí do schránky `GetData` nebo `SetData` metodu s formát schránky jiných než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="e4cfe-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="e4cfe-107">Pomocí `GetData` nebo `SetData` metody `DataObject` formátu schránky v oblasti vyhrazené Microsoft Windows registrované formáty (& HC000 - & HFFFF), když tento formát schránky není zaregistrován s Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="e4cfe-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e4cfe-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e4cfe-108">To correct this error</span></span>  
  
-   <span data-ttu-id="e4cfe-109">Odeberte neplatný formát a zadejte platný.</span><span class="sxs-lookup"><span data-stu-id="e4cfe-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cfe-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4cfe-110">See also</span></span>

- [<span data-ttu-id="e4cfe-111">Schránka: Přidání dalších formátů</span><span class="sxs-lookup"><span data-stu-id="e4cfe-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
