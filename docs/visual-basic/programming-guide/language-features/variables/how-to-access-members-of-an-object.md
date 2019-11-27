---
title: 'Postupy: Přístup ke členům v objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348671"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Postupy: Přístup ke členům v objektu (Visual Basic)

Máte-li objektovou proměnnou, která odkazuje na objekt, často chcete pracovat s členy tohoto objektu, například jeho metodami, vlastnostmi, poli a událostmi. Například po vytvoření nového objektu <xref:System.Windows.Forms.Form> můžete chtít nastavit jeho vlastnost <xref:System.Windows.Forms.Control.Text%2A> nebo volat jeho metodu <xref:System.Windows.Forms.Control.Focus%2A>.

## <a name="accessing-members"></a>Přístup ke členům

Přistupujete k členům objektu přes proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object"></a>Přístup ke členům objektu

- Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.

    ```vb
    currentText = newForm.Text
    ```

    Pokud je člen [sdílen](../../../../visual-basic/language-reference/modifiers/shared.md), nepotřebujete k přístupu k němu proměnnou.

## <a name="accessing-members-of-an-object-of-known-type"></a>Přístup ke členům objektu známého typu

Pokud znáte typ objektu v době kompilace, můžete použít *počáteční vazbu* pro proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro který znáte typ v době kompilace

1. Deklarujte proměnnou objektu pro typ objektu, který chcete přiřadit proměnné.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    Pomocí `Option Strict On`lze `extraForm`přiřadit pouze objekty <xref:System.Windows.Forms.Form> (nebo objekty typu odvozené z <xref:System.Windows.Forms.Form>). Pokud jste definovali třídu nebo strukturu s rozšiřujícím `CType`m převodem na <xref:System.Windows.Forms.Form>, můžete tuto třídu nebo strukturu přiřadit i `extraForm`.

2. Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.

    ```vb
    extraForm.Show()
    ```

    Ke všem metodám a vlastnostem, které jsou specifické pro třídu <xref:System.Windows.Forms.Form>, můžete přistupovat bez ohledu na to, co nastavení `Option Strict`.

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Přístup ke členům objektu neznámého typu

Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazbu* pro libovolnou proměnnou, která na ni odkazuje.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro který neznáte typ v době kompilace.

1. Deklarujte proměnnou objektu pro [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Deklarace proměnné jako `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType>.)

    ```vb
    Dim someControl As Object
    ```

    V `Option Strict On`máte přístup pouze k členům, které jsou definovány na <xref:System.Object> třídě.

2. Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.

    ```vb
    someControl.GetType()
    ```

    Aby bylo možné přistupovat ke členům libovolného objektu, který přiřadíte proměnné objektu, je nutné nastavit `Option Strict Off`. Pokud to uděláte, kompilátor nemůže zaručit, že daný člen je zveřejněn objektem, který přiřadíte proměnné. Pokud objekt nezveřejňuje člena, ke kterému se pokoušíte získat přístup, dojde k výjimce <xref:System.MemberAccessException>.

## <a name="see-also"></a>Viz také:

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
