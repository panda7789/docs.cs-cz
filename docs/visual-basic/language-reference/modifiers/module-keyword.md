---
title: <keyword> – modul (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: f6ded1184aedf1702f4b6e5eebb85709cf8e39f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814273"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="0850a-102">Module \<keyword> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0850a-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="0850a-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na aktuální modul sestavení.</span><span class="sxs-lookup"><span data-stu-id="0850a-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0850a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0850a-104">Remarks</span></span>  
 <span data-ttu-id="0850a-105">Mnoho atributů se vztahují na jednotlivý programový element, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0850a-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="0850a-106">Použijte takový atribut připojením atribut bloku, v lomených závorkách (`< >`), přímo do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="0850a-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="0850a-107">Pokud atribut náleží nejen tento element, ale aktuální modul sestavení, umístěte blok atribut na začátku zdrojového souboru a identifikovat atribut s `Module` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0850a-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="0850a-108">Pokud se vztahuje na celé sestavení, můžete použít [sestavení](../../../visual-basic/language-reference/modifiers/assembly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0850a-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="0850a-109">`Module` Modifikátor není stejný jako [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0850a-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0850a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0850a-110">See also</span></span>

- [<span data-ttu-id="0850a-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="0850a-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="0850a-112">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="0850a-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="0850a-113">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="0850a-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
