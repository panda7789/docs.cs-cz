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
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415346"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádná omezení přístupu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud publikujete součást nebo sadu komponent, jako je například knihovna tříd, obvykle chcete, aby byly k dispozici programové prvky pro jakýkoliv kód, který spolupracuje s vaším sestavením. Chcete-li udělit takovému neomezenému přístupu u prvku, můžete ho deklarovat pomocí `Public` .  
  
 Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu. Všimněte si, že úroveň přístupu elementu deklarovaného v rámci výchozího rozhraní, modulu, třídy nebo struktury je v `Public` případě, že jej nedeklarujete jinak.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že kontext deklarace pro `Public` prvek musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura a nemůže být procedura.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód, který má přístup k modulu, třídě nebo struktuře, má přístup k jeho `Public` prvkům.  
  
- **Výchozí přístup** Místní proměnné uvnitř procedury jsou ve výchozím nastavení veřejný přístup a nemůžete použít žádné modifikátory přístupu.  
  
- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public`V těchto kontextech lze použít modifikátor:  
  
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
  
 [Operator – příkaz](../statements/operator-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Structure – příkaz](../statements/structure-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Proti](protected.md)
- [Friend](friend.md)
- [Hlášen](private.md)
- [Soukromé chráněné](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
