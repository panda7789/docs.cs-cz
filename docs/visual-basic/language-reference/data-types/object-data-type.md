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
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415580"
---
# <a name="object-data-type"></a>Datový typ objektu

Obsahuje adresy, které odkazují na objekty. Proměnné můžete přiřadit libovolný typ odkazu (řetězec, pole, třída nebo rozhraní) `Object` . `Object`Proměnná může také odkazovat na data libovolného typu hodnoty (číselná,,, `Boolean` `Char` `Date` , struktura nebo výčet).

## <a name="remarks"></a>Poznámky

`Object`Datový typ může ukazovat na data libovolného datového typu, včetně jakékoli instance objektu, kterou vaše aplikace rozpoznává. Použijte, `Object` Pokud v době kompilace neznáte, na jaký datový typ proměnné může odkazovat.

Výchozí hodnota `Object` je `Nothing` (odkaz s hodnotou null).

## <a name="data-types"></a>Typy dat

Proměnné, konstanty nebo výrazy libovolného datového typu můžete přiřadit `Object` proměnné. Chcete-li určit datový typ `Object` , na který proměnná aktuálně odkazuje, můžete použít <xref:System.Type.GetTypeCode%2A> metodu <xref:System.Type?displayProperty=nameWithType> třídy. Toto dokládá následující příklad.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object`Datový typ je odkazový typ. Nicméně Visual Basic považuje `Object` proměnnou jako typ hodnoty, když odkazuje na data typu hodnoty.

## <a name="storage"></a>Storage

Libovolný datový typ, na který odkazuje, `Object` Proměnná neobsahuje datovou hodnotu samotnou, ale spíše ukazatel na hodnotu. Vždycky používá čtyři bajty v paměti počítače, ale nezahrnuje úložiště dat, která představují hodnotu proměnné. Z důvodu kódu, který používá ukazatel k vyhledání dat, jsou proměnné, které mají `Object` typy hodnot, mírně pomalejší pro přístup, než explicitně typované proměnné.

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy ukazatelů v jiných prostředích nejsou kompatibilní s typem Visual Basic `Object` .

- **Předepsané.** Proměnná, kterou deklarujete s `Object` typem, je dostatečně flexibilní, aby obsahovala odkaz na libovolný objekt. Nicméně pokud pro takovou proměnnou vyvoláte metodu nebo vlastnost, vždy se vám bude účtovat *pozdní vazba* (za běhu). Chcete-li vynutit *počáteční vazbu* (v době kompilace) a lepší výkon, deklarujte proměnnou pomocí konkrétního názvu třídy nebo ji přetypujte na konkrétní datový typ.

  Pokud deklarujete proměnnou objektu, zkuste použít konkrétní typ třídy, například <xref:System.OperatingSystem> namísto zobecněného `Object` typu. Měli byste také použít nejvíce dostupné třídy, jako je například <xref:System.Windows.Forms.TextBox> namísto <xref:System.Windows.Forms.Control> , abyste měli přístup k jeho vlastnostem a metodám. Můžete obvykle použít seznam **třídy** v **Prohlížeč objektů** k vyhledání dostupných názvů tříd.

- **Rozšiřující.** Všechny datové typy a všechny typy odkazů se rozšíří na `Object` datový typ. To znamená, že můžete převést libovolný typ na `Object` bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.

  Nicméně pokud převedete mezi typy hodnot a `Object` , Visual Basic provádí operace s názvem *zabalení* a *rozbalení*, které provádějí zpracování pomaleji.

- **Znaky typu.** `Object`nemá žádný znak typu literálu nebo znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Object?displayProperty=nameWithType> Třída.

## <a name="example"></a>Příklad

Následující příklad ukazuje `Object` proměnnou odkazující na instanci objektu.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Viz také

- <xref:System.Object>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Postupy: Určení, zda dva objekty souvisejí.](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Postupy: Určení, zda dva objekty jsou identické](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
