---
title: -addmodule
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c17d5541fe2d02ba88f4c5ef259b2248f371dfe5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
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
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
