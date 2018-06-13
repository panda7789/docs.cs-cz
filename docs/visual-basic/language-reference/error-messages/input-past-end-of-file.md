---
title: Vstup za koncem souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586738"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="9277d-102">Vstup za koncem souboru</span><span class="sxs-lookup"><span data-stu-id="9277d-102">Input past end of file</span></span>
<span data-ttu-id="9277d-103">Buď `Input` příkaz je čtení ze souboru, který je prázdný nebo ve které se používá všechna data, nebo jste použili `EOF` funkce souborem otevřen pro binární.</span><span class="sxs-lookup"><span data-stu-id="9277d-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9277d-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9277d-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="9277d-105">Použití `EOF` funkce bezprostředně před `Input` příkaz pro zjištění konec souboru.</span><span class="sxs-lookup"><span data-stu-id="9277d-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="9277d-106">Pokud soubor je otevřen pro binární, použijte `Seek` a `Loc`.</span><span class="sxs-lookup"><span data-stu-id="9277d-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9277d-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="9277d-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
