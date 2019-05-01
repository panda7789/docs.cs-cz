---
title: ReadOnly (Visual Basic)
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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051855"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Určuje, že proměnné nebo vlastnosti lze číst, ale není zapsána.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `ReadOnly` pouze na úrovni modulu. To znamená, že deklarace kontext `ReadOnly` elementu musí být třída, struktura nebo modulu a nemůže být zdrojový soubor, obor názvů nebo proceduru.  
  
- **Kombinované modifikátory.** Nelze zadat `ReadOnly` spolu s `Static` ve stejné deklaraci.  
  
- **Přiřazení hodnoty.** Použití kódu `ReadOnly` jeho hodnotu nelze nastavit vlastnost. Ale kód, který má přístup k podkladové úložiště můžete přiřadit nebo změňte hodnotu v každém okamžiku.  
  
     Můžete přiřadit hodnoty k `ReadOnly` proměnné pouze v jeho deklaraci nebo v konstruktoru třídy nebo struktury, ve kterém je definována.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kdy použít proměnnou jen pro čtení  
 Existují situace, ve kterých nelze použít [Const příkaz](../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnotu. Například `Const` příkaz nemusí přijmout typ dat, kterou chcete přiřadit, nebo nemusí být schopný vypočítat hodnotu v době kompilace konstantní výraz. Hodnota nemusí vědět i v době kompilace. V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnotu.  
  
> [!IMPORTANT]
>  Pokud je datový typ proměnné typu odkazu, například pole nebo instanci třídy, jejích členů lze změnit i v případě, že je proměnná samotného `ReadOnly`. Toto dokládá následující příklad.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Při inicializaci pole odkazované `characterArray()` blokování "x", "y" a "z". Protože proměnné `characterArray` je `ReadOnly`, jeho hodnotu nelze změnit po inicializaci; který je, není možné přiřadit nové pole. Však můžete změnit hodnoty jedné nebo více členů pole. Následující volání do procedury `changeArrayElement`, pole odkazované `characterArray()` blokování "x", "M" a "z".  
  
 Všimněte si, že je podobná deklaraci parametru postupu bude [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což zabrání změně samotného argumentu volajícího procesu, ale umožňuje měnit její členy.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `ReadOnly` vlastnost pro datum přijetí zaměstnance. Vlastnost hodnota interně jako třídy úložiště `Private` tuto hodnotu můžete změnit proměnné a to pouze kód uvnitř třídy. Vlastnost je však `Public`, a vlastnost může přečíst jakýkoli kód, který může přistupovat k třídě.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
