---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 0e0915a2534f950cec074632a59750c3f96b679d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962450"
---
# <a name="-addmodule"></a>-addmodule
Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Povinný parametr. Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení. Názvy souborů, které obsahují mezery, by měly být obklopené uvozovkami ("").  
  
## <a name="remarks"></a>Poznámky  
 Soubory uvedené `fileList` parametrem musí být vytvořeny `-target:module` s možností nebo s `-target:module`jiným kompilátorem ekvivalentním.  
  
 Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud to tak není, zobrazí <xref:System.TypeLoadException> se chyba.  
  
 Pokud zadáte (implicitně nebo explicitně) možnost libovolný[cíl (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) jiné než `-target:module` s `-addmodule`, soubory, které předáte `-addmodule` , se stanou součástí sestavení projektu. Pro spuštění výstupního souboru, který obsahuje jeden nebo více souborů přidaných pomocí `-addmodule`, je vyžadováno sestavení.  
  
 Použijte [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pro import metadat ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
> Tato `-addmodule` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Následující kód importuje typy modulu.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Když spustíte `t1`, výstup `802`IT.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
