---
title: Klíč
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351509"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
Klíčové slovo `Key` umožňuje zadat chování pro vlastnosti anonymních typů. Pouze vlastnosti, které označíte jako klíčové vlastnosti, se účastní testů rovnosti mezi instancemi anonymního typu nebo výpočtů hodnot kódů hash. Hodnoty vlastností klíče nelze změnit.  
  
 Vlastnost anonymního typu určíte tak, že umístíte klíčové slovo `Key` před jeho deklaraci v inicializačním seznamu. V následujícím příkladu jsou `Airline` a `FlightNo` klíčové vlastnosti, ale `Gate` není.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Při vytvoření nového anonymního typu se zdědí přímo z <xref:System.Object>. Kompilátor přepíše tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>a <xref:System.Object.ToString%2A>. Kód přepsání, který je vytvořen pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> je založen na vlastnostech klíče. Pokud typ neobsahuje žádné klíčové vlastnosti, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nejsou přepsány.  
  
## <a name="equality"></a>Rovnost  
 Dvě instance anonymního typu jsou stejné, pokud jsou instance stejného typu a jsou-li hodnoty jejich klíčových vlastností stejné. V následujících příkladech je `flight2` rovno `flight1` z předchozího příkladu, protože jsou instancemi stejného anonymního typu a mají odpovídající hodnoty pro své klíčové vlastnosti. `flight3` se ale nerovná `flight1`, protože má jinou hodnotu pro klíčovou vlastnost `FlightNo`. Instance `flight4` není stejného typu jako `flight1`, protože určují různé vlastnosti jako klíčové vlastnosti.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Pokud jsou deklarovány dvě instance s pouze neklíčovým vlastností, které jsou stejné jako název, typ, pořadí a hodnota, tyto dvě instance se neshodují. Instance bez vlastností klíče je stejná jenom pro sebe sama.  
  
 Další informace o podmínkách, za kterých jsou dvě instance anonymního typu instance stejného anonymního typu, naleznete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Výpočet kódu hash  
 Podobně jako <xref:System.Object.Equals%2A>, funkce hash, která je definována v <xref:System.Object.GetHashCode%2A> anonymního typu, je založena na klíčových vlastnostech typu. Následující příklady znázorňují interakci mezi vlastnostmi klíče a hodnotami hash kódu.  
  
 Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče, mají stejnou hodnotu hash kódu, a to i v případě, že vlastnosti bez klíče nemají odpovídající hodnoty. Následující příkaz vrátí `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Instance anonymního typu, které mají různé hodnoty pro jednu nebo více vlastností klíče, mají jiné hodnoty kódu hash. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Instance anonymních typů, které určují různé vlastnosti jako klíčové vlastnosti, nejsou instancemi stejného typu. Mají různé hodnoty hash kódu, a to i v případě, že jsou názvy a hodnoty všech vlastností stejné. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Hodnoty jen pro čtení  
 Hodnoty vlastností klíče nelze změnit. Například v `flight1` v předchozích příkladech jsou pole `Airline` a `FlightNo` pouze pro čtení, ale `Gate` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Definice anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
