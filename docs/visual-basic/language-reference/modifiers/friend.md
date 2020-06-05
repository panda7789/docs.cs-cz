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
ms.openlocfilehash: 4ac8e5942cf6097642ec111992ebfcdb91e8d7c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392168"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci sestavení, které obsahuje jejich deklaraci.  
  
## <a name="remarks"></a>Poznámky  
 V mnoha případech požadujete, aby byly programovací prvky, jako jsou třídy a struktury, použity celým sestavením, nikoli pouze komponentou, která je deklaruje. Je však možné, že nechcete, aby byly přístupné pomocí kódu mimo sestavení (například pokud je aplikace proprietární). Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Friend` modifikátoru.  
  
 Kód v jiných třídách, strukturách a modulech, které jsou zkompilovány do stejného sestavení, mají přístup ke všem `Friend` prvkům v tomto sestavení.  
  
 `Friend`přístup je často upřednostňovanou úrovní pro programovací prvky aplikace a `Friend` je výchozí úrovní přístupu rozhraní, modulu, třídy nebo struktury.  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo oboru názvů. Proto kontext deklarace pro `Friend` prvek musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura. nemůže to být procedura.  

> [!NOTE]
> Můžete použít také modifikátor [Protected Friend](protected-friend.md) Access, který zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná. Chcete-li omezit přístup ke členovi z jeho třídy a z odvozených tříd ve stejném sestavení, použijte modifikátor [privátního chráněného](private-protected.md) přístupu.

 Porovnání `Friend` a ostatní modifikátory přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Můžete určit, že jiné sestavení je sestavení typu Friend, které umožňuje přístup ke všem typům a členům, které jsou označeny jako `Friend` . Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).

## <a name="example"></a>Příklad  
 Následující třída používá `Friend` Modifikátor k povolení přístupu k určitým členům jiným programovacím prvkům v rámci stejného sestavení.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Využití  
 `Friend`V těchto kontextech můžete použít modifikátor:  
  
 [Class – příkaz](../statements/class-statement.md)  
  
 [Const – příkaz](../statements/const-statement.md)  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
 [Delegate – příkaz](../statements/delegate-statement.md)  
  
 [Dim – příkaz](../statements/dim-statement.md)  
  
 [Enum – příkaz](../statements/enum-statement.md)  
  
 [Event – příkaz](../statements/event-statement.md)  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Interface – příkaz](../statements/interface-statement.md)  
  
 [Module – příkaz](../statements/module-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Structure – příkaz](../statements/structure-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Republik](public.md)
- [Proti](protected.md)
- [Hlášen](private.md)
- [Soukromé chráněné](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
