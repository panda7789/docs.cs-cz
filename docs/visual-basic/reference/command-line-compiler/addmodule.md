---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a>/addmodule
Způsobí, že kompilátor zkontrolujte všechny informace ze zadané soubory, které jsou k dispozici do projektu, které jsou aktuálně kompilování typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Požadováno. Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení. Názvy souborů obsahujících mezery musí být uzavřena v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Soubory uvedené podle `fileList` parametr musí být vytvořeny s `/target:module` možnost, nebo s jinou kompilátoru ekvivalent `/target:module`.  
  
 Všechny moduly přidané pomocí `/addmodule` musí být ve stejném adresáři jako výstupní soubor za běhu. To znamená můžete zadat modul v libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace za běhu. Pokud není, můžete získat <xref:System.TypeLoadException> chyby.  
  
 Pokud zadáte (implicitně nebo explicitně) žádné[/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) možnost jiné než `/target:module` s `/addmodule`, soubory, které předat `/addmodule` se stanou součástí sestavení projektu. Sestavení se vyžaduje ke spuštění výstupního souboru, který má jeden nebo víc souborů se přidaly `/addmodule`.  
  
 Použití [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Import metadat ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
>  `/addmodule` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Následující kód importuje modulu typy.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Při spuštění `t1`, vyprodukuje `802`.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
