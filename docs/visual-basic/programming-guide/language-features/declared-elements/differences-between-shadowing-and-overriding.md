---
title: Rozdíly mezi stínováním a přepsáním (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827923"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Rozdíly mezi stínováním a přepsáním (Visual Basic)
Když definujete třídu, která dědí ze základní třídy, můžete někdy chtít znovu definovat jeden nebo více prvků základní třídy v odvozené třídě. Stínováním a přepsáním jsou k dispozici pro tento účel.  
  
## <a name="comparison"></a>Srovnání  
 Stínováním a přepsáním se oba používají při odvozená třída dědí ze základní třídy a obě znovu definovat jeden element deklarovaný s jiným. Ale existují významné rozdíly mezi nimi.  
  
 Následující tabulka porovnává stínový provoz pomocí přepsání.  
  
||||  
|---|---|---|  
|Porovnání|Stínování|Přepsání|  
|Účel|Chrání proti následné změny základní třídy, která představuje člena, které jsou již definovány v odvozené třídě|Dosahuje jinou implementaci procedury nebo vlastnost se stejnou volací sekvence definování polymorfismu<sup>1</sup>|  
|Předefinované – element|Některé deklarovaný typ elementu|Pouze procedury (`Function`, `Sub`, nebo `Operator`) nebo vlastnost|  
|Element, nově definují obor|Některé deklarovaný typ elementu|Pouze procedura nebo vlastnost s identické volací sekvence<sup>1</sup>|  
|Úroveň přístupu, nově definují obor – element|Žádné úrovně přístupu|Nelze změnit úroveň přístupu přepsaný prvek|  
|Hlediska čitelnosti a zapisovatelnosti z elementu, nově definují obor|Libovolná kombinace|Nelze změnit čitelnosti a zapisovatelnosti přepsané vlastnosti|  
|Možnost ovládat, nově definují obor|Základní třída prvku nelze vynutit nebo zakázat stínování|Můžete určit základní třída prvku `MustOverride`, `NotOverridable`, nebo `Overridable`|  
|Využití – klíčové slovo|`Shadows` doporučení v odvozené třídě; `Shadows` předpokládá, že pokud ani jedno `Shadows` ani `Overrides` zadané<sup>2</sup>|`Overridable` nebo `MustOverride` vyžaduje v základní třídě; `Overrides` potřebné v odvozené třídě|  
|Dědičnost třídy odvozené z odvozené třídy, nově definují obor – element|Kontrastními element dědí další odvozené třídy; Stínovaný stále skrytý element<sup>3</sup>|Přepsání element dědí další odvozené třídy; přepsaný prvek stále přepsat.|  
  
 <sup>1</sup> *volání pořadí* se skládá z typ elementu (`Function`, `Sub`, `Operator`, nebo `Property`), pojmenujte, seznam parametrů a návratový typ. Nejde přepsat procedura se vlastnost nebo naopak. Nejde přepsat jeden druh procedury (`Function`, `Sub`, nebo `Operator`) pomocí jiného druhu.  
  
 <sup>2</sup> Pokud nezadáte buď `Shadows` nebo `Overrides`, kompilátor vyvolá upozornění můžete být jisti, jaký druh nová definice, kterou chcete použít. Pokud budete toto upozornění ignorovat, stínového provozu mechanismu, který se používá.  
  
 <sup>3</sup> Pokud stínového provozu prvek je přístupný v další odvozené třídy, není zděděno stínováním. Například, pokud deklarujete stínového provozu prvek jako `Private`, původní elementu namísto stínového provozu element dědí třídu odvozenou z odvozené třídy.  
  
## <a name="guidelines"></a>Pokyny  
 Obvykle použijete přepsání v následujících případech:  
  
-   Definování polymorfní odvozené třídy.  
  
-   Chcete, aby bezpečnost s kompilátoru vynutit typ elementu identické a volací sekvence.  
  
 Obvykle použijete stínění v následujících případech:  
  
-   Očekáváte, že základní třídy se může změnit a definovat elementu s použitím se stejným názvem se nenachází žádný.  
  
-   Chcete, aby svobody změna typ prvku nebo sekvence volání.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
