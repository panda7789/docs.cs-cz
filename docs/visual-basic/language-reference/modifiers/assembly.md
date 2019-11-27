---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351638"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="fafda-102">Sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fafda-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="fafda-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="fafda-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fafda-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fafda-104">Remarks</span></span>  
 <span data-ttu-id="fafda-105">Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fafda-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="fafda-106">Tento atribut použijete připojením bloku atributu v rámci lomených závorek (`< >`) přímo k příkazu Declaration.</span><span class="sxs-lookup"><span data-stu-id="fafda-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="fafda-107">Pokud atribut nenáleží pouze k následujícímu prvku, ale k celému sestavení, umístěte blok atributů na začátek zdrojového souboru a Identifikujte atribut pomocí klíčového slova `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="fafda-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="fafda-108">Pokud se vztahuje na aktuální modul sestavení, použijte klíčové slovo [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="fafda-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="fafda-109">Můžete také použít atribut pro sestavení v souboru AssemblyInfo. vb, v takovém případě není nutné použít blok atributu v hlavním souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="fafda-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafda-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fafda-110">See also</span></span>

- [<span data-ttu-id="fafda-111">Klíčové slovo \<modulu ></span><span class="sxs-lookup"><span data-stu-id="fafda-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="fafda-112">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="fafda-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
