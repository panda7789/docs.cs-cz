---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2fefdf81ab25d2e109f265f0c895a3415ad5673d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-addmodule"></a>-addmodule
Způsobí, že kompilátor zkontrolujte všechny informace ze zadané soubory, které jsou k dispozici do projektu, které jsou aktuálně kompilování typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Požadováno. Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení. Názvy souborů obsahujících mezery musí být uzavřena v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Soubory uvedené podle `fileList` parametr musí být vytvořeny s `-target:module` možnost, nebo s jinou kompilátoru ekvivalent `-target:module`.  
  
 Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor za běhu. To znamená můžete zadat modul v libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace za běhu. Pokud není, můžete získat <xref:System.TypeLoadException> chyby.  
  
 Pokud zadáte (implicitně nebo explicitně) žádné[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) možnost jiné než `-target:module` s `-addmodule`, soubory, které předat `-addmodule` se stanou součástí sestavení projektu. Sestavení se vyžaduje ke spuštění výstupního souboru, který má jeden nebo víc souborů se přidaly `-addmodule`.  
  
 Použití [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Import metadat ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
>  `-addmodule` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Následující kód importuje modulu typy.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Při spuštění `t1`, vyprodukuje `802`.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
