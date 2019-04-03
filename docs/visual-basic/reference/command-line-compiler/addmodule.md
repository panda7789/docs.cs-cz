---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2de5fe82f1969a2fdb305d45951d7d698252c0c8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816431"
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
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Následující kód naimportuje typy modulu.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Při spuštění `t1`, výstupu `802`.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
