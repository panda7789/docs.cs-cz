---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 5530da4c784346df4a1088998b8d2027feee08e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403158"
---
# <a name="-main"></a>-main
Určuje třídu nebo modul, který obsahuje `Sub Main` proceduru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Argumenty  
 `location`  
 Povinná hodnota. Název třídy nebo modulu, který obsahuje `Sub Main` proceduru, která má být volána při spuštění programu. Může to být v podobě **: hlavní: modul** nebo **-hlavní: obor názvů. Module**.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte při vytváření spustitelného souboru nebo spustitelného programu systému Windows. Pokud je možnost **-Main** vynechána, kompilátor vyhledá platnou sdílenou `Sub Main` ve všech veřejných třídách a modulech.  
  
 Diskuzi o různých formulářích postupu najdete [v tématu hlavní postup v Visual Basic](../../programming-guide/program-structure/main-procedure.md) `Main` .  
  
 Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form> , kompilátor poskytuje výchozí `Main` proceduru, která spustí aplikaci, pokud třída nemá žádnou `Main` proceduru. To umožňuje kompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Nastavení – hlavní v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **aplikace** .  
  
3. Ujistěte se, že není zaškrtnuté políčko **Povolit aplikační rozhraní** .  
  
4. Upravte hodnotu v poli **spouštěcí objekt** .  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a `T3.vb` určí, že `Sub Main` procedura bude nalezena ve `Test2` třídě.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Hlavní procedura v jazyce Visual Basic](../../programming-guide/program-structure/main-procedure.md)
