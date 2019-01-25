---
title: 'Postupy: Řízení dostupnosti proměnné (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 4d5db7fe474d8732e0ae37f3d95d0187eef68ec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582485"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Postupy: Řízení dostupnosti proměnné (Visual Basic)
Řízení dostupnosti proměnné tak, že zadáte jeho *úroveň přístupu*. Úroveň přístupu určuje, jaký kód má oprávnění ke čtení nebo zápisu do proměnné.  
  
-   *Členské proměnné* (definované na úrovni modulu a mimo všechny procedury) výchozí veřejný přístup, což znamená, že veškerý kód, který můžete vidět k nim přistupovat. Toto můžete změnit tak, že zadáte modifikátor přístupu.  
  
-   *Lokální proměnné* (definované uvnitř procedury) formálně mít veřejný přístup, i když k nim může přistupovat pouze kód v rámci jejich procedury. Nelze změnit úroveň přístupu lokální proměnné, ale můžete změnit úroveň přístupu postup, který jej obsahuje.  
  
 Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Privátní a veřejné přístup  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Aby byla proměnná přístupný pouze uvnitř jeho modulu, třídy nebo struktury  
  
1.  Místo [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.  
  
2.  Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkazu.  
  
     Může číst nebo zapisovat do proměnné z kamkoli v modulu, třídy nebo struktury, ale ne z mimo něj.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Aby byla proměnná přístupný z jakéhokoli kódu, který je můžou zobrazit  
  
1.  Členské proměnné, umístěte `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.  
  
2.  Zahrnout [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkazu.  
  
     Může číst nebo zapisovat do proměnné z veškerý kód, který spolupracuje s vaší sestavení.  
  
 -nebo-  
  
1.  Pro místní proměnné, umístěte `Dim` příkaz pro proměnnou uvnitř procedury.  
  
2.  Nejsou zahrnuté `Public` – klíčové slovo v `Dim` příkazu.  
  
     Může číst nebo zapisovat do proměnné z kdekoli v rámci procesu, ale ne z mimo něj.  
  
## <a name="protected-and-friend-access"></a>Chráněné a přístup typu Friend  
 Můžete omezit úroveň přístupu proměnné do své třídy a všechny odvozené třídy, nebo jeho sestavení. Můžete také zadat unii tato omezení, která umožňuje přístup z kódu v kterékoli odvozené třídě, nebo na jiném místě ve stejném sestavení. Zadejte tento sjednocení tím, že zkombinujete `Protected` a `Friend` klíčová slova ve stejné deklaraci.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Aby byla proměnná přístupný pouze uvnitř své třídy a všechny odvozené třídy  
  
1.  Místo `Dim` příkaz pro proměnnou uvnitř třídy, ale mimo všechny procedury.  
  
2.  Zahrnout [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v `Dim` příkazu.  
  
     Může číst nebo zapisovat do proměnné z kdekoli v rámci třídy, stejně jako v rámci jakékoli třídy odvozené z něj, ale ne z mimo všechny třídy v řetězci odvození.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Aby byla proměnná přístupný pouze z v rámci stejného sestavení  
  
1.  Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.  
  
2.  Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v `Dim` příkazu.  
  
     Může číst nebo zapisovat do proměnné z kamkoli v modulu, třídy nebo struktury, stejně jako v žádném kódu ve stejném sestavení, ale ne z mimo sestavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje deklarace proměnných s `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private` úrovně přístupu. Všimněte si, že `Dim` příkaz určuje úroveň přístupu, není potřeba zahrnout `Dim` – klíčové slovo.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Více omezující úroveň přístupu proměnné, čím menší pravděpodobnost, že škodlivý kód může být nesprávné využít.  
  
## <a name="see-also"></a>Viz také:
- [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
