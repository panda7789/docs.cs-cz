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
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599909"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Určuje, že proměnné nebo vlastnosti lze číst, ale nebyl zapsán.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `ReadOnly` jenom na úrovni modulu. To znamená kontext deklarace `ReadOnly` element musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů nebo postupu.  
  
-   **Kombinovaná parametrů.** Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.  
  
-   **Přiřazení hodnoty.** Použití kódu `ReadOnly` vlastnost nelze nastavit jeho hodnotu. Ale kód, který má přístup k podkladové úložiště přiřadit, nebo změňte hodnotu kdykoli.  
  
     Můžete přiřadit hodnotu na `ReadOnly` proměnné pouze v jeho deklaraci nebo v konstruktoru třídu nebo strukturu, ve kterém je definovaný.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kdy použít proměnnou jen pro čtení  
 Existují situace, ve kterých se nedá použít [příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md) deklarovat a přiřadit konstantní hodnotu. Například `Const` příkaz nemusí přijmout datový typ chcete přiřadit, nebo není možné k výpočtu hodnoty v době kompilace s konstantní výraz. Hodnota nemusí vědět i v době kompilace. V těchto případech můžete použít `ReadOnly` proměnnou pro uložení konstantní hodnotu.  
  
> [!IMPORTANT]
>  Pokud datový typ proměnné je odkazového typu, jako je například pole nebo instance třídy, i když je proměnná samotné lze změnit její členy `ReadOnly`. Toto dokládá následující příklad.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Při inicializaci, pole na kterou odkazuje `characterArray()` blokování "x", "y" a "z". Protože proměnnou `characterArray` je `ReadOnly`, jeho hodnotu nelze změnit po inicializaci; je, není možné přiřadit nové pole. Můžete však změnit hodnoty jednoho nebo více členů pole. Po výzvě k postupu `changeArrayElement`, pole na kterou odkazuje `characterArray()` blokování "x", "M" a "z".  
  
 Tento název se podobně jako deklarace parametru procedury být [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což zabraňuje měnit volání samotného argumentu postup, ale umožní změnit její členy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje `ReadOnly` vlastnost pro datum přijetí zaměstnance. Třída úložiště vlastnost hodnota interně jako `Private` kód proměnnou a to pouze uvnitř třídy můžete změnit tuto hodnotu. Je však vlastnost `Public`, a kód, který může přistupovat k třídě může číst vlastnosti.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 `ReadOnly` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
