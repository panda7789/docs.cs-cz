---
title: "Option Compare – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00753eddb641c07ef9c6e6282fe00c5e8d00547a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="option-compare-statement"></a>Option Compare – příkaz
Deklaruje výchozí metoda porovnání pro použití při porovnávání dat řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`Binary`|Volitelné. Výsledkem porovnání řetězců podle pořadí řazení odvozené z interní binární reprezentace znaky.<br /><br /> Tento typ porovnání je užitečný zejména v případě, že řetězce mohou obsahovat znaky, které nemají interpretovat jako text. V takovém případě nechcete na posunu porovnání s abecedním rovnocenností, jako je například nerozlišování.|  
|`Text`|Volitelné. Výsledkem porovnání řetězců podle pořadí řazení velká a malá písmena text určen podle národního prostředí vašeho systému.<br /><br /> Tento typ porovnání je užitečný, pokud vaše řetězce obsahovat všechny znaky textu a chcete porovnat je s ohledem na účet abecedním rovnocenností například nerozlišování a úzce související písmena. Například můžete chtít zvážit `A` a `a` být stejné, a `Ä` a `ä` na dřívější než `B` a `b`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud se používá, `Option Compare` příkazu musí být v souboru před jakékoli jiné příkazy zdrojového kódu.  
  
 `Option Compare` Příkaz určuje metodu porovnání řetězce (`Binary` nebo `Text`).  Výchozí metoda porovnání textu je `Binary`.  
  
 A `Binary` porovnání porovná číselnou hodnotu Unicode každý znak v každé řetězec. A `Text` porovnání porovná každý znak Unicode podle její lexikální význam v aktuální jazykovou verzi.  
  
 V systému Windows je určen pořadí řazení podle znakové stránky. Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).  
  
 V následujícím příkladu, řazení znaků v angličtině nebo Evropské znaková stránka (ANSI 1252) pomocí `Option Compare Binary`, který vytváří typické binární řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Když jsou seřazeny stejné znaky na stejné stránce kódu s použitím `Option Compare Text`, vytváří následující text pořadí řazení.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Při porovnání možnost příkazu není k dispozici  
 Pokud zdrojový kód neobsahuje `Option Compare` příkaz, **možnost porovnat** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud používáte kompilátoru příkazového řádku, nastavení určeného [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru se používá.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Chcete-li nastavit možnost porovnat v prostředí IDE  
  
1.  V **Průzkumníku**, vyberte projektu. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Nastavte hodnotu v **možnost porovnat** pole.  
  
 Při vytváření projektu, **možnost porovnat** nastavení na **zkompilovat** karta je nastaven na **možnost porovnat** nastavení v **možnosti** Dialogové okno. Chcete-li změnit toto nastavení na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**. Počáteční výchozí nastavení v **VB výchozí** je **binární**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Chcete-li nastavit možnost porovnat na příkazovém řádku  
  
-   Zahrnout [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru v **Vbc –** příkaz.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Compare` příkaz binární porovnání nastavit jako výchozí metoda porovnání řetězce. Chcete-li použít tento kód, zrušte komentář u `Option Compare Binary` příkaz a umístí jej v horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Compare` příkaz nastavit pořadí řazení velká a malá písmena text jako výchozí metoda porovnání řetězce. Chcete-li použít tento kód, zrušte komentář u `Option Compare Text` příkaz a umístí jej v horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)  
 [Řetězcové funkce](../../../visual-basic/language-reference/functions/string-functions.md)  
 [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
