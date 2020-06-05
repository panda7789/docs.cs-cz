---
title: Sestavení
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
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373157"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="5b20e-102">Sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b20e-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="5b20e-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b20e-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b20e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b20e-104">Remarks</span></span>  
 <span data-ttu-id="5b20e-105">Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b20e-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="5b20e-106">Tento atribut lze uplatnit připojením bloku atributu v rámci lomených závorek ( `< >` ) přímo k příkazu Declaration.</span><span class="sxs-lookup"><span data-stu-id="5b20e-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="5b20e-107">Pokud atribut nenáleží pouze k následujícímu prvku, ale k celému sestavení, umístěte blok atributů na začátek zdrojového souboru a Identifikujte atribut pomocí `Assembly` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="5b20e-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="5b20e-108">Pokud se vztahuje na aktuální modul sestavení, použijte klíčové slovo [Module](module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="5b20e-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="5b20e-109">Můžete také použít atribut pro sestavení v souboru AssemblyInfo. vb, v takovém případě není nutné použít blok atributu v hlavním souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5b20e-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b20e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b20e-110">See also</span></span>

- [<span data-ttu-id="5b20e-111">Čipu\<keyword></span><span class="sxs-lookup"><span data-stu-id="5b20e-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="5b20e-112">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="5b20e-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
