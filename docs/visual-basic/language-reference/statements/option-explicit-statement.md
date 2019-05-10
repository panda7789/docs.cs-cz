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
ms.openlocfilehash: 8374cdf6526061dfd463574887c2e98d25010910
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582769"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit – příkaz (Visual Basic)
Vynutí explicitní deklaraci všech proměnných do souboru nebo umožňuje implicitní deklarací proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
 `On`  
 Volitelné. Umožňuje `Option Explicit` kontrolu. Pokud `On` nebo `Off` není zadán, výchozí hodnota je `On`.  
  
 `Off`  
 Volitelné. Zakáže `Option Explicit` kontrolu.  
  
## <a name="remarks"></a>Poznámky  
 Když `Option Explicit On` nebo `Option Explicit` se zobrazí v souboru, musíte explicitně deklarovat všechny proměnné pomocí `Dim` nebo `ReDim` příkazy. Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě v době kompilace. `Option Explicit Off` Příkaz umožňuje implicitní deklaraci proměnných.  
  
 Pokud použijete, `Option Explicit` příkazu musí být uvedena v soubor předtím, než všechny ostatní příkazy zdrojového kódu.  
  
> [!NOTE]
>  Nastavení `Option Explicit` k `Off` není obvykle vhodné. Název proměnné v jedné nebo více umístění, což způsobilo neočekávané výsledky při spuštění programu může mít překlep.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Pokud není k dispozici Option Explicit – příkaz  
 Pokud zdrojový kód neobsahuje `Option Explicit` příkazu **Option Explicit** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud se používá kompilátor příkazového řádku, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru je používá.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Nastavení Option Explicit v integrovaném vývojovém prostředí  
  
1. V **Průzkumníka řešení**, vyberte projekt. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2. Klikněte na tlačítko **kompilaci** kartu.  
  
3. Nastavte hodnotu **Option Explicit** pole.  
  
 Když vytvoříte nový projekt **Option Explicit** nastavení na **kompilaci** karty nastavená na **Option Explicit** nastavení **VB výchozí**dialogové okno. Pro přístup **VB výchozí** dialogovém okně **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Chcete-li nastavit na příkazovém řádku Option Explicit  
  
- Zahrnout [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru v **Vbc –** příkazu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Option Explicit` příkaz vynutit explicitní deklaraci všech proměnných. Pokus o použití Nedeklarovaná proměnná způsobí chybu v době kompilace.  
  
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
