---
title: Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 7616bcdc39ab479049586534fac22f1e2d96a700
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831836"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="301ea-102">Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="301ea-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="301ea-103">Příkazy řádek již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="301ea-103">Line statements are no longer supported.</span></span> <span data-ttu-id="301ea-104">I/O soubor funkce je dostupná jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce jsou k dispozici jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="301ea-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="301ea-105">**ID chyby:** BC30830</span><span class="sxs-lookup"><span data-stu-id="301ea-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="301ea-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="301ea-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="301ea-107">Pokud provádíte přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="301ea-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="301ea-108">Pokud provádíte grafiky, použijte `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="301ea-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301ea-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="301ea-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="301ea-110">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="301ea-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
