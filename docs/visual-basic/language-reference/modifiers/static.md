---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f1031fe005a2fc264b50116b8ea3311dc7065dbc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647643"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Určuje, že nejmíň jeden z deklarovaných lokálních proměnných jsou dál existovat a zachovat svou poslední hodnotu po ukončení procesu, ve kterém jsou deklarovány.  
  
## <a name="remarks"></a>Poznámky  
 Za normálních okolností místní proměnné v postupu zaniká ihned poté, co proces se zastaví. Statická proměnná existuje i nadále a zachová svou poslední hodnotu. Při příštím kódu volá proceduru, proměnná není opakování inicializace odběrů a dál obsahuje nejnovější hodnotu, který jste přiřadili. Statická proměnná nebude existuje po dobu životnosti třídu nebo modul, který je definován v i nadále.  
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `Static` pouze pro místní proměnné. To znamená, že deklarace kontext `Static` proměnná musí být procedura nebo blok v postupu, a nemůže být zdrojový soubor, obor názvů, třídy, struktury nebo modulu.  
  
     Nemůžete použít `Static` uvnitř procedury struktury.  
  
- Datové typy `Static` lokální proměnné nelze odvodit. Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Kombinované modifikátory.** Nelze zadat `Static` spolu s `ReadOnly`, `Shadows`, nebo `Shared` ve stejné deklaraci.  
  
## <a name="behavior"></a>Chování  
 Pokud deklarujete statickou proměnnou `Shared` postupu jenom jednu kopii statická proměnná je k dispozici pro celou aplikaci. Volání `Shared` název postupu pomocí třídy, není proměnná, která odkazuje na instanci třídy.  
  
 Pokud deklarujete statická proměnná v postupu, který není `Shared`pouze jednu kopii proměnné je k dispozici pro každou instanci třídy. Volání procedury nesdílené pomocí proměnné, která odkazuje na konkrétní instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` Proměnnou `totalSales` je inicializován na hodnotu 0 pouze jednou. Pokaždé, když zadáte `updateSales`, `totalSales` stále obsahuje nejnovější hodnotu, kterou jste vypočítali pro něj.  
  
 `Static` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Doba platnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
