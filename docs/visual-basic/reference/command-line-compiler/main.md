---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005505"
---
# <a name="-main"></a>-main
Určuje třídu nebo modul, který obsahuje postup `Sub Main`.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Požadováno. Název třídy nebo modulu, který obsahuje postup `Sub Main`, který se má volat při spuštění programu. Může to být v podobě **: hlavní: modul** nebo **-hlavní: obor názvů. Module**.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte při vytváření spustitelného souboru nebo spustitelného programu systému Windows. Pokud je možnost **-Main** vynechána, kompilátor vyhledá platný sdílený `Sub Main` ve všech veřejných třídách a modulech.  
  
 Diskuzi o různých formách postupu `Main` najdete [v části hlavní postup v Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) .  
  
 Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí proceduru `Main`, která spustí aplikaci, pokud třída nemá proceduru `Main`. To umožňuje kompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Nastavení – hlavní v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **aplikace** .  
  
3. Ujistěte se, že není zaškrtnuté políčko **Povolit aplikační rozhraní** .  
  
4. Upravte hodnotu v poli **spouštěcí objekt** .  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a `T3.vb` a určí, že se procedura `Sub Main` bude nacházet ve třídě `Test2`.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Hlavní postup v Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
