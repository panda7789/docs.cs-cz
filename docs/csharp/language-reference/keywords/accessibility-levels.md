---
title: Úrovně přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 085e99dd96074bd0f5bfe9d26d4364033f442404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216688"
---
# <a name="accessibility-levels-c-reference"></a>Úrovně přístupnosti (Referenční dokumentace jazyka C#)

Modifikátory přístupu pomocí `public`, `protected`, `internal`, nebo `private`, chcete zadat jednu z následujících úrovní přístupu deklarované pro členy.  
  
|Deklarované usnadnění přístupu|Význam|  
|----------------------------|-------------|  
|[`public`](public.md)|Přístup není s omezeným přístupem.|  
|[`protected`](protected.md)|Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.|  
|[`internal`](internal.md)|Přístup je omezen na aktuální sestavení.|  
|[`protected internal`](protected-internal.md)|Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.|  
|[`private`](private.md)|Přístup je omezen na nadřazeném typu.|  
|[`private protected`](private-protected.md)|Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení. Dostupné od verze jazyka C# 7.2. |  
  
 Modifikátor přístupu jenom jeden je povolena pro člena nebo typu, s výjimkou při použití `protected internal` nebo `private protected` kombinace.  
  
 Modifikátory přístupu nejsou povoleny na obory názvů. Obory názvů mít žádná omezení přístupu.  
  
 V závislosti na kontextu, ve kterém dojde k deklarace členů jsou povolené jenom určité deklarované přístupnosti. Pokud žádné – modifikátor přístupu je zadaný v deklaraci člen, použije se výchozí usnadnění.  
  
 Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, může mít pouze `internal` nebo `public` usnadnění. Je výchozí usnadnění pro tyto typy `internal`.  
  
 Vnořené typy, které jsou členy jiné typy, můžete mít deklarovat přístupnosti, které je uvedené v následující tabulce.  
  
|Členové|Výchozí člen pro usnadnění přístupu|Povolené deklarované usnadnění člena|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Žádné|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Žádné|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Usnadnění vnořeného typu závisí na jeho [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md), což je dáno tím deklarované usnadnění člena a doména přístupnosti okamžitě nadřazeného typu. Doména přístupnosti vnořeného typu však nesmí překročit u nadřazeného typu.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
