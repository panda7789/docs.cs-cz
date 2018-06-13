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
# <a name="assembly-visual-basic"></a>Sestavení (Visual Basic)
Určuje, že atribut na začátku zdrojového souboru platí pro celou sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Počet atributů se týkají jednotlivých programovací element, jako je například třída nebo vlastnost. Použít takového atributu připojením atribut bloku, v rámci lomené závorky (`< >`), přímo k příkazu deklarace.  
  
 Pokud atribut se vztahují pouze na následující element, ale na celý sestavení, můžete umístit atribut bloku na začátku zdrojový soubor a identifikovat atribut s `Assembly` – klíčové slovo. Pokud se vztahuje na aktuální modul sestavení, můžete použít [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md) – klíčové slovo.  
  
 Atribut můžete také použít k sestavení v souboru AssemblyInfo.vb v takovém případě není muset použít blok atribut v souboru hlavní zdrojového kódu.  
  
## <a name="see-also"></a>Viz také  
 [Modul \<– klíčové slovo >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

