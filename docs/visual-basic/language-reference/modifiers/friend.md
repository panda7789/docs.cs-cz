---
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351563"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci sestavení, které obsahuje jejich deklaraci.  
  
## <a name="remarks"></a>Poznámky  
 V mnoha případech požadujete, aby byly programovací prvky, jako jsou třídy a struktury, použity celým sestavením, nikoli pouze komponentou, která je deklaruje. Je však možné, že nechcete, aby byly přístupné pomocí kódu mimo sestavení (například pokud je aplikace proprietární). Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí modifikátoru `Friend`.  
  
 Kód v jiných třídách, strukturách a modulech, které jsou zkompilovány do stejného sestavení, mají přístup ke všem prvkům `Friend` v tomto sestavení.  
  
 přístup k `Friend` je často upřednostňovanou úrovní pro programovací prvky aplikace a `Friend` je výchozí úrovní přístupu rozhraní, modulu, třídy nebo struktury.  
  
 `Friend` můžete použít jenom na úrovni modulu, rozhraní nebo oboru názvů. Proto kontext deklarace pro prvek `Friend` musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura; nemůže se jednat o proceduru.  

> [!NOTE]
> Můžete použít také modifikátor [Protected Friend](protected-friend.md) Access, který zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná. Chcete-li omezit přístup ke členovi z jeho třídy a z odvozených tříd ve stejném sestavení, použijte modifikátor [privátního chráněného](private-protected.md) přístupu.

 Porovnání `Friend` a dalších modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Můžete určit, že jiné sestavení je sestavení typu Friend, které umožňuje přístup ke všem typům a členům, které jsou označeny jako `Friend`. Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).

## <a name="example"></a>Příklad  
 Následující třída používá modifikátor `Friend`, aby umožnil ostatním programovacím prvkům v rámci stejného sestavení získat přístup k určitým členům.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Využití  
 V těchto kontextech můžete použít modifikátor `Friend`:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
