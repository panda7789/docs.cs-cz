---
title: Čipu<keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 0cb009c22dada7b92956e113d33505923a92f2b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362421"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="57d78-102">\<keyword> – modul (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57d78-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="57d78-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na aktuální modul sestavení.</span><span class="sxs-lookup"><span data-stu-id="57d78-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57d78-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57d78-104">Remarks</span></span>  
 <span data-ttu-id="57d78-105">Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="57d78-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="57d78-106">Tento atribut lze uplatnit připojením bloku atributu v rámci lomených závorek ( `< >` ) přímo k příkazu Declaration.</span><span class="sxs-lookup"><span data-stu-id="57d78-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="57d78-107">Pokud atribut nenáleží pouze k následujícímu elementu, ale k aktuálnímu modulu sestavení, umístěte blok atributu na začátek zdrojového souboru a Identifikujte atribut pomocí `Module` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="57d78-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="57d78-108">Pokud platí pro celé sestavení, použijte klíčové slovo [Assembly](assembly.md) .</span><span class="sxs-lookup"><span data-stu-id="57d78-108">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="57d78-109">`Module`Modifikátor není stejný jako [příkaz Module](../statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57d78-109">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d78-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="57d78-110">See also</span></span>

- [<span data-ttu-id="57d78-111">Sestavení</span><span class="sxs-lookup"><span data-stu-id="57d78-111">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="57d78-112">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="57d78-112">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="57d78-113">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="57d78-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
