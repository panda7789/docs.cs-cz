---
title: "Úrovně přístupnosti (Referenční dokumentace jazyka C#)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="accessibility-levels-c-reference"></a>Úrovně přístupnosti (Referenční dokumentace jazyka C#)

Použijte modifikátory přístupu [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md), chcete zadat jednu z následujících deklarovaný úrovně přístupnosti pro členy.  
  
|Deklarované usnadnění přístupu|Význam|  
|----------------------------|-------------|  
|`public`|Přístup není s omezeným přístupem.|  
|`protected`|Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.|  
|`internal`|Přístup je omezen na aktuální sestavení.|  
|`protected internal`|Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.|  
|`private`|Přístup je omezen na nadřazeném typu.|  
|`private protected`|Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení. Dostupné od verze jazyka C# 7.2. |  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [veřejné](../../../csharp/language-reference/keywords/public.md)  
 [privátní](../../../csharp/language-reference/keywords/private.md)  
 [chráněný](../../../csharp/language-reference/keywords/protected.md)  
 [interní](../../../csharp/language-reference/keywords/internal.md)
