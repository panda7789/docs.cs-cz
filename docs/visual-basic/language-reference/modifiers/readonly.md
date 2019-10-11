---
title: Jen pro čtení (Visual Basic)
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
ms.openlocfilehash: 748c38835cec83cefe54535f90d40ec3a030e4f4
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250381"
---
# <a name="readonly-visual-basic"></a>Jen pro čtení (Visual Basic)
Určuje, že proměnnou nebo vlastnost lze číst, ale nikoli zapsat.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** @No__t-0 můžete použít pouze na úrovni modulu. To znamená, že kontext deklarace pro prvek `ReadOnly` musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.  
  
- **Kombinované modifikátory.** Nelze zadat `ReadOnly` spolu s `Static` ve stejné deklaraci.  
  
- **Přiřazení hodnoty.** Kód, který spotřebovává vlastnost `ReadOnly`, nemůže nastavit jeho hodnotu. Kód, který má přístup k základnímu úložišti, ale může hodnotu kdykoli přiřadit nebo změnit.  
  
     Můžete přiřadit hodnotu proměnné `ReadOnly` pouze v deklaraci nebo v konstruktoru třídy nebo struktury, ve které je definována.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kdy použít proměnnou jen pro čtení  
 Existují situace, kdy nelze použít [příkaz const](../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty. Například příkaz `Const` nemusí akceptovat datový typ, který chcete přiřadit, nebo je možné, že nebudete moci vypočítat hodnotu v době kompilace pomocí konstantního výrazu. Nemusíte ani znát hodnotu v době kompilace. V těchto případech můžete použít proměnnou `ReadOnly` pro uchování konstantní hodnoty.  
  
> [!IMPORTANT]
> Pokud je datovým typem proměnné odkazový typ, jako je například pole nebo instance třídy, mohou být jeho členové změněny i v případě, že je proměnná sama `ReadOnly`. Následující příklad znázorňuje toto.  
  
 ```vb
 ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
 Sub ChangeArrayElement()
     characterArray(1) = "M"c
 End Sub
 ```
  
 Při inicializaci obsahuje pole, na které ukazuje `characterArray()`, "x", "y" a "z". Vzhledem k tomu, že proměnná `characterArray` je `ReadOnly`, po inicializaci již nelze změnit její hodnotu; To znamená, že k němu nemůžete přiřadit nové pole. Můžete však změnit hodnoty jednoho nebo více členů pole. Po volání procedury `ChangeArrayElement`, pole, na které ukazuje `characterArray()`, obsahuje "x", "M" a "z".
  
 Všimněte si, že je to podobné jako deklarace parametru procedury pro [ByVal](byval.md), což brání postupu v změně samotného argumentu volání, ale umožňuje změnit jeho členy.  
  
## <a name="example"></a>Příklad

Následující příklad definuje vlastnost @no__t 0 pro datum, kdy byl zaměstnanec přijat. Třída ukládá hodnotu vlastnosti interně jako proměnnou `Private` a tato hodnota může změnit pouze kód uvnitř třídy. Vlastnost však je `Public` a jakýkoli kód, který má přístup ke třídě, může číst vlastnost.
  
[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]
  
V těchto kontextech lze použít modifikátor `ReadOnly`:
  
- [Dim – příkaz](../statements/dim-statement.md) 
- [Property – příkaz](../statements/property-statement.md)  
  
## <a name="see-also"></a>Související témata

- [WriteOnly](writeonly.md)
- [Klíčov](../keywords/index.md)
