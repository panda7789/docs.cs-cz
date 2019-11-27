---
title: ReDim – příkaz
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
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346742"
---
# <a name="redim-statement-visual-basic"></a>ReDim – příkaz (Visual Basic)
Znovu přidělí prostor úložiště pro proměnnou pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|----------|----------------|  
|`Preserve`|Volitelná. Modifikátor používaný k zachování dat v existujícím poli při změně velikosti pouze poslední dimenze.|  
|`name`|Požadováno. Název proměnné pole Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Požadováno. Seznam hranic jednotlivých dimenzí předefinovaného pole|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí příkazu `ReDim` můžete změnit velikost jedné nebo více dimenzí pole, které již bylo deklarováno. Pokud máte velké pole a již nepotřebujete některé z jeho prvků, `ReDim` může uvolnit paměť zmenšením velikosti pole. Na druhé straně, pokud vaše pole potřebuje více prvků, `ReDim` je může přidat.  
  
 Příkaz `ReDim` je určen pouze pro pole. Není platná pro skalární hodnoty (proměnné, které obsahují pouze jednu hodnotu), kolekce nebo struktury. Všimněte si, že pokud deklarujete proměnnou, která má být typu `Array`, příkaz `ReDim` neobsahuje dostatečné informace o typu pro vytvoření nového pole.  
  
 `ReDim` můžete použít jenom na úrovni procedury. Proto kontext deklarace pro proměnnou musí být procedura; nemůže to být zdrojový soubor, obor názvů, rozhraní, třída, struktura, modul nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Několik proměnných.** Můžete změnit velikost několika proměnných pole v rámci jednoho příkazu deklarace a určit `name` a `boundlist` části pro každou proměnnou. Více proměnných je odděleno čárkami.  
  
- **Meze pole.** Každá položka v `boundlist` může určit dolní a horní hranici dané dimenze. Dolní mez je vždycky 0 (nula). Horní mez představuje nejvyšší možnou hodnotu indexu pro tuto dimenzi, nikoli délku dimenze (což je horní mez plus jedna). Index pro každou dimenzi se může od nuly lišit hodnotou horní meze.  
  
     Počet rozměrů v `boundlist` musí odpovídat původnímu počtu rozměrů pole (Rank).  
  
- **Datové typy.** Příkaz `ReDim` nemůže změnit datový typ proměnné pole nebo jejích elementů.  
  
- **Operace.** Příkaz `ReDim` nemůže poskytnout nové inicializační hodnoty pro prvky pole.  
  
- **Pořadí.** Příkaz `ReDim` nemůže změnit pořadí (počet rozměrů) pole.  
  
- **Změna velikosti se zachováním zachovat.** Pokud používáte `Preserve`, můžete změnit velikost pouze poslední dimenze pole. Pro všechny ostatní dimenze je nutné zadat hranici existujícího pole.  
  
     Například pokud má vaše pole pouze jednu dimenzi, můžete změnit velikost této dimenze a zachovat obsah pole, protože měníte poslední a pouze dimenzi. Pokud má ale vaše pole dvě nebo více dimenzí, můžete změnit velikost jenom poslední dimenze, pokud používáte `Preserve`.  
  
- **Vlastnosti.** Můžete použít `ReDim` u vlastnosti, která obsahuje pole hodnot.  
  
## <a name="behavior"></a>Chování  
  
- **Nahrazení pole** `ReDim` uvolní existující pole a vytvoří nové pole se stejným pořadím. Nové pole nahradí uvolněné pole v proměnné pole.  
  
- **Inicializace bez zachování.** Pokud nezadáte `Preserve`, `ReDim` inicializuje prvky nového pole pomocí výchozí hodnoty pro svůj datový typ.  
  
- **Inicializace s zachovat.** Pokud zadáte `Preserve`, Visual Basic zkopíruje prvky z existujícího pole do nového pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad zvětší velikost poslední dimenze dynamického pole, aniž by ztratila všechna existující data v poli, a pak zmenší velikost s částečnou ztrátou dat. Nakonec zmenší velikost zpátky na původní hodnotu a znovu inicializuje všechny prvky pole.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 Příkaz `Dim` vytvoří nové pole se třemi dimenzemi. Každá dimenze je deklarována s hranicí 10, takže index pole pro každou dimenzi může být v rozsahu od 0 do 10. V následující diskuzi se tři dimenze označují jako vrstvy, řádky a sloupce.  
  
 První `ReDim` vytvoří nové pole, které nahradí existující pole v proměnné `intArray`. `ReDim` zkopíruje všechny prvky z existujícího pole do nového pole. Přidává také 10 dalších sloupců na konec každého řádku v každé vrstvě a inicializuje prvky v těchto nových sloupcích na 0 (výchozí hodnota `Integer`, což je typ prvku pole).  
  
 Druhý `ReDim` vytvoří další nové pole a zkopíruje všechny prvky, které odpovídají. Nicméně pět sloupců se na konci každého řádku v každé vrstvě ztratí. Nejedná se o problém, pokud jste s použitím těchto sloupců dokončili. Zmenšení velikosti velkého pole může uvolnit paměť, kterou už nepotřebujete.  
  
 Třetí `ReDim` vytvoří další nové pole a z konce každého řádku v každé vrstvě odebere další pět sloupců. Tentokrát nekopíruje žádné existující prvky. Tento příkaz vrátí pole do původní velikosti. Vzhledem k tomu, že příkaz neobsahuje modifikátor `Preserve`, nastaví všechny prvky pole na původní výchozí hodnoty.  
  
 Další příklady naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IndexOutOfRangeException>
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Příkaz Erase](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
