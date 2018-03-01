---
title: Static (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Určuje, že jeden nebo více deklarované lokální proměnné jsou nadále existovat a po ukončení procesu, ve které jsou deklarovány zachovat jejich nejnovější hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Za normálních okolností místní proměnné v postupu přestane existovat také zastaví proces. Statické proměnné nadále existovat a jeho nejnovější hodnotu zachová. Při příštím kódu volá proceduru, není inicializace proměnné a že dál obsahuje nejpozdější hodnotu, který jste přiřadili k němu. Statické proměnné i nadále existovat pro životnost třídu nebo modul, který je definován v.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Static` pouze na místní proměnné. To znamená kontext deklarace `Static` proměnná musí být procedury nebo blok v postupu, a nelze ji zdrojový soubor, obor názvů, třídy, struktury nebo modul.  
  
     Nemůžete použít `Static` uvnitř procedury struktura.  
  
-   Datové typy `Static` místní proměnné nelze odvodit. Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Kombinovaná parametrů.** Nelze zadat `Static` společně s `ReadOnly`, `Shadows`, nebo `Shared` ve stejné deklaraci.  
  
## <a name="behavior"></a>Chování  
 Když je deklarovat statickou proměnnou v `Shared` postup, pouze jedna kopie statické proměnné je k dispozici pro celou aplikaci. Volání `Shared` název postupu pomocí třídy, ne proměnné, která odkazuje na instanci třídy.  
  
 Když je deklarovat statické proměnné v postupu, který není `Shared`, pouze jedna kopie proměnné je k dispozici pro každou instanci třídy. Volání procedury, nesdílené pomocí proměnné, která odkazuje na konkrétní instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static` Proměnná `totalSales` je inicializováno 0 pouze jednou. Pokaždé, když zadáte `updateSales`, `totalSales` má stále nejnovější hodnotu, kterou jste vypočítali pro něj.  
  
 `Static` Modifikátor můžete v tomto kontextu použít:  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Sdílené](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Doba platnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
