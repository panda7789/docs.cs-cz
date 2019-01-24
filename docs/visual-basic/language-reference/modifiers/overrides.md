---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: dbcd0625cdbcd06affc495ca29972c6c183c10f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582093"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
Určuje, že se vlastnost nebo procedura přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>pravidla  
  
-   **Místní deklarace.** Můžete použít `Overrides` pouze v příkazu deklarace vlastnost nebo procedura.  
  
-   **Kombinované modifikátory.** Nelze zadat `Overrides` spolu s `Shadows` nebo `Shared` ve stejné deklaraci. Vzhledem k tomu, že element přepsání přepsatelné, nelze kombinovat `Overridable` s `Overrides`.  
  
-   **Odpovídající podpisy.** Signatura této deklarace musí přesně odpovídat *podpis* vlastnost nebo proceduru, která přepíše. To znamená, že v seznamu parametrů musí mít stejný počet parametrů, ve stejném pořadí, se stejnými typy dat.  
  
     Kromě podpis přepsání deklarace musí také přesně odpovídat následující:  
  
    -   Úroveň přístupu  
  
    -   Návratový typ, pokud existuje  
  
-   **Generických signatur.** Obecný postup je popsán podpis obsahuje počet parametrů typu. Proto přepsání deklarace musí odpovídat verzi základní třídy v tomto ohledu také.  
  
-   **Další shodu.** Kromě vzorů podpis verze základní třídy, tato deklarace se taky musí shodovat se v těchto ohledech:  
  
    -   Modifikátor úroveň přístupu (například [veřejné](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Předání mechanismus každého parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Omezení jsou uvedeny na jednotlivé parametry typu obecné procedury  
  
-   **Stínováním a přepsáním.** Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy. Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.  
  
 `Overrides` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
