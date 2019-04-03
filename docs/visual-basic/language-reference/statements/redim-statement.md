---
title: ReDim – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8f5f3172eaa6b43d9b07aefa0036708b26087777
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824114"
---
# <a name="redim-statement-visual-basic"></a>ReDim – příkaz (Visual Basic)
Znovu alokuje prostor úložiště pro proměnné pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|----------|----------------|  
|`Preserve`|Volitelné. Modifikátor se používá k zachování dat v existujícím poli, když změníte velikost jenom poslední dimenze.|  
|`name`|Povinný parametr. Název proměnné pole. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Povinný parametr. Seznam mezí jednotlivých rozměrů pole Předefinovaná.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `ReDim` příkaz ke změně velikosti jednu nebo více dimenzí pole, které je už deklarovaný. Pokud máte velké pole a které už nepotřebujete, některé z jeho prvků `ReDim` může uvolnit paměť snížením velikosti pole. Na druhou stranu, pokud další prvky, musí vaše pole `ReDim` můžete je přidat.  
  
 `ReDim` Příkaz je určena pouze pro pole. Není platný v skaláry (proměnné, které obsahují jenom jedna hodnota), kolekce nebo struktury. Všimněte si, že pokud deklarujete proměnnou typu `Array`, `ReDim` příkaz nemá dostatek informací o typu k vytvoření nové pole.  
  
 Můžete použít `ReDim` pouze na úrovni postup. Místní deklarace proměnné proto musí být postup; ho nemůže být zdrojový soubor, obor názvů, rozhraní, třídy, struktury, modul nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Více proměnných.** Můžete změnit velikost několik proměnných ve stejném příkazu deklarace a určit, `name` a `boundlist` částí pro každou proměnnou. Více proměnných jsou odděleny čárkami.  
  
-   **Array Bounds.** Každá položka v `boundlist` můžete zadat, dolní a horní hranice této dimenze. Dolní mez je vždy 0 (nula). Horní mez je nejvyšší hodnota možný index pro tuto dimenzi, nikoli velikost rozměru (což je horní mez plus jedna). Index každé dimenze se může lišit od 0 do jeho hodnotu horní mez.  
  
     Počet dimenzí v `boundlist` musí odpovídat původní počet rozměrů (pořadí) pole.  
  
-   **Datové typy.** `ReDim` Příkaz nelze změnit datový typ proměnné pole nebo jeho elementů.  
  
-   **Inicializace.** `ReDim` Příkaz nelze zadat nové inicializace hodnoty pro prvky pole.  
  
-   **Pořadí.** `ReDim` Příkaz nelze změnit pořadí (počet rozměrů) v poli.  
  
-   **Změna velikosti se zachová.** Pokud používáte `Preserve`, změníte velikost jenom poslední dimenze pole. Pro každou dimenzi je nutné zadat mez existujícího pole.  
  
     Například pokud vaše pole má pouze jednu dimenzi, můžete změnit velikost daná dimenze a zároveň zachovat veškerý obsah pole, protože se mění poslední a pouze dimenze. Nicméně pokud vaše pole má dvě nebo více dimenzí, můžete změnit velikost jenom poslední dimenze používáte `Preserve`.  
  
-   **Vlastnosti.** Můžete použít `ReDim` na vlastnost, která obsahuje pole hodnot.  
  
## <a name="behavior"></a>Chování  
  
-   **Nahrazení pole.** `ReDim` uvolní existujícího pole a vytvoří nové pole obsahující stejné pořadí. Nové pole nahradí vydané pole v proměnné pole.  
  
-   **Inicializace bez zachování.** Pokud nezadáte `Preserve`, `ReDim` inicializuje elementy nové pole pomocí výchozí hodnota pro jejich datové typy.  
  
-   **Inicializace pomocí zachovat.** Pokud zadáte `Preserve`, Visual Basic zkopíruje prvky z existujícího pole do nového pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad zvyšuje velikost poslední dimenze dynamické pole bez ztráty všechna existující data v poli a pak snižuje velikost ztráty částečná data. Nakonec se zmenší velikost zpět na původní hodnotu a znovu inicializuje všechny prvky pole.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim` Příkaz vytvoří nové pole s tři dimenze. Každé dimenze je deklarován s hranicí 10, takže index pole pro jednotlivé rozměry v rozsahu 0 až 10. V následující diskuse tři dimenze jsou označovány jako vrstva, řádků a sloupců.  
  
 První `ReDim` vytvoří nové pole, která nahradí stávající pole v proměnné `intArray`. `ReDim` zkopíruje všechny prvky z existujícího pole do nového pole. Také přidá 10 další sloupce na konci každého řádku v každé vrstvě a inicializuje prvky v těchto nových sloupců na hodnotu 0 (výchozí hodnota `Integer`, což je typ prvku pole).  
  
 Druhá `ReDim` vytvoří další nové pole a zkopíruje všechny prvky, které vyhovují. Pět sloupců se ale ztratí z konci každého řádku v každé vrstvě. To není problém, pokud jste dokončili pomocí těchto sloupců. Zmenšit velké pole můžete uvolnit paměť, která už nepotřebujete.  
  
 Třetí `ReDim` vytvoří další nové pole a odebere jiného pět sloupců z konci každého řádku v každé vrstvě. Tentokrát nekopíruje jakýchkoli prvků. Tento příkaz vrátí pole původní velikost. Protože neobsahuje příkaz `Preserve` modifikátor, nastaví všechny prvky pole na původní výchozí hodnoty.  
  
 Další příklady najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IndexOutOfRangeException>
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Příkaz Erase](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
