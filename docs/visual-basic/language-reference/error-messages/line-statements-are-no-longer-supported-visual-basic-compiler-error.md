---
title: Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339070"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="aa555-102">Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="aa555-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="aa555-103">Příkazy řádek již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="aa555-103">Line statements are no longer supported.</span></span> <span data-ttu-id="aa555-104">I/O soubor funkce je dostupná jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce jsou k dispozici jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="aa555-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="aa555-105">**ID chyby:** BC30830</span><span class="sxs-lookup"><span data-stu-id="aa555-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa555-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aa555-106">To correct this error</span></span>  
  
1. <span data-ttu-id="aa555-107">Pokud provádíte přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="aa555-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="aa555-108">Pokud provádíte grafiky, použijte `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="aa555-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa555-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa555-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="aa555-110">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa555-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
