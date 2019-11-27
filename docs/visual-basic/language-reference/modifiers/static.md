---
title: Statické
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350763"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Určuje, že nejmíň jedna z deklarovaných lokálních proměnných bude i po ukončení postupu, ve kterém jsou deklarované, dál existovat a uchovávat jejich nejnovější hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 V normálním případě místní proměnná v proceduře přestane existovat, jakmile se procedura zastaví. Statická proměnná stále existuje a uchovává její nejnovější hodnotu. Při příštím volání procedury kód, proměnná není znovu inicializována a stále obsahuje nejnovější hodnotu, kterou jste přiřadili. Statická proměnná bude nadále existovat po dobu života třídy nebo modulu, ve kterém je definována.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** `Static` můžete použít pouze pro místní proměnné. To znamená, že kontext deklarace pro proměnnou `Static` musí být procedura nebo blok v proceduře a nemůže se jednat o zdrojový soubor, obor názvů, třídu, strukturu nebo modul.  
  
     V proceduře struktury nelze použít `Static`.  
  
- Datové typy `Static` místních proměnných nelze odvodit. Další informace naleznete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Kombinované modifikátory.** V rámci stejné deklarace nelze zadat `Static` společně s `ReadOnly`, `Shadows`nebo `Shared`.  
  
## <a name="behavior"></a>Chování  
 Pokud deklarujete statickou proměnnou v `Shared` proceduře, je k dispozici pouze jedna kopie statické proměnné pro celou aplikaci. Proceduru `Shared` zavoláte pomocí názvu třídy, nikoli proměnné, která odkazuje na instanci třídy.  
  
 Pokud deklarujete statickou proměnnou v proceduře, která není `Shared`, je k dispozici pouze jedna kopie proměnné pro každou instanci třídy. Nesdílenou proceduru zavoláte pomocí proměnné, která odkazuje na konkrétní instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 Proměnná `Static` `totalSales` byla inicializována na hodnotu 0 pouze jednou. Pokaždé, když zadáte `updateSales`, má `totalSales` stále nejnovější hodnotu, kterou jste pro ni vypočítali.  
  
 V tomto kontextu lze použít modifikátor `Static`:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Doba života v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
