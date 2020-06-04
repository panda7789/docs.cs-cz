---
title: 'Postupy: Přístup ke členům v objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410539"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Postupy: Přístup ke členům v objektu (Visual Basic)

Máte-li objektovou proměnnou, která odkazuje na objekt, často chcete pracovat s členy tohoto objektu, například jeho metodami, vlastnostmi, poli a událostmi. Například Jakmile vytvoříte nový <xref:System.Windows.Forms.Form> objekt, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost nebo zavolat její <xref:System.Windows.Forms.Control.Focus%2A> metodu.

## <a name="accessing-members"></a>Přístup ke členům

Přistupujete k členům objektu přes proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object"></a>Přístup ke členům objektu

- Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.

    ```vb
    currentText = newForm.Text
    ```

    Pokud je člen [sdílen](../../../language-reference/modifiers/shared.md), nepotřebujete k přístupu k němu proměnnou.

## <a name="accessing-members-of-an-object-of-known-type"></a>Přístup ke členům objektu známého typu

Pokud znáte typ objektu v době kompilace, můžete použít *počáteční vazbu* pro proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro který znáte typ v době kompilace

1. Deklarujte proměnnou objektu pro typ objektu, který chcete přiřadit proměnné.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    Pomocí `Option Strict On` můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozené z <xref:System.Windows.Forms.Form> ) k `extraForm` . Pokud jste definovali třídu nebo strukturu s rozšiřujícím `CType` převodem na <xref:System.Windows.Forms.Form> , můžete tuto třídu nebo strukturu přiřadit také k `extraForm` .

2. Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.

    ```vb
    extraForm.Show()
    ```

    Ke všem metodám a vlastnostem, které jsou specifické pro <xref:System.Windows.Forms.Form> třídu, můžete přistupovat bez ohledu na to, co `Option Strict` je nastavení.

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Přístup ke členům objektu neznámého typu

Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazbu* pro libovolnou proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro který neznáte typ v době kompilace.

1. Deklarujte proměnnou objektu pro [datový typ objektu](../../../language-reference/data-types/object-data-type.md). (Deklarace proměnné tak, jak `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType> .)

    ```vb
    Dim someControl As Object
    ```

    Pomocí nástroje máte `Option Strict On` přístup pouze k členům, které jsou definovány ve <xref:System.Object> třídě.

2. Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.

    ```vb
    someControl.GetType()
    ```

    Aby bylo možné přistupovat ke členům libovolného objektu, který přiřadíte proměnné objektu, je nutné nastavit `Option Strict Off` . Pokud to uděláte, kompilátor nemůže zaručit, že daný člen je zveřejněn objektem, který přiřadíte proměnné. Pokud objekt nezveřejňuje člena, ke kterému se pokoušíte získat přístup, <xref:System.MemberAccessException> dojde k výjimce.

## <a name="see-also"></a>Viz také

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Proměnné objektu](object-variables.md)
- [Deklarace proměnné objektu](object-variable-declaration.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
