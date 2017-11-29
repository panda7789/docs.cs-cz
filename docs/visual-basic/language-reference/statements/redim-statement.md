---
title: "ReDim – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cec66ee33bfd82b3abd623a0130f5635aa3d1d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="redim-statement-visual-basic"></a>ReDim – příkaz (Visual Basic)
Přidělí prostor úložiště pro proměnné pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|----------|----------------|  
|`Preserve`|Volitelné. Modifikátor umožňuje zachovat data v existující pole, když změníte velikost pouze poslední dimenze.|  
|`name`|Požadováno. Název proměnné pole. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Požadováno. Seznam mezí Každá dimenze Předefinovaná pole.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `ReDim` příkaz ke změně velikosti jeden nebo více rozměry pole, které již byl deklarován. Pokud máte velké pole a některé jeho elementy již nepotřebujete `ReDim` můžete uvolnit paměť snížením velikost pole. Na druhé straně, pokud další prvky, musí vaše pole `ReDim` je přidat.  
  
 `ReDim` Příkaz je určena pouze pro pole. Není platný na skalárních hodnot (proměnné, které obsahují pouze jednu hodnotu), kolekce nebo struktury. Všimněte si, že pokud deklarovat proměnnou být typu `Array`, `ReDim` příkaz nemá dostatek informací o typu vytvořte nové pole.  
  
 Můžete použít `ReDim` jenom na úrovni postupu. Kontext deklarace proměnné proto musí být procedury; nemůže být zdrojový soubor, obor názvů, rozhraní, třídy, struktury, modul nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Více proměnných.** Můžete změnit velikost několik proměnné pole v jednom příkazu deklarace a určit, `name` a `boundlist` částí pro každou proměnnou. Více proměnných jsou oddělené čárkami.  
  
-   **Meze pole.** Každá položka v `boundlist` můžete určit, dolní a horní meze této dimenze. Dolní hranice je vždy 0 (nula). Horní mez je hodnota nejvyšší možné indexu pro daná dimenze, není délka dimenze (což je horní mez plus jedna). Index pro Každá dimenze se může lišit od 0 do jeho horní mez hodnoty.  
  
     Počet dimenzí v `boundlist` původní počet rozměrů (pořadí) pole se musí shodovat.  
  
-   **Datové typy.** `ReDim` Příkaz nelze změnit datový typ proměnné pole nebo jeho prvky.  
  
-   **Inicializace.** `ReDim` Příkaz nelze zadat nové inicializace hodnoty pro elementy pole.  
  
-   **Pořadí.** `ReDim` Příkaz nelze změnit pořadí pole (počet dimenzí).  
  
-   **Změna velikosti s zachovat.** Pokud používáte `Preserve`, můžete změnit velikost pouze poslední dimenze pole. Pro každý další dimenze je nutné zadat mez existující pole.  
  
     Například pokud vaše pole má jenom jednu dimenzi, můžete změnit velikost daná dimenze a současně zachovat veškerý obsah pole, protože měníte jenom dimenze a poslední. Ale pokud vaše pole má dvě nebo více dimenzí, je možné změnit velikost pouze poslední dimenze používáte `Preserve`.  
  
-   **Vlastnosti.** Můžete použít `ReDim` u vlastnosti, která obsahuje pole hodnot.  
  
## <a name="behavior"></a>Chování  
  
-   **Pole nahrazení.** `ReDim`uvolní existující pole a vytvoří nové pole s stejné pořadí. Nové pole nahrazuje pole vydaných v proměnné pole.  
  
-   **Inicializace bez zachovat.** Pokud nezadáte `Preserve`, `ReDim` inicializuje prvky nové pole pomocí výchozí hodnota pro datového typu.  
  
-   **Inicializace se zachovat.** Pokud zadáte `Preserve`, Visual Basic zkopíruje elementy ze stávající pole do nové pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad zvyšuje velikost poslední dimenze dynamické pole bez ztráty jakákoli stávající data v poli a potom snižuje velikost ztráty částečná data. Nakonec snižuje velikost zpět na původní hodnotu a znovu inicializuje všechny elementy pole.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 `Dim` Příkaz vytvoří nové pole s tři dimenze. Každá dimenze je deklarovaný s mez 10, takže index pole pro každý dimenze může být v rozsahu od 0 až 10. V následující diskusi tři dimenze jsou označovány jako vrstvy, řádků a sloupců.  
  
 První `ReDim` vytvoří nové pole, které nahradí stávající pole v proměnné `intArray`. `ReDim`zkopíruje všechny elementy z existující pole do nové pole. Také přidá na konec každý řádek v každé vrstvě 10 více sloupců a inicializuje elementů v tyto nové sloupce na hodnotu 0 (výchozí hodnota `Integer`, což je typ elementu pole).  
  
 Druhý `ReDim` vytvoří jiné nové pole a zkopíruje všechny prvky, které vyhovují. Pět sloupce jsou však ztraceny od konce každý řádek v každé vrstvě. To není problém, pokud dokončíte používání těchto sloupců. Zmenšení velikosti velké pole můžete uvolnit paměť, která již nepotřebujete.  
  
 Třetí `ReDim` vytvoří jiné nové pole a odebere jiné pět sloupců z konce každý řádek v každé vrstvě. Tentokrát ho nekopíruje existující prvky. Tento příkaz vrátí pole pro její původní velikost. Vzhledem k tomu, že neobsahuje příkaz `Preserve` modifikátor, nastaví všechny elementy pole na původní výchozí hodnoty.  
  
 Další příklady najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IndexOutOfRangeException>  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Erase – příkaz](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nic](../../../visual-basic/language-reference/nothing.md)  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
