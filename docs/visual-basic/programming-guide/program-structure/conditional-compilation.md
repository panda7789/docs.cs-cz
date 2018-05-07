---
title: Podmíněná kompilace v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="conditional-compilation-in-visual-basic"></a>Podmíněná kompilace v jazyce Visual Basic
V *Podmíněná kompilace*, konkrétní bloky kódu v programu kompilovány selektivně, zatímco další se ignorují.  
  
 Například můžete chtít zápisu ladění příkazy, které porovnávají rychlosti různý přístup do stejné programovací úlohy, nebo můžete chtít lokalizace aplikace pro více jazyků. Podmíněná kompilace příkazy jsou navrženy pro spuštění při kompilaci, není v době běhu.  
  
 Označují bloky kódu podmíněně sestavují s `#If...Then...#Else` – direktiva. Například k vytvoření francouzštinu a češtinu jazykové verze stejné aplikace ze stejného zdrojového kódu, vložení kódu pro konkrétní platformu segmentů v `#If...Then` příkazy pomocí předdefinovaných konstanty `FrenchVersion` a `GermanVersion`. Následující příklad ukazuje, jak:  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Pokud nastavíte hodnotu `FrenchVersion` konstanta Podmíněná kompilace pro `True` při kompilaci, kompilace podmíněného kódu pro je francouzská verze. Pokud nastavíte hodnotu `GermanVersion` konstanta, která se `True`, kompilátor použije německé verzi. Pokud ani jeden z nich je nastavený na `True`, kód za posledních `Else` blokovat spuštění.  
  
> [!NOTE]
>  Automatické dokončování není funkce při úpravě code a pomocí direktiv Podmíněná kompilace, pokud kód není součástí aktuální větve.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarace konstant Podmíněná kompilace  
 Podmíněná kompilace konstanty můžete nastavit v jednom ze tří způsobů:  
  
-   V **Návrhář projektu**  
  
-   Na příkazovém řádku při použití příkazového řádku kompilátoru  
  
-   V kódu  
  
 Podmíněná kompilace konstanty mít speciální obor a nelze získat přístup z standardní kódu. Rozsah konstanta Podmíněná kompilace je závislé na způsobu, jakým je nastavena. Následující tabulka uvádí oboru konstanty deklarováno s použitím každého ze tří způsobů uvedených výše.  
  
|Nastavení konstanta|Rozsah konstanta|  
|---|---|  
|**Návrhář projektu**|Veřejné pro všechny soubory v projektu|  
|Příkazový řádek|Veřejné ke všem souborům předaný kompilátoru příkazového řádku|  
|`#Const` příkaz v kódu|Privátní do souboru, ve kterém je deklarovaná|  
  
|Chcete-li nastavit konstanty v Návrháři projektu|  
|---|  
|-Před vytvořením spustitelný soubor, nastavte konstanty **Návrhář projektu** podle kroků uvedených v [vlastností Správa projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Chcete-li nastavit konstanty na příkazovém řádku|  
|---|  
|-Použít **/d** přepínač tak, aby zadejte Podmíněná kompilace konstanty, jako v následujícím příkladu:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Je vyžadován mezi žádné místo **/d** přepínač a první konstanta. Další informace najdete v tématu [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Příkazového řádku deklarace přepsání deklarace zadané v **Návrhář projektu**, ale není z nich vymazat obsah. Argumenty nastavit **Návrhář projektu** zůstávají platná pro následné kompilace.<br />     Při zápisu konstanty v samotný kód, nejsou vzhledem k tomu, že jejich obor je celý modul, ve které jsou deklarované žádná striktní pravidla, jejich umístění.|  
  
|Chcete-li nastavit konstanty v kódu|  
|---|  
|-Umístíte konstanty v bloku deklarace modulu, ve kterém se používají. To pomáhá chránit váš kód uspořádány snadněji číst.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|---|---|  
|[Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Poskytuje doporučení pro snadné číst a spravovat váš kód.|  
  
## <a name="reference"></a>Odkaz  
 [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
