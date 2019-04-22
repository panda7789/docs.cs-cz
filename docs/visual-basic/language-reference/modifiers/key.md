---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842301"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key` – Klíčové slovo umožňuje zadat chování vlastností anonymních typů. Pouze vlastnosti, kterou určíte jako vlastnosti klíče účasti v testech rovnost mezi anonymního typu instance nebo výpočet hodnoty hash. Nelze změnit hodnoty vlastnosti klíče.  
  
 Vlastnost anonymního typu určíte jako klíčová vlastnost tak, že klíčové slovo `Key` před deklarací ve inicializačního seznamu. V následujícím příkladu `Airline` a `FlightNo` jsou klíčové vlastnosti, ale `Gate` není.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Když se vytvoří nové anonymní typ, dědí přímo z <xref:System.Object>. Kompilátor nahradí tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Přepsání kód, který je vytvořen pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> vychází z klíčové vlastnosti. Pokud nejsou žádné klíčové vlastnosti v typu, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nejsou přepsána.  
  
## <a name="equality"></a>Rovnost  
 Když jsou instance stejného typu, a pokud jsou hodnoty jejich klíče vlastnosti stejné dvě instance anonymního typu jsou si rovny. V následujících příkladech `flight2` rovná `flight1` z předchozího příkladu vzhledem k tomu, že jsou instance anonymní stejného typu a mají odpovídající hodnoty pro jejich vlastnosti klíče. Ale `flight3` není roven `flight1` vzhledem k tomu, že má jinou hodnotu pro klíčovou vlastnost `FlightNo`. Instance `flight4` není stejného typu jako `flight1` vzhledem k tomu, že se určit různé vlastnosti jako vlastnosti klíče.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Pokud není deklarovaný dvě instance s pouze neklíčovým vlastnostmi, identické název, typ, pořadí a hodnoty, nejsou dvě instance stejné. Instance bez klíčové vlastnosti rovná pouze na sebe sama.  
  
 Další informace o podmínkách, za kterých jsou dvě instance anonymního typu instance stejného typu anonymní najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Výpočet hodnoty hash kód  
 Stejně jako <xref:System.Object.Equals%2A>, funkci hash, která je definována v <xref:System.Object.GetHashCode%2A> anonymního typu je založena na klíčové vlastnosti typu. Následující příklady ukazují interakce mezi klíčové vlastnosti a hodnotu hash hodnoty kódu.  
  
 Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče mají stejnou hodnotu hash kód, i v případě, že vlastnosti neklíčovým nemají odpovídající hodnoty. Následující příkaz vrátí `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Instance anonymního typu, které mají různé hodnoty pro jeden nebo více klíčové vlastnosti mají odlišné kódu hodnoty hash. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Instance anonymních typů, které určují různé vlastnosti jako vlastnosti klíče nejsou instance stejného typu. Hodnoty hash různých mají i v případě, že názvy a hodnoty všech vlastností jsou stejné. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Hodnoty jen pro čtení  
 Nelze změnit hodnoty vlastnosti klíče. Například v `flight1` v předchozích příkladech `Airline` a `FlightNo` pole jsou jen pro čtení, ale `Gate` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Definice anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
