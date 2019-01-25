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
ms.openlocfilehash: e6cb7e7a2520d6bb586dab4ed0af75abb04fabd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726465"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="fe0fa-102">Sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe0fa-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="fe0fa-103">Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe0fa-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe0fa-104">Remarks</span></span>  
 <span data-ttu-id="fe0fa-105">Mnoho atributů se vztahují na jednotlivý programový element, jako je třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="fe0fa-106">Použijte takový atribut připojením atribut bloku, v lomených závorkách (`< >`), přímo do příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="fe0fa-107">Pokud atribut se vztahuje pouze na tento element, ale na celé sestavení, umístěte blok atribut na začátku zdrojového souboru a identifikovat atribut s `Assembly` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="fe0fa-108">Pokud se vztahuje na aktuální modul sestavení, můžete použít [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="fe0fa-109">Můžete také použít atribut na sestavení v souboru AssemblyInfo.vb v takovém případě není potřeba použít blok atributu v souboru hlavní zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0fa-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe0fa-110">See also</span></span>
- [<span data-ttu-id="fe0fa-111">Module \<keyword></span><span class="sxs-lookup"><span data-stu-id="fe0fa-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="fe0fa-112">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="fe0fa-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

