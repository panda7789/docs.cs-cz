---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 3b323d5fb1c4f1357b9f476213793c69d29b7208
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402691"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Určuje, že nejmíň jedna z deklarovaných lokálních proměnných bude i po ukončení postupu, ve kterém jsou deklarované, dál existovat a uchovávat jejich nejnovější hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 V normálním případě místní proměnná v proceduře přestane existovat, jakmile se procedura zastaví. Statická proměnná stále existuje a uchovává její nejnovější hodnotu. Při příštím volání procedury kód, proměnná není znovu inicializována a stále obsahuje nejnovější hodnotu, kterou jste přiřadili. Statická proměnná bude nadále existovat po dobu života třídy nebo modulu, ve kterém je definována.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** Můžete použít `Static` pouze pro místní proměnné. To znamená, že kontext deklarace `Static` proměnné musí být procedura nebo blok v proceduře a nemůže se jednat o zdrojový soubor, obor názvů, třídu, strukturu nebo modul.  
  
     `Static`V rámci struktury nelze použít proceduru.  
  
- Datové typy `Static` místních proměnných nelze odvodit. Další informace naleznete v tématu [odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md).  
  
- **Kombinované modifikátory.** Nelze zadat `Static` společně s `ReadOnly` , `Shadows` nebo `Shared` ve stejné deklaraci.  
  
## <a name="behavior"></a>Chování  
 Pokud deklarujete statickou proměnnou v `Shared` proceduře, je k dispozici pouze jedna kopie statické proměnné pro celou aplikaci. Proceduru zavoláte `Shared` pomocí názvu třídy, nikoli proměnné, která odkazuje na instanci třídy.  
  
 Pokud deklarujete statickou proměnnou v proceduře, která není `Shared` , je k dispozici pouze jedna kopie proměnné pro každou instanci třídy. Nesdílenou proceduru zavoláte pomocí proměnné, která odkazuje na konkrétní instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Static` .  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`Proměnná `totalSales` je inicializována na hodnotu 0 pouze jednou. Pokaždé, když zadáte `updateSales` , `totalSales` má stále nejnovější hodnotu, kterou jste pro ni vypočítali.  
  
 `Static`V tomto kontextu lze použít modifikátor:  
  
 [Dim – příkaz](../statements/dim-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Shadows](shadows.md)
- [Shared](shared.md)
- [Doba platnosti v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Deklarace proměnné](../../programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
