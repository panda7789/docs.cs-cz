---
title: "Formát schránky není platný."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="51bf0-102">Formát schránky není platný.</span><span class="sxs-lookup"><span data-stu-id="51bf0-102">Clipboard format is not valid</span></span>
<span data-ttu-id="51bf0-103">Zadaný formát schránky není kompatibilní s metodu spouštěna.</span><span class="sxs-lookup"><span data-stu-id="51bf0-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="51bf0-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="51bf0-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="51bf0-105">Pomocí do schránky `GetText` nebo `SetText` metoda s formát schránky jinak než `vbCFText` nebo `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="51bf0-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="51bf0-106">Pomocí do schránky `GetData` nebo `SetData` metoda s formát schránky jinak než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="51bf0-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="51bf0-107">Pomocí `DataObject``GetData` metoda nebo `SetData` metoda s formát schránky v rozsahu vyhrazený systémem Microsoft Windows pro registrované formátů (& HC000 & HFFFF), když tento formát schránky nebyl zaregistrován v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="51bf0-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51bf0-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="51bf0-108">To correct this error</span></span>  
  
-   <span data-ttu-id="51bf0-109">Odeberte neplatný formát a zadejte platný.</span><span class="sxs-lookup"><span data-stu-id="51bf0-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51bf0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="51bf0-110">See Also</span></span>  
 [<span data-ttu-id="51bf0-111">Schránka: Přidání dalších formátů</span><span class="sxs-lookup"><span data-stu-id="51bf0-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
