---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 9e8146497d63d949f138d6cd08c9ea8c7b03c651
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414308"
---
# <a name="-addmodule"></a>-addmodule
Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Povinná hodnota. Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení. Názvy souborů, které obsahují mezery, by měly být obklopené uvozovkami ("").  
  
## <a name="remarks"></a>Poznámky  
 Soubory uvedené `fileList` parametrem musí být vytvořeny s `-target:module` možností nebo s jiným kompilátorem ekvivalentním `-target:module` .  
  
 Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu. To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu. Pokud to tak není, zobrazí se <xref:System.TypeLoadException> Chyba.  
  
 Pokud zadáte (implicitně nebo explicitně) možnost libovolný[cíl (Visual Basic)](target.md) jiné než `-target:module` s `-addmodule` , soubory, které předáte, se `-addmodule` stanou součástí sestavení projektu. Pro spuštění výstupního souboru, který obsahuje jeden nebo více souborů přidaných pomocí, je vyžadováno sestavení `-addmodule` .  
  
 Pomocí [-Reference (Visual Basic)](reference.md) můžete importovat metadata ze souboru, který obsahuje sestavení.  
  
> [!NOTE]
> Tato `-addmodule` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří modul.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Následující kód importuje typy modulu.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Když spustíte `t1` , výstup IT `802` .  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [-Reference (Visual Basic)](reference.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
