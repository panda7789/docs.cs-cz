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
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801983"
---
# <a name="assembly-visual-basic"></a>Sestavení (Visual Basic)
Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Mnoho atributů se vztahují na jednotlivý programový element, jako je třída nebo vlastnost. Použijte takový atribut připojením atribut bloku, v lomených závorkách (`< >`), přímo do příkazu deklarace.  
  
 Pokud atribut se vztahuje pouze na tento element, ale na celé sestavení, umístěte blok atribut na začátku zdrojového souboru a identifikovat atribut s `Assembly` – klíčové slovo. Pokud se vztahuje na aktuální modul sestavení, můžete použít [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md) – klíčové slovo.  
  
 Můžete také použít atribut na sestavení v souboru AssemblyInfo.vb v takovém případě není potřeba použít blok atributu v souboru hlavní zdrojového kódu.  
  
## <a name="see-also"></a>Viz také:

- [Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
