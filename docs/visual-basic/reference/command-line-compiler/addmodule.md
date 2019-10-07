---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002414"
---
# <a name="-addmodule"></a>-addmodule
Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Požadováno. Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení. Názvy souborů, které obsahují mezery, by měly být obklopené uvozovkami ("").  
  
## <a name="remarks"></a>Poznámky  
 Soubory uvedené parametrem `fileList` musí být vytvořeny s možností `-target:module` nebo s jiným kompilátorem ekvivalentním `-target:module`.  
  
 Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud to tak není, zobrazí se chyba <xref:System.TypeLoadException>.  
  
 Pokud zadáte (implicitně nebo explicitně) možnost libovolný[cíl (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) kromě `-target:module` s `-addmodule`, soubory, které předáte do `-addmodule`, se stanou součástí sestavení projektu. Pro spuštění výstupního souboru, který obsahuje jeden nebo více souborů přidaných s `-addmodule`, je vyžadováno sestavení.  
  
 Použijte [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pro import metadat ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
> Možnost `-addmodule` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Následující kód importuje typy modulu.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Když spustíte `t1`, výstup IT `802`.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
