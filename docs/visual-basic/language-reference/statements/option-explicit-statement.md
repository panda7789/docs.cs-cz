---
title: Option Explicit – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912338"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit – příkaz (Visual Basic)
Vynutí explicitní deklaraci všech proměnných v souboru nebo umožňuje implicitní deklarace proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
 `On`  
 Volitelný parametr. Povoluje `Option Explicit` kontrolu. Pokud parametr není zadán, je `On`použita výchozí hodnota. `On` `Off`  
  
 `Off`  
 Volitelný parametr. Zakáže `Option Explicit` kontrolu.  
  
## <a name="remarks"></a>Poznámky  
 Když `Option Explicit On` `Dim` `ReDim` nebo `Option Explicit` se zobrazí v souboru, musíte explicitně deklarovat všechny proměnné pomocí příkazů nebo. Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě v době kompilace. `Option Explicit Off` Příkaz umožňuje implicitní deklaraci proměnných.  
  
 Je-li použit `Option Explicit` , příkaz se musí objevit v souboru před jakýmkoli jiným příkazy zdrojového kódu.  
  
> [!NOTE]
> Nastavení `Option Explicit` na`Off` není obvykle dobrým zvykem. V jednom nebo více umístěních byste mohli nastavovat navýšení názvu proměnné, což způsobí, že při spuštění programu dojde k neočekávaným výsledkům.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Pokud není k dispozici příkaz Option Explicit  
 Pokud zdrojový kód `Option Explicit` neobsahuje příkaz, je použita **možnost explicitní** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Pokud je použit kompilátor příkazového řádku, je použita možnost kompilátoru [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) .  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Nastavení možnosti Explicit v integrovaném vývojovém prostředí  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **kompilovat** .  
  
3. Nastavte hodnotu v poli **explicitní možnosti** .  
  
 Při vytváření nového projektu je **možnost explicitní** nastavení na kartě **kompilovat** nastavena na **možnost explicitní** nastavení v dialogovém okně **výchozí hodnoty VB** . Chcete-li získat přístup k dialogovému oknu **výchozí hodnoty VB** , v nabídce **nástroje** klikněte na možnost **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Výchozí výchozí nastavení ve výchozím nastavení **jazyka VB** je `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Nastavení možnosti Explicit na příkazovém řádku  
  
- Do příkazu **Vbc** zahrňte možnost kompilátoru [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Explicit` příkaz k vynucení explicitní deklarace všech proměnných. Pokus o použití nedeklarované proměnné způsobí chybu v době kompilace.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
