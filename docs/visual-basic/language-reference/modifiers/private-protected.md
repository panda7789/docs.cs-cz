---
title: Chráněné privátní (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>Chráněné privátní (Visual Basic)

`Private Protected` – Kombinace klíčových slov je modifikátor přístupu členů. A `Private Protected` člen je dostupný ve své třídě obsahující všechny členy, a také pro typy odvozené od třídy obsahující, ale pouze v případě, že se nacházejí v jeho obsahující sestavení. 

Můžete zadat `Private Protected` pouze u členů tříd; nelze použít `Private Protected` u členů struktury protože struktury nemůže být zděděno.

`Private Protected` – Modifikátor přístupu jsou podporovány nástrojem 15,5 Visual Basic a vyšší. Pokud chcete použít, můžete přidat následující prvek se v souboru projektu (*.vbproj) jazyka Visual Basic. Jak dlouho jako 15,5 Visual Basic nebo novější je nainstalován ve vašem systému, umožňuje využít výhod všech funkcí jazyka nejnovější verze kompilátoru jazyka Visual Basic nepodporuje:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> V sadě Visual Studio, výběr F1 – Nápověda na `private protected` poskytuje nápovědu pro buď [privátní](private.md) nebo [chráněné](protected.md). Prostředí IDE vybere jeden token pod kurzor spíše než složené aplikace word.

## <a name="rules"></a>Pravidla

- **Kontext deklarace.** Můžete použít `Private Protected` pouze na úrovni třídy. To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** Všechny kódu v třídě mají přístup k jeho elementy. Kód do třídy, která je odvozena ze základní třídy a je obsažený ve stejném sestavení přístup k veškerým `Private Protected` elementy základní třídy. Však se kód do třídy, která je odvozena ze základní třídy a je obsažený v jiném sestavení nemůže přistupovat k základní třídy `Private Protected` elementy.

- **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 `Private Protected` Modifikátor lze použít v těchto kontexty:  
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) delegáta vnořené v třídě  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration vnořené v třídě 
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořené v třídě 
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořené v třídě 
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Chráněné Friend](./protected-friend.md)   
[Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
