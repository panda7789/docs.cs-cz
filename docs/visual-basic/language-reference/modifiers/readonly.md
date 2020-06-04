---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 405297a25d4b948a6920bd989c7826e8b6f66bb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398204"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Určuje, že proměnnou nebo vlastnost lze číst, ale nikoli zapsat.

## <a name="remarks"></a>Poznámky

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `ReadOnly` pouze na úrovni modulu. To znamená, že kontext deklarace pro `ReadOnly` prvek musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.

- **Kombinované modifikátory.** Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.

- **Přiřazení hodnoty.** Kód, který spotřebovává `ReadOnly` vlastnost, nemůže nastavit jeho hodnotu. Kód, který má přístup k základnímu úložišti, ale může hodnotu kdykoli přiřadit nebo změnit.

     Můžete přiřadit hodnotu `ReadOnly` proměnné pouze v deklaraci nebo v konstruktoru třídy nebo struktury, ve které je definována.

## <a name="when-to-use-a-readonly-variable"></a>Kdy použít proměnnou jen pro čtení

Existují situace, kdy nelze použít [příkaz const](../statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty. Například `Const` příkaz nemusí přijmout datový typ, který chcete přiřadit, nebo možná nebudete moci vypočítat hodnotu v době kompilace pomocí konstantního výrazu. Nemusíte ani znát hodnotu v době kompilace. V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnoty.

> [!IMPORTANT]
> Pokud je datovým typem proměnné odkazový typ, jako je například pole nebo instance třídy, mohou být jeho členové změněny i v případě, že je proměnná sama `ReadOnly` . Toto dokládá následující příklad.

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

Při inicializaci pole, na které ukazuje, `characterArray()` obsahuje "x", "y" a "z". Vzhledem k tomu `characterArray` , že proměnná je `ReadOnly` , nelze po inicializaci změnit její hodnotu; to znamená, že k ní nelze přiřadit nové pole. Můžete však změnit hodnoty jednoho nebo více členů pole. Po volání procedury se pole, na které se odkazuje, `ChangeArrayElement` `characterArray()` drží "x", "M" a "z".

Všimněte si, že je to podobné jako deklarace parametru procedury pro [ByVal](byval.md), což brání postupu v změně samotného argumentu volání, ale umožňuje změnit jeho členy.

## <a name="example"></a>Příklad

Následující příklad definuje `ReadOnly` vlastnost pro datum, kdy byl zaměstnanec přijat. Třída ukládá hodnotu vlastnosti interně jako `Private` proměnnou a pouze kód uvnitř třídy může tuto hodnotu změnit. Vlastnost je však `Public` a jakýkoli kód, který má přístup ke třídě, může číst vlastnost.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly`V těchto kontextech lze použít modifikátor:

- [Dim – příkaz](../statements/dim-statement.md)
- [Property – příkaz](../statements/property-statement.md)

## <a name="see-also"></a>Viz také

- [WriteOnly](writeonly.md)
- [Klíčová slova](../keywords/index.md)
