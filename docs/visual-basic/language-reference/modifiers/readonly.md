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
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965424"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Určuje, že proměnnou nebo vlastnost lze číst, ale nikoli zapsat.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidly  
  
- **Kontext deklarace** Můžete použít `ReadOnly` pouze na úrovni modulu. To znamená, že kontext deklarace pro `ReadOnly` prvek musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.  
  
- **Kombinované modifikátory.** Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.  
  
- **Přiřazení hodnoty.** Kód, který `ReadOnly` spotřebovává vlastnost, nemůže nastavit jeho hodnotu. Kód, který má přístup k základnímu úložišti, ale může hodnotu kdykoli přiřadit nebo změnit.  
  
     Můžete přiřadit hodnotu `ReadOnly` proměnné pouze v deklaraci nebo v konstruktoru třídy nebo struktury, ve které je definována.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kdy použít proměnnou jen pro čtení  
 Existují situace, kdy nelze použít [příkaz const](../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty. Například `Const` příkaz nemusí přijmout datový typ, který chcete přiřadit, nebo možná nebudete moci vypočítat hodnotu v době kompilace pomocí konstantního výrazu. Nemusíte ani znát hodnotu v době kompilace. V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnoty.  
  
> [!IMPORTANT]
> Pokud je datovým typem proměnné odkazový typ, jako je například pole nebo instance třídy, mohou být jeho členové změněny i v případě, že je `ReadOnly`proměnná sama. Toto dokládá následující příklad.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Při inicializaci pole, na `characterArray()` které ukazuje, obsahuje "x", "y" a "z". Vzhledem k tomu `characterArray` , `ReadOnly`že proměnná je, nelze po inicializaci změnit její hodnotu; to znamená, že k ní nelze přiřadit nové pole. Můžete však změnit hodnoty jednoho nebo více členů pole. Po volání procedury `changeArrayElement`se pole, `characterArray()` na které se odkazuje, drží "x", "M" a "z".  
  
 Všimněte si, že je to podobné jako deklarace parametru procedury pro [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což brání postupu v změně samotného argumentu volání, ale umožňuje změnit jeho členy.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `ReadOnly` vlastnost pro datum, kdy byl zaměstnanec přijat. Třída ukládá hodnotu vlastnosti interně jako `Private` proměnnou a pouze kód uvnitř třídy může tuto hodnotu změnit. Vlastnost je `Public`však a jakýkoli kód, který má přístup ke třídě, může číst vlastnost.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 V těchto kontextech lze použít Modifikátor:`ReadOnly`  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
