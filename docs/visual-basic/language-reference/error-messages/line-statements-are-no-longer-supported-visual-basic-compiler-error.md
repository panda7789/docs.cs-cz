---
title: Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 17025e9a3c87d84a10ddaa7aeef616d985143879
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283206"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="2d126-102">Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2d126-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="2d126-103">Příkazy řádek již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2d126-103">Line statements are no longer supported.</span></span> <span data-ttu-id="2d126-104">I/O soubor funkce je dostupná jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce jsou k dispozici jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="2d126-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="2d126-105">**ID chyby:** BC30830</span><span class="sxs-lookup"><span data-stu-id="2d126-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d126-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2d126-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2d126-107">Pokud provádíte přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="2d126-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="2d126-108">Pokud provádíte grafiky, použijte `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="2d126-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d126-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d126-109">See also</span></span>
- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="2d126-110">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d126-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
