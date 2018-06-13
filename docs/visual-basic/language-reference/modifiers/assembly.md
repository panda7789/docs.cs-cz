---
title: Sestavení (Visual Basic)
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
ms.openlocfilehash: 7ee6cddefd5955ee76510ffeb23335f05460657b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595287"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="db1e1-102">Sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db1e1-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="db1e1-103">Určuje, že atribut na začátku zdrojového souboru platí pro celou sestavení.</span><span class="sxs-lookup"><span data-stu-id="db1e1-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db1e1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db1e1-104">Remarks</span></span>  
 <span data-ttu-id="db1e1-105">Počet atributů se týkají jednotlivých programovací element, jako je například třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db1e1-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="db1e1-106">Použít takového atributu připojením atribut bloku, v rámci lomené závorky (`< >`), přímo k příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="db1e1-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="db1e1-107">Pokud atribut se vztahují pouze na následující element, ale na celý sestavení, můžete umístit atribut bloku na začátku zdrojový soubor a identifikovat atribut s `Assembly` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db1e1-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="db1e1-108">Pokud se vztahuje na aktuální modul sestavení, můžete použít [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db1e1-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="db1e1-109">Atribut můžete také použít k sestavení v souboru AssemblyInfo.vb v takovém případě není muset použít blok atribut v souboru hlavní zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="db1e1-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1e1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="db1e1-110">See Also</span></span>  
 [<span data-ttu-id="db1e1-111">Modul \<– klíčové slovo ></span><span class="sxs-lookup"><span data-stu-id="db1e1-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="db1e1-112">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="db1e1-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

