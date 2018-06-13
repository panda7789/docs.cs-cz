---
title: '&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587876"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="878d1-102">&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="878d1-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="878d1-103">Příkazy řádku již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="878d1-103">Line statements are no longer supported.</span></span> <span data-ttu-id="878d1-104">Vstupně-výstupní funkce je k dispozici jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce je k dispozici jako `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="878d1-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="878d1-105">**ID chyby:** BC30830</span><span class="sxs-lookup"><span data-stu-id="878d1-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="878d1-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="878d1-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="878d1-107">Pokud se provádí přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="878d1-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="878d1-108">Pokud budete provádět grafiky, použijte `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="878d1-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878d1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="878d1-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="878d1-110">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="878d1-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
