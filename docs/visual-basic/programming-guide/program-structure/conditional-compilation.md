---
title: Podmíněná kompilace v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967846"
---
# <a name="conditional-compilation-in-visual-basic"></a>Podmíněná kompilace v jazyce Visual Basic
V *podmíněné kompilace*, konkrétní bloky kódu v programu v jazyce jsou selektivně zkompilován, zatímco jiné jsou ignorovány.  
  
 Například můžete chtít napsat ladění příkazů, které porovnat rychlost různé přístupy k stejné programovací úlohy, nebo může být vhodné lokalizovat aplikaci pro více jazyků. Příkazy podmíněné kompilace jsou navrženy ke spouštění během kompilace, ne za běhu.  
  
 Označení bloky kódu, který se podmíněně kompilována s `#If...Then...#Else` směrnice. Například vytvořit francouzština a němčina jazykové verze stejné aplikace ze stejného zdrojového kódu, vložení příslušných segmentech kódu specifické pro platformu v `#If...Then` příkazy pomocí předdefinovaných konstant `FrenchVersion` a `GermanVersion`. Následující příklad ukazuje, jak:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Pokud nastavíte hodnotu `FrenchVersion` Konstanta podmíněné kompilace do `True` v době kompilace, je zkompilován podmíněný kód pro francouzské verze. Pokud nastavíte hodnotu `GermanVersion` konstanta, která se `True`, kterou kompilátor používá německé verzi. Pokud ani jedno je nastavená na `True`, kód za posledních `Else` blok.  
  
> [!NOTE]
>  Automatického doplňování se nebude fungovat při úpravách kódu a pomocí direktivy podmíněné kompilace, pokud kód není součástí aktuální větve.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarace konstanty pro podmíněnou kompilaci  
 Konstanty pro podmíněnou kompilaci můžete nastavit v jednom ze tří způsobů:  
  
-   V **Návrhář projektu**  
  
-   Na příkazovém řádku při použití kompilátoru příkazového řádku  
  
-   V kódu  
  
 Konstanty pro podmíněnou kompilaci mají zvláštní obor a nelze přistupovat z standardní kód. Rozsah Konstanta podmíněné kompilace je závislé na způsobu, jakým je nastavena. V následující tabulce jsou uvedeny oboru konstanty, které jsou deklarovány pomocí každé ze tří způsobů uvedených výše.  
  
|Jak nastavit – konstanta|Obor – konstanta|  
|---|---|  
|**Project Designer**|Veřejné na všechny soubory v projektu|  
|Příkazový řádek|Veřejné na všechny soubory, které jsou předány kompilátoru příkazového řádku|  
|`#Const` příkaz v kódu|Soukromé vzhledem k souboru, ve kterém je deklarována|  
  
|Chcete-li nastavit konstanty v Návrháři projektu|  
|---|  
|-Před vytvořením spustitelného souboru, nastavte konstanty **Návrháře projektu** podle postupu uvedeného v [vlastností správy projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Chcete-li nastavit konstanty na příkazovém řádku|  
|---|  
|– Použijte **/d** přepínač tak, aby zadejte konstanty pro podmíněnou kompilaci, jako v následujícím příkladu:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Mezera není je vyžadován mezi **/d** přepínače a první konstanta. Další informace najdete v tématu [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Příkazového řádku deklarace přepsání zadaná v deklaracích **Návrháře projektu**, ale ne z nich vymazat obsah. Argumenty nastavit **Návrháře projektu** zůstávají v platnosti pro následné kompilace.<br />     Při zápisu konstanty v samotný kód, nejsou žádná pravidla striktní jde o jejich umístění, protože jejich oboru je celý modul, ve kterém jsou deklarovány.|  
  
|Chcete-li nastavit konstanty v kódu|  
|---|  
|-Umístíte konstanty v bloku deklaraci modulu, ve kterém jsou použity. Díky tomu váš kód uspořádané a snadněji čitelné.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|---|---|  
|[Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Nabízí návrhy pro snadné čtení a udržovat váš kód.|  
  
## <a name="reference"></a>Odkaz  
 [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
