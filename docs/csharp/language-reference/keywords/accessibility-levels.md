---
title: Úrovně usnadnění přístupu – odkaz jazyka C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713820"
---
# <a name="accessibility-levels-c-reference"></a>Úrovně přístupnosti (Referenční dokumentace jazyka C#)

Pomocí modifikátorů `public` `protected`přístupu , , `internal`, nebo `private`, určete jednu z následujících deklarovaných úrovní přístupnosti pro členy.  
  
|Deklarovaná přístupnost|Význam|  
|----------------------------|-------------|  
|[`public`](public.md)|Přístup není omezen.|  
|[`protected`](protected.md)|Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy.|  
|[`internal`](internal.md)|Přístup je omezen na aktuální sestavení.|  
|[`protected internal`](protected-internal.md)|Přístup je omezen na aktuální sestavení nebo typy odvozené z obsahující třídy.|  
|[`private`](private.md)|Přístup je omezen na obsahující typ.|  
|[`private protected`](private-protected.md)|Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy v rámci aktuálního sestavení. K dispozici od C# 7.2. |  
  
 Pro člena nebo typ je povolen pouze jeden modifikátor přístupu, `protected internal` s výjimkou použití kombinace nebo. `private protected`  
  
 Modifikátory přístupu nejsou v oborech názvů povoleny. Obory názvů nemají žádná omezení přístupu.  
  
 V závislosti na kontextu, ve kterém dojde k deklaraci člena, jsou povoleny pouze určité deklarované přístupnosti. Pokud v deklaraci člena není zadán žádný modifikátor přístupu, použije se výchozí usnadnění přístupu.  
  
 Typy nejvyšší úrovně, které nejsou vnořené v `internal` `public` jiných typech, mohou mít pouze nebo usnadnění přístupu. Výchozí usnadnění přístupu `internal`pro tyto typy je .  
  
 Vnořené typy, které jsou členy jiných typů, mohou deklarovat přístupnosti, jak je uvedeno v následující tabulce.  
  
|Členové|Výchozí usnadnění přístupu členů|Povolená deklarovaná přístupnost člena|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Žádný|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Žádný|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Usnadnění vnořeného typu závisí na [jeho doméně usnadnění přístupu](./accessibility-domain.md), která je určena deklarovanou přístupností člena i doménou usnadnění typu bezprostředně obsahujícího. Doména usnadnění vnořeného typu však nesmí překročit doménu obsahujícího typu.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Doména přístupnosti](./accessibility-domain.md)
- [Omezení používání úrovní přístupu](./restrictions-on-using-accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Veřejné](./public.md)
- [Soukromé](./private.md)
- [protected](./protected.md)
- [Vnitřní](./internal.md)
