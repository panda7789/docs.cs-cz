---
title: <keyword> modulu
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: cd2f762181b5a702f0b0defd5b71bb7bdf129c7b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351556"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="750b0-102">Modul \<> klíčového slova (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="750b0-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="750b0-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na aktuální modul sestavení.</span><span class="sxs-lookup"><span data-stu-id="750b0-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="750b0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="750b0-104">Remarks</span></span>  
 <span data-ttu-id="750b0-105">Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="750b0-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="750b0-106">Tento atribut použijete připojením bloku atributu v rámci lomených závorek (`< >`) přímo k příkazu Declaration.</span><span class="sxs-lookup"><span data-stu-id="750b0-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="750b0-107">Pokud atribut nenáleží pouze k následujícímu elementu, ale k aktuálnímu modulu sestavení, umístěte blok atributů na začátek zdrojového souboru a Identifikujte atribut pomocí klíčového slova `Module`.</span><span class="sxs-lookup"><span data-stu-id="750b0-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="750b0-108">Pokud platí pro celé sestavení, použijte klíčové slovo [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) .</span><span class="sxs-lookup"><span data-stu-id="750b0-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="750b0-109">Modifikátor `Module` není stejný jako [příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="750b0-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750b0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="750b0-110">See also</span></span>

- [<span data-ttu-id="750b0-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="750b0-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="750b0-112">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="750b0-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="750b0-113">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="750b0-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
