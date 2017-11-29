---
title: "Postupy: Přístup ke členům v objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
