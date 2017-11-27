---
title: "Sestavení (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="7210a-102">Sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7210a-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="7210a-103">Určuje, že atribut na začátku zdrojového souboru platí pro celou sestavení.</span><span class="sxs-lookup"><span data-stu-id="7210a-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7210a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7210a-104">Remarks</span></span>  
 <span data-ttu-id="7210a-105">Počet atributů se týkají jednotlivých programovací element, jako je například třída nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7210a-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="7210a-106">Použít takového atributu připojením atribut bloku, v rámci lomené závorky (`< >`), přímo k příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="7210a-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="7210a-107">Pokud atribut se vztahují pouze na následující element, ale na celý sestavení, můžete umístit atribut bloku na začátku zdrojový soubor a identifikovat atribut s `Assembly` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7210a-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="7210a-108">Pokud se vztahuje na aktuální modul sestavení, můžete použít [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7210a-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="7210a-109">Atribut můžete také použít k sestavení v souboru AssemblyInfo.vb v takovém případě není muset použít blok atribut v souboru hlavní zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="7210a-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7210a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7210a-110">See Also</span></span>  
 [<span data-ttu-id="7210a-111">Modul \<– klíčové slovo ></span><span class="sxs-lookup"><span data-stu-id="7210a-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="7210a-112">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="7210a-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

