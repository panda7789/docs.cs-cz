---
title: "Postupy: Řízení dostupnosti proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Postupy: Řízení dostupnosti proměnné (Visual Basic)
Řízení dostupnosti proměnné zadáním jeho *úroveň přístupu*. Úroveň přístupu určuje, jaký kód má oprávnění ke čtení nebo zápisu do proměnné.  
  
-   *Členské proměnné* (definovanou na úrovni modulu a mimo libovolná procedura) výchozí nastavení veřejný přístup, což znamená, kód, který můžete vidět k nim mají přístup. Toto můžete změnit zadáním – modifikátor přístupu.  
  
-   *Lokální proměnné* (definované uvnitř procedury) jmenovitě mít veřejný přístup, i když k nim mít přístup jenom kód v rámci jejich procedury. Nelze změnit úroveň přístupu, místní proměnné, ale můžete změnit úroveň přístupu tohoto postupu, který jej obsahuje.  
  
 Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Privátní a veřejné přístup  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Chcete-li proměnnou přístupné pouze v rámci jeho modulu, třídu nebo strukturu  
  
1.  Místo [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkaz.  
  
     Můžou číst nebo zapisovat do proměnné z kamkoli v modulu, třídu nebo strukturu, ale nikoli z mimo něj.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Chcete-li proměnnou přístupné z kód, který můžete zobrazit  
  
1.  Členské proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkaz.  
  
     Můžou číst nebo zapisovat do proměnné ze kód, který bude spolupracovat s vaší sestavení.  
  
 -nebo-  
  
1.  Pro místní proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř procedury.  
  
2.  Nezahrnovat `Public` – klíčové slovo v `Dim` příkaz.  
  
     Můžou číst nebo zapisovat do proměnné z kdekoli v rámci procesu, ale nikoli z mimo něj.  
  
## <a name="protected-and-friend-access"></a>Protected Friend přístupu a  
 Můžete omezit úroveň přístupu proměnné do své třídy a všechny odvozené třídy, nebo jeho sestavení. Můžete také zadat sjednocení tato omezení, která umožňuje přístup z kódu všechny odvozené třídy nebo na jiném místě ve stejném sestavení. Zadejte tento sjednocení tím, že zkombinujete `Protected` a `Friend` klíčová slova ve stejné deklaraci.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Chcete-li proměnnou přístupné pouze v rámci své třídy a všechny odvozené třídy  
  
1.  Místo `Dim` příkaz pro proměnnou uvnitř třídy, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v `Dim` příkaz.  
  
     Můžou číst nebo zapisovat do proměnné z kdekoli v rámci třídy, ale také v libovolné třídy odvozené z něj, ale nikoli z mimo všechny třídy v řetězu odvození.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Chcete-li proměnnou přístupné pouze v rámci stejného sestavení  
  
1.  Místo `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v `Dim` příkaz.  
  
     Můžou číst nebo zapisovat do proměnné z kamkoli v modulu, třídu nebo strukturu, a také z jakékoli kódu ve stejném sestavení, ale nikoli z mimo sestavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje deklarace proměnné s `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private` úrovně přístupu. Všimněte si, že pokud `Dim` příkaz určuje úroveň přístupu, není potřeba zahrnovat `Dim` – klíčové slovo.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Více omezující úroveň přístupu proměnné, tím menší pravděpodobnost, že škodlivý kód způsobit nesprávné použití ho.  
  
## <a name="see-also"></a>Viz také  
 [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Veřejné](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Chráněný](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privátní](../../../../visual-basic/language-reference/modifiers/private.md)
