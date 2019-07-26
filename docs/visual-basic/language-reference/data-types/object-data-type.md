---
title: Datový typ objektu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513052"
---
# <a name="object-data-type"></a>Datový typ objektu

Obsahuje adresy, které odkazují na objekty. `Object` Proměnné můžete přiřadit libovolný typ odkazu (řetězec, pole, třída nebo rozhraní). Proměnná může také odkazovat na data libovolného typu hodnoty ( `Char`číselná, `Boolean` `Date`,,, struktura nebo výčet). `Object`

## <a name="remarks"></a>Poznámky

`Object` Datový typ může ukazovat na data libovolného datového typu, včetně jakékoli instance objektu, kterou vaše aplikace rozpoznává. Použijte `Object` , pokud v době kompilace neznáte, na jaký datový typ proměnné může odkazovat.

Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).

## <a name="data-types"></a>Datové typy

Proměnné, konstanty nebo výrazy libovolného datového typu `Object` můžete přiřadit proměnné. Chcete-li určit datový typ `Object` , na který proměnná aktuálně odkazuje, můžete <xref:System.Type.GetTypeCode%2A> použít metodu <xref:System.Type?displayProperty=nameWithType> třídy. Toto dokládá následující příklad.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object` Datový typ je odkazový typ. Nicméně Visual Basic považuje `Object` proměnnou jako typ hodnoty, když odkazuje na data typu hodnoty.

## <a name="storage"></a>Úložiště

Libovolný datový typ, na který odkazuje, `Object` proměnná neobsahuje datovou hodnotu samotnou, ale spíše ukazatel na hodnotu. Vždycky používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště dat, která představují hodnotu proměnné. Z důvodu kódu, který používá ukazatel k vyhledání dat, jsou proměnné `Object` , které mají typy hodnot, mírně pomalejší pro přístup, než explicitně typované proměnné.

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy ukazatelů v jiných prostředích nejsou kompatibilní s typem Visual Basic `Object` .

- **Výkon.** Proměnná, kterou deklarujete s `Object` typem, je dostatečně flexibilní, aby obsahovala odkaz na libovolný objekt. Nicméně pokud pro takovou proměnnou vyvoláte metodu nebo vlastnost, vždy se vám bude účtovat *pozdní vazba* (za běhu). Chcete-li vynutit *počáteční vazbu* (v době kompilace) a lepší výkon, deklarujte proměnnou pomocí konkrétního názvu třídy nebo ji přetypujte na konkrétní datový typ.

  Pokud deklarujete proměnnou objektu, zkuste použít konkrétní typ třídy, <xref:System.OperatingSystem>například namísto `Object` zobecněného typu. Měli byste také použít nejvíce dostupné třídy, <xref:System.Windows.Forms.TextBox> jako je například <xref:System.Windows.Forms.Control>namísto, abyste měli přístup k jeho vlastnostem a metodám. Můžete obvykle použít seznam **třídy** v **Prohlížeč objektů** k vyhledání dostupných názvů tříd.

- **Rozšiřující.** Všechny datové typy a všechny typy odkazů se rozšíří na `Object` datový typ. To znamená, že můžete převést libovolný typ `Object` na bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.

  Nicméně pokud převedete mezi typy hodnot a `Object`, Visual Basic provádí operace s názvem zabalení a rozbalení, které provádějí zpracování pomaleji.

- **Znaky typu.** `Object`nemá žádný znak typu literálu nebo znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Object?displayProperty=nameWithType> třída.

## <a name="example"></a>Příklad

Následující příklad ukazuje `Object` proměnnou odkazující na instanci objektu.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Viz také:

- <xref:System.Object>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Postupy: Určení, zda dva objekty souvisejí](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda jsou dva objekty identické](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
