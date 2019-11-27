---
title: Datový typ objektu
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
ms.openlocfilehash: 2ccb9b69b865c259d078ed9642d63c7f83514756
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343954"
---
# <a name="object-data-type"></a>Datový typ objektu

Obsahuje adresy, které odkazují na objekty. K proměnné `Object` můžete přiřadit libovolný typ odkazu (řetězec, pole, třída nebo rozhraní). `Object` proměnná může také odkazovat na data libovolného typu hodnoty (číselná, `Boolean`, `Char`, `Date`, Structure nebo Enumeration).

## <a name="remarks"></a>Poznámky

Datový typ `Object` může ukazovat na data libovolného datového typu, včetně jakékoli instance objektu, kterou vaše aplikace rozpoznává. Použijte `Object`, když v době kompilace neznáte, na jaký datový typ proměnné může odkazovat.

Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).

## <a name="data-types"></a>Datové typy

Proměnné, konstanty nebo výrazy libovolného datového typu můžete přiřadit k proměnné `Object`. Chcete-li určit datový typ, `Object` proměnná aktuálně odkazuje na, můžete použít metodu <xref:System.Type.GetTypeCode%2A> třídy <xref:System.Type?displayProperty=nameWithType>. Toto dokládá následující příklad.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object` datový typ je odkazový typ. Nicméně Visual Basic považuje `Object` proměnnou jako typ hodnoty, když odkazuje na data typu hodnoty.

## <a name="storage"></a>Úložiště

Libovolný datový typ, na který odkazuje, `Object` proměnná neobsahuje hodnotu dat, ale spíše ukazatel na hodnotu. Vždycky používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště dat, která představují hodnotu proměnné. Z důvodu kódu, který používá ukazatel k vyhledání dat, `Object` proměnné, které mají typy hodnot, jsou mírně pomalejší pro přístup než explicitně typované proměnné.

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy ukazatelů v jiných prostředích nejsou kompatibilní s typem `Object` Visual Basic.

- **Předepsané.** Proměnná, kterou deklarujete s typem `Object`, je dostatečně flexibilní, aby obsahovala odkaz na libovolný objekt. Nicméně pokud pro takovou proměnnou vyvoláte metodu nebo vlastnost, vždy se vám bude účtovat *pozdní vazba* (za běhu). Chcete-li vynutit *počáteční vazbu* (v době kompilace) a lepší výkon, deklarujte proměnnou pomocí konkrétního názvu třídy nebo ji přetypujte na konkrétní datový typ.

  Pokud deklarujete proměnnou objektu, zkuste použít konkrétní typ třídy, například <xref:System.OperatingSystem>namísto zobecněného typu `Object`. Měli byste také použít nejvíce dostupné třídy, například <xref:System.Windows.Forms.TextBox> místo <xref:System.Windows.Forms.Control>, abyste měli přístup k jeho vlastnostem a metodám. Můžete obvykle použít seznam **třídy** v **Prohlížeč objektů** k vyhledání dostupných názvů tříd.

- **Rozšiřující.** Všechny datové typy a všechny typy odkazů se rozšíří na `Object` datový typ. To znamená, že můžete převést libovolný typ na `Object` bez výskytu chyby <xref:System.OverflowException?displayProperty=nameWithType>.

  Nicméně pokud převedete mezi typy hodnot a `Object`, Visual Basic provádí operace s názvem *zabalení* a *rozbalení*, které provádějí zpracování pomaleji.

- **Znaky typu.** `Object` nemá žádný znak typu literálu ani znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je třída <xref:System.Object?displayProperty=nameWithType>.

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
- [Postupy: Určení, zda dva objekty spolu souvisí](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
