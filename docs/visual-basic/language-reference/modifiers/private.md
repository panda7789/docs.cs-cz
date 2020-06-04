---
title: Soukromé
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 524f03e77e075bef08a1b41b563985de41baacb6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404807"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci svého kontextu deklarace, včetně v rámci libovolných obsažených typů.  
  
## <a name="remarks"></a>Poznámky  
 Pokud programovací element představuje proprietární funkce nebo obsahuje důvěrné údaje, obvykle chcete omezit přístup k němu, co je to možné. Dosáhnete maximálního omezení tím, že povolíte pouze modul, třídu nebo strukturu, které ji definují k přístupu. Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Private` .  

> [!NOTE]
> Můžete také použít modifikátor [privátního chráněného](private-protected.md) přístupu, který zpřístupňuje člena v rámci této třídy a z odvozených tříd umístěných v jeho obsahujícím sestavení.

## <a name="rules"></a>Pravidla  

- **Kontext deklarace** Můžete použít `Private` pouze na úrovni modulu. To znamená, že kontext deklarace pro `Private` prvek musí být modul, třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní nebo proceduru.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód v kontextu deklarace má přístup k jeho `Private` prvkům. To zahrnuje kód v rámci obsaženého typu, jako je vnořená třída nebo výraz přiřazení ve výčtu. Žádný kód mimo kontext deklarace má přístup k jeho `Private` prvkům.  
  
- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private`V těchto kontextech lze použít modifikátor:  
  
 [Class – příkaz](../statements/class-statement.md)  
  
 [Const – příkaz](../statements/const-statement.md)  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
 [Delegate – příkaz](../statements/delegate-statement.md)  
  
 [Dim – příkaz](../statements/dim-statement.md)  
  
 [Enum – příkaz](../statements/enum-statement.md)  
  
 [Event – příkaz](../statements/event-statement.md)  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Interface – příkaz](../statements/interface-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Structure – příkaz](../statements/structure-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Republik](public.md)
- [Proti](protected.md)
- [Friend](friend.md)
- [Soukromé chráněné](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
