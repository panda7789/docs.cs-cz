---
title: Podmíněná kompilace
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: c3eb1eb57b3d76e762ed53edb3b168ad96abec39
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403262"
---
# <a name="conditional-compilation-in-visual-basic"></a>Podmíněná kompilace v jazyce Visual Basic
V *podmíněné kompilaci*jsou konkrétní bloky kódu v programu kompilovány selektivně, zatímco ostatní jsou ignorovány.  
  
 Například můžete chtít napsat příkazy ladění, které porovnávají rychlost různých přístupů ke stejnému programovacímu úkolu, nebo můžete chtít lokalizovat aplikaci pro více jazyků. Příkazy podmíněné kompilace jsou navrženy tak, aby běžely v době kompilace, nikoli v době běhu.  
  
 Všimněte si, že bloky kódu budou podmíněně kompilovány s `#If...Then...#Else` direktivou. Chcete-li například vytvořit francouzsky a německé jazykové verze stejné aplikace ze stejného zdrojového kódu, vložte segmenty kódu specifické pro platformu v `#If...Then` příkazech pomocí předdefinovaných konstant `FrenchVersion` a `GermanVersion` . Následující příklad ukazuje, jak:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Pokud nastavíte hodnotu `FrenchVersion` konstanty podmíněné kompilace na `True` v době kompilace, bude zkompilován podmíněný kód pro francouzskou verzi. Pokud nastavíte hodnotu `GermanVersion` konstanty na `True` , kompilátor použije německou verzi. Pokud není ani nastaveno na `True` , kód v posledním bloku se `Else` spustí.  
  
> [!NOTE]
> Automatického dokončování nebude fungovat při úpravách kódu a použití direktiv podmíněné kompilace, pokud kód není součástí aktuální větve.  
  
## <a name="declaring-conditional-compilation-constants"></a>Deklarace konstant podmíněné kompilace  
 Můžete nastavit konstanty podmíněné kompilace jedním ze tří způsobů:  
  
- V **Návrháři projektu**  
  
- Při použití kompilátoru příkazového řádku na příkazovém řádku  
  
- Ve vašem kódu  
  
 Konstanty podmíněné kompilace mají speciální rozsah a nelze k němu přicházet ze standardního kódu. Rozsah podmíněné kompilační konstanty závisí na způsobu, jakým je nastaven. V následující tabulce je uveden rozsah konstant deklarovaných pomocí každého ze tří způsobů uvedených výše.  
  
|Jak je nastavená konstanta|Rozsah konstanty|  
|---|---|  
|**návrhář projektu**|Veřejné pro všechny soubory v projektu|  
|Příkazový řádek|Veřejné ke všem souborům předaným kompilátoru příkazového řádku|  
|`#Const`příkaz v kódu|Soukromá k souboru, ve kterém je deklarovaný|  
  
|Nastavení konstant v Návrháři projektu|  
|---|  
|– Před vytvořením spustitelného souboru nastavte konstanty v **Návrháři projektu** podle kroků uvedených v části [Správa vlastností projektu a řešení](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Nastavení konstant na příkazovém řádku|  
|---|  
|– Použijte přepínač **-d** k zadání konstant podmíněné kompilace, jako v následujícím příkladu:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Mezi přepínačem **-d** a první konstantou není nutné žádné místo. Další informace naleznete v tématu [-define (Visual Basic)](../../reference/command-line-compiler/define.md).<br />     Deklarace příkazového řádku, které jsou popsány v **Návrháři projektu**, však nejsou smazány. Argumenty nastavené v **Návrháři projektu** zůstávají platné pro následné kompilace.<br />     Při psaní konstant v samotném kódu nejsou k dispozici žádná striktní pravidla pro jejich umístění, protože jejich rozsah je celý modul, ve kterém jsou deklarovány.|  
  
|Nastavení konstant v kódu|  
|---|  
|-Vložte konstanty do bloku deklarací modulu, ve kterém jsou použity. To pomáhá zajistit, aby byl kód uspořádán a čitelnější.|  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|---|---|  
|[Struktura programu a konvence kódu](program-structure-and-code-conventions.md)|Poskytuje návrhy, jak snadno číst a udržovat váš kód.|  
  
## <a name="reference"></a>Referenční informace  
 [#Const direktiva](../../language-reference/directives/const-directive.md)  
  
 [#If... Then... #Else – direktivy](../../language-reference/directives/if-then-else-directives.md)  
  
 [-define (Visual Basic)](../../reference/command-line-compiler/define.md)
