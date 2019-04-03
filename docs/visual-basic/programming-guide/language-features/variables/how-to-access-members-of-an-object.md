---
title: 'Postupy: Přístup k členům v objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2b7e600a23ed326fe3e914957b4e698bc34c6135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819645"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Postupy: Přístup k členům v objektu (Visual Basic)
Až budete mít proměnné objektu, který odkazuje na objekt, často chcete pracovat s členy tohoto objektu, jako jsou metody, vlastnosti, pole a události. Například po vytvoření nového <xref:System.Windows.Forms.Form> objektu, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastností nebo volání jeho <xref:System.Windows.Forms.Control.Focus%2A> metoda.  
  
## <a name="accessing-members"></a>Přístup ke členům  
 Získáte přístup k členům objektu prostřednictvím proměnné, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object"></a>Pro přístup ke členům objektu  
  
-   Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Pokud je člen [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), není nutné proměnnou, která k němu přístup.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Přístup ke členům objektu známého typu  
 Pokud víte, typ objektu v době kompilace, můžete použít *časné vazby* pro proměnnou, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro kterou znáte typ v době kompilace  
  
1.  Deklarace proměnné objektu typu objektu, který máte v úmyslu přiřadit k proměnné.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     S `Option Strict On`, můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozeného z <xref:System.Windows.Forms.Form>) k `extraForm`. Pokud jste definovali třídy nebo struktury se rozšiřující `CType` převod na <xref:System.Windows.Forms.Form>, můžete také přiřadit dané třídy nebo struktury na `extraForm`.  
  
2.  Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Všechny metody a vlastnosti specifické pro dostanete <xref:System.Windows.Forms.Form> třídy, bez ohledu na to, co `Option Strict` nastavení je.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Přístup ke členům objekt neznámého typu.  
 Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazby* pro jakoukoli proměnnou, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pro přístup ke členům objektu, pro kterou neznáte typ v době kompilace  
  
1.  Deklarace proměnné objektu bude [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Deklarace proměnné jako `Object` je stejné jako deklarování jako <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     S `Option Strict On`, dostanete pouze členy, které jsou definovány na <xref:System.Object> třídy.  
  
2.  Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Aby bylo možné pro přístup ke členům libovolný objekt přiřadit k proměnné, je nutné nastavit `Option Strict Off`. Když toto provedete, kompilátor nemůže zaručit, že je daný člen je zveřejněný prostřednictvím objektu, který je přiřadit k proměnné. Pokud objekt nevystavuje člen pokus o přístup, <xref:System.MemberAccessException> dojde k výjimce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
