---
title: Úrovně dostupnosti – C# referenční informace
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602384"
---
# <a name="accessibility-levels-c-reference"></a>Úrovně přístupnosti (Referenční dokumentace jazyka C#)

K určení jedné z následujících deklarovaných `protected`úrovní dostupnosti pro `private`členy použijte modifikátory `public` `internal`přístupu,,, nebo.  
  
|Deklarovaná přístupnost|Význam|  
|----------------------------|-------------|  
|[`public`](public.md)|Přístup není omezen.|  
|[`protected`](protected.md)|Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy.|  
|[`internal`](internal.md)|Přístup je omezen na aktuální sestavení.|  
|[`protected internal`](protected-internal.md)|Přístup je omezen na aktuální sestavení nebo typy odvozené z nadřazené třídy.|  
|[`private`](private.md)|Přístup je omezen na nadřazený typ.|  
|[`private protected`](private-protected.md)|Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy v rámci aktuálního sestavení. K dispozici od C# verze 7,2. |  
  
 Pro člena nebo typ je povolen pouze jeden modifikátor přístupu, s výjimkou použití `protected internal` kombinací nebo. `private protected`  
  
 Modifikátory přístupu nejsou povolené pro obory názvů. Obory názvů nemají žádná omezení přístupu.  
  
 V závislosti na kontextu, ve kterém je vyvolána deklarace členů, jsou povoleny pouze určité deklarované přístupnosti. Pokud v deklaraci členu není zadaný žádný modifikátor přístupu, použije se výchozí přístupnost.  
  
 Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, mohou mít `internal` pouze nebo `public` přístupnost. Výchozí přístupnost pro tyto typy je `internal`.  
  
 Vnořené typy, které jsou členy jiných typů, mohou mít deklarované přístupnosti, jak je uvedeno v následující tabulce.  
  
|Členové|Přístupnost výchozího člena|Povolená deklarovaná přístupnost člena|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Žádné|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Žádné|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Přístupnost vnořeného typu závisí na své [doméně](./accessibility-domain.md)přístupnosti, která je určena deklarovanou přístupností člena a doménou přístupnosti bezprostředně obsahujícího typu. Nicméně doména přístupnosti vnořeného typu nemůže přesáhnout typ nadřazeného typu.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Doména přístupnosti](./accessibility-domain.md)
- [Omezení používání úrovní přístupu](./restrictions-on-using-accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
