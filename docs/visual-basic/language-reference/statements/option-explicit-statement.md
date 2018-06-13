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
ms.openlocfilehash: 3a2d81b1441052c132e4739dfe6045f8c3a026d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604598"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit – příkaz (Visual Basic)
Vynutí explicitní deklaraci všech proměnných v souboru nebo umožňuje implicitní deklarace proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
 `On`  
 Volitelné. Umožňuje `Option Explicit` kontrola. Pokud `On` nebo `Off` není určena, výchozí hodnota je `On`.  
  
 `Off`  
 Volitelné. Zakáže `Option Explicit` kontrola.  
  
## <a name="remarks"></a>Poznámky  
 Když `Option Explicit On` nebo `Option Explicit` se zobrazí v souboru, je potřeba explicitně deklarovat všechny proměnné pomocí `Dim` nebo `ReDim` příkazy. Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě při kompilaci. `Option Explicit Off` Příkaz umožňuje implicitní deklarace proměnných.  
  
 Pokud se používá, `Option Explicit` příkazu musí být v souboru před jakékoli jiné příkazy zdrojového kódu.  
  
> [!NOTE]
>  Nastavení `Option Explicit` k `Off` je obecně není vhodné. Může chybně název proměnné v jedné nebo více umístění, což by způsobilo neočekávané výsledky při spuštění programu.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Když se nenachází Option Explicit – příkaz  
 Pokud zdrojový kód neobsahuje `Option Explicit` příkaz, **Option Explicit** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud se používá kompilátoru příkazového řádku, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru se používá.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Chcete-li nastavit možnost explicitní v prostředí IDE  
  
1.  V **Průzkumníku**, vyberte projektu. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Nastavte hodnotu v **Option Explicit** pole.  
  
 Když vytvoříte nový projekt, **Option Explicit** nastavení na **zkompilovat** karta je nastaven na **Option Explicit** nastavení v **VB výchozí**dialogové okno. Pro přístup k **VB výchozí** v dialogovém **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**. Počáteční výchozí nastavení v **VB výchozí** je `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Chcete-li nastavit možnost explicitní na příkazovém řádku  
  
-   Zahrnout [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru v **Vbc –** příkaz.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Explicit` příkaz vynutíte explicitní deklaraci všech proměnných. Pokus o použití nedeklarované proměnná způsobí chybu v době kompilace.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
