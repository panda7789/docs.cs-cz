---
title: Vstup za koncem souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768550"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="d24de-102">Vstup za koncem souboru</span><span class="sxs-lookup"><span data-stu-id="d24de-102">Input past end of file</span></span>
<span data-ttu-id="d24de-103">Buď `Input` příkazu je čtení ze souboru, který je prázdný nebo ve kterém se používá všechna data nebo jste použili `EOF` funkce se souborem otevření pro binární přístup.</span><span class="sxs-lookup"><span data-stu-id="d24de-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d24de-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d24de-104">To correct this error</span></span>  
  
1. <span data-ttu-id="d24de-105">Použití `EOF` funkce bezprostředně před `Input` příkaz k zjištění konce souboru.</span><span class="sxs-lookup"><span data-stu-id="d24de-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="d24de-106">Pokud je soubor otevřen pro binární přístup, použijte `Seek` a `Loc`.</span><span class="sxs-lookup"><span data-stu-id="d24de-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24de-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d24de-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
