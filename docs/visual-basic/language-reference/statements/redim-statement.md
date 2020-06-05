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
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404275"
---
# <a name="redim-statement-visual-basic"></a>ReDim – příkaz (Visual Basic)
Znovu přidělí prostor úložiště pro proměnnou pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|----------|----------------|  
|`Preserve`|Nepovinný parametr. Modifikátor používaný k zachování dat v existujícím poli při změně velikosti pouze poslední dimenze.|  
|`name`|Povinná hodnota. Název proměnné pole Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Povinná hodnota. Seznam hranic jednotlivých dimenzí předefinovaného pole|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `ReDim` příkazu můžete změnit velikost jedné nebo více dimenzí pole, které již bylo deklarováno. Pokud máte velké pole a již nepotřebujete některé z jeho prvků, `ReDim` může uvolnit paměť zmenšením velikosti pole. Na druhé straně, pokud vaše pole potřebuje více prvků, `ReDim` může je přidat.  
  
 `ReDim`Příkaz je určen pouze pro pole. Není platná pro skalární hodnoty (proměnné, které obsahují pouze jednu hodnotu), kolekce nebo struktury. Všimněte si, že pokud deklarujete proměnnou, která má být typu `Array` , `ReDim` příkaz nemá dostatečné informace o typu pro vytvoření nového pole.  
  
 Můžete použít `ReDim` pouze na úrovni procedury. Proto kontext deklarace pro proměnnou musí být procedura; nemůže to být zdrojový soubor, obor názvů, rozhraní, třída, struktura, modul nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Několik proměnných.** Můžete změnit velikost několika proměnných pole v rámci jednoho příkazu deklarace a zadat `name` součásti a `boundlist` pro každou proměnnou. Více proměnných je odděleno čárkami.  
  
- **Meze pole.** Každá položka v `boundlist` rámci může určovat dolní a horní hranici dané dimenze. Dolní mez je vždycky 0 (nula). Horní mez představuje nejvyšší možnou hodnotu indexu pro tuto dimenzi, nikoli délku dimenze (což je horní mez plus jedna). Index pro každou dimenzi se může od nuly lišit hodnotou horní meze.  
  
     Počet rozměrů v `boundlist` musí odpovídat původnímu počtu rozměrů pole (Rank).  
  
- **Datové typy.** `ReDim`Příkaz nemůže změnit datový typ proměnné pole nebo jejích elementů.  
  
- **Operace.** `ReDim`Příkaz nemůže poskytnout nové inicializační hodnoty pro prvky pole.  
  
- **Pořadí.** `ReDim`Příkaz nemůže změnit pořadí (počet rozměrů) pole.  
  
- **Změna velikosti se zachováním zachovat.** Pokud používáte `Preserve` , můžete změnit velikost jenom na poslední rozměr pole. Pro všechny ostatní dimenze je nutné zadat hranici existujícího pole.  
  
     Například pokud má vaše pole pouze jednu dimenzi, můžete změnit velikost této dimenze a zachovat obsah pole, protože měníte poslední a pouze dimenzi. Nicméně pokud má vaše pole dvě nebo více dimenzí, můžete změnit velikost pouze poslední dimenze, pokud použijete `Preserve` .  
  
- **Vlastnosti.** Můžete použít `ReDim` na vlastnost, která obsahuje pole hodnot.  
  
## <a name="behavior"></a>Chování  
  
- **Nahrazení pole** `ReDim`uvolní existující pole a vytvoří nové pole se stejným pořadím. Nové pole nahradí uvolněné pole v proměnné pole.  
  
- **Inicializace bez zachování.** Pokud nezadáte `Preserve` , `ReDim` inicializuje prvky nového pole pomocí výchozí hodnoty pro svůj datový typ.  
  
- **Inicializace s zachovat.** Pokud zadáte `Preserve` , Visual Basic zkopíruje prvky z existujícího pole do nového pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad zvětší velikost poslední dimenze dynamického pole, aniž by ztratila všechna existující data v poli, a pak zmenší velikost s částečnou ztrátou dat. Nakonec zmenší velikost zpátky na původní hodnotu a znovu inicializuje všechny prvky pole.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim`Příkaz vytvoří nové pole se třemi dimenzemi. Každá dimenze je deklarována s hranicí 10, takže index pole pro každou dimenzi může být v rozsahu od 0 do 10. V následující diskuzi se tři dimenze označují jako vrstvy, řádky a sloupce.  
  
 První `ReDim` vytvoří nové pole, které nahradí existující pole v proměnné `intArray` . `ReDim`zkopíruje všechny prvky z existujícího pole do nového pole. Přidá také 10 dalších sloupců na konec každého řádku v každé vrstvě a inicializuje prvky v těchto nových sloupcích na hodnotu 0 (výchozí hodnota `Integer` , což je typ prvku pole).  
  
 Druhý `ReDim` vytvoří další nové pole a zkopíruje všechny prvky, které odpovídají. Nicméně pět sloupců se na konci každého řádku v každé vrstvě ztratí. Nejedná se o problém, pokud jste s použitím těchto sloupců dokončili. Zmenšení velikosti velkého pole může uvolnit paměť, kterou už nepotřebujete.  
  
 Třetí `ReDim` vytvoří další nové pole a odebere další pět sloupců z konce každého řádku v každé vrstvě. Tentokrát nekopíruje žádné existující prvky. Tento příkaz vrátí pole do původní velikosti. Vzhledem k tomu, že příkaz neobsahuje `Preserve` modifikátor, nastaví všechny prvky pole na původní výchozí hodnoty.  
  
 Další příklady naleznete v tématu [Arrays](../../programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IndexOutOfRangeException>
- [Const – příkaz](const-statement.md)
- [Dim – příkaz](dim-statement.md)
- [Erase – příkaz](erase-statement.md)
- [Nothing](../nothing.md)
- [Pole](../../programming-guide/language-features/arrays/index.md)
