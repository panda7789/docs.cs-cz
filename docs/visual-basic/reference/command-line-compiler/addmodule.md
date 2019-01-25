---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580574"
---
# <a name="-addmodule"></a>-addmodule
Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Povinný parametr. Čárkami oddělený seznam souborů, které obsahují metadata, ale nebude obsahovat manifest sestavení. Názvy souborů obsahujících mezery by měla být uzavřena v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Souborů uvedené podle `fileList` parametr musí být vytvořená s `-target:module` možnost, nebo jiného kompilátoru ekvivalentem `-target:module`.  
  
 Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená můžete zadat modulu do libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud není, můžete získat <xref:System.TypeLoadException> chyby.  
  
 Pokud zadáte (implicitně nebo explicitně) všechny[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) možností jiných než `-target:module` s `-addmodule`, soubory předáte `-addmodule` se stanou součástí sestavení projektu. Sestavení se vyžaduje pro spuštění výstupního souboru, který obsahuje jednu nebo více souborů se přidá s `-addmodule`.  
  
 Použití [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Import metadat ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
>  `-addmodule` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Následující kód naimportuje typy modulu.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Při spuštění `t1`, výstupu `802`.  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
