---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351297"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádná omezení přístupu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud publikujete součást nebo sadu komponent, jako je například knihovna tříd, obvykle chcete, aby byly k dispozici programové prvky pro jakýkoliv kód, který spolupracuje s vaším sestavením. Chcete-li udělit takovému neomezenému přístupu u prvku, můžete ho deklarovat pomocí `Public`.  
  
 Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu. Všimněte si, že úroveň přístupu elementu deklarovaného v rámci rozhraní, modulu, třídy nebo struktury se standardně `Public`, pokud jej nedeklarujete jinak.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** `Public` lze použít pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že kontext deklarace pro prvek `Public` musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura a nemůže být procedura.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód, který má přístup k modulu, třídě nebo struktuře, má přístup k jeho prvkům `Public`.  
  
- **Výchozí přístup** Místní proměnné uvnitř procedury jsou ve výchozím nastavení veřejný přístup a nemůžete použít žádné modifikátory přístupu.  
  
- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 V těchto kontextech lze použít modifikátor `Public`:  
  
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
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
