---
title: 'Postupy: Přístup ke členům v objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 62be2955bd1f62fa5af4e54fb0af5e7dca29c421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650917"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Postupy: Přístup ke členům v objektu (Visual Basic)
Až budete mít proměnná objektu, který odkazuje na objekt, často chcete pracovat se členy tohoto objektu, například metody, vlastnosti, pole a události. Například po vytvoření nové <xref:System.Windows.Forms.Form> objekt, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost nebo volání jeho <xref:System.Windows.Forms.Control.Focus%2A> metoda.  
  
## <a name="accessing-members"></a>Získávání přístupu k členům  
 Členové objektu přistupujete prostřednictvím proměnné, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object"></a>Pro přístup k členům v objektu  
  
-   Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Pokud je člen [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md), není nutné proměnnou, do které k němu přístup.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Přístup ke členům v objektu známé typu  
 Pokud znáte typ objektu v době kompilace, můžete použít *časné vazby* pro proměnné, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pro přístup k členům v objektu, pro kterou je znát typ v době kompilace  
  
1.  Deklarujte proměnnou objektu bude typu objektu, který chcete přiřadit k proměnné.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     S `Option Strict On`, můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozené od <xref:System.Windows.Forms.Form>) k `extraForm`. Pokud jste definovali třídu nebo strukturu s rozšíření `CType` převod na <xref:System.Windows.Forms.Form>, můžete také přiřadit třídy nebo struktury k `extraForm`.  
  
2.  Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Můžete všechny metody a vlastnosti specifické pro přístup <xref:System.Windows.Forms.Form> třída, bez ohledu na to, co `Option Strict` nastavení je.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Přístup ke členům objekt neznámého typu.  
 Pokud neznáte typ objektu v době kompilace, musíte použít *pozdní vazby* pro všechny proměnné, která odkazuje na ni.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pro přístup k členům v objektu, pro kterou neznáte typ v době kompilace  
  
1.  Deklarace proměnné objektu bude [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Deklarace proměnné jako `Object` je stejný jako deklarace jej jako <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     S `Option Strict On`, můžete přístup pouze členové, které jsou definovány na <xref:System.Object> třídy.  
  
2.  Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Abyste mohli přístup ke členům v libovolného objektu přiřadit proměnné objektu, musíte nastavit `Option Strict Off`. Když to uděláte, kompilátor nemůže zaručit, že je daný člen je zveřejněný prostřednictvím objektu, který přiřadíte k proměnné. Pokud objekt nevystavuje členem pokusu o přístup, <xref:System.MemberAccessException> došlo k výjimce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
