---
title: Úrovně přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 4679fd2564454e7f1ade5cb4813729b65f433012
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484548"
---
# <a name="accessibility-levels-c-reference"></a>Úrovně přístupnosti (Referenční dokumentace jazyka C#)

Používat modifikátory přístupu `public`, `protected`, `internal`, nebo `private`, chcete-li určit jednu z následujících úrovní deklarovaná přístupnost členů.  
  
|Deklarovaná přístupnost|Význam|  
|----------------------------|-------------|  
|[`public`](public.md)|Přístup není omezený.|  
|[`protected`](protected.md)|Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující.|  
|[`internal`](internal.md)|Přístup je omezený na aktuální sestavení.|  
|[`protected internal`](protected-internal.md)|Přístup je omezený na aktuální sestavení nebo typy odvozené od třídy obsahující.|  
|[`private`](private.md)|Přístup je omezený na nadřazeného typu.|  
|[`private protected`](private-protected.md)|Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuálního sestavení. Dostupné od verze C# 7.2. |  
  
 Modifikátor přístupu pouze jeden je povolený pro člen nebo typ, s výjimkou při použití `protected internal` nebo `private protected` kombinace.  
  
 Modifikátory přístupu nejsou povoleny u oborů názvů. Obory názvů nemá žádné omezení přístupu.  
  
 V závislosti na kontextu, ve kterém dochází k deklaraci člena jsou povoleny pouze určité deklarované přístupnosti. Pokud v deklaraci člena není zadán žádný modifikátor přístupu, použije se výchozí dostupnost.  
  
 Nejvyšší úrovně typy, které nejsou vnořené v jiných typech, může mít pouze `internal` nebo `public` usnadnění přístupu. Výchozí dostupnost pro tyto typy je `internal`.  
  
 Vnořené typy, které jsou členy ostatních typů, mohou být deklarovány přístupnosti jak je uvedeno v následující tabulce.  
  
|Členové|Výchozí člen dostupnost|Povolené deklarovaná přístupnost člena|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Žádné|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Žádné|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Přístupnost vnořeného typu závisí na jeho [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md), které je určeno deklarovanou přístupností člena a doménou přístupnosti bezprostředně nadřazeného typu. Doména přístupnosti vnořeného typu však nesmí přesáhnout přístupnost nadřazeného typu.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md)  
- [Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)
