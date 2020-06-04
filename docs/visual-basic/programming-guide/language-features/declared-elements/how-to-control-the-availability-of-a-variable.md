---
title: 'Postupy: Řízení dostupnosti proměnné'
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
ms.openlocfilehash: 0bfa7fa2bdac4746827884c1dad62734c549a48e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357384"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Postupy: Řízení dostupnosti proměnné (Visual Basic)
Dostupnost proměnné můžete řídit zadáním její *úrovně přístupu*. Úroveň přístupu určuje, který kód má oprávnění ke čtení nebo zápisu do proměnné.  
  
- *Členské proměnné* (definované na úrovni modulu a mimo jakoukoli proceduru) jsou výchozí pro veřejný přístup, což znamená, že k nim budou mít přístup všechny kódy, které je můžou zobrazit. To můžete změnit zadáním modifikátoru přístupu.  
  
- *Místní proměnné* (definované uvnitř procedury) mají formálně přístupný veřejný přístup, i když k nim mají přístup jenom kód v rámci jejich postupu. Úroveň přístupu místní proměnné se nedá změnit, ale můžete změnit úroveň přístupu pro proceduru, která ho obsahuje.  
  
 Další informace najdete v tématu [úrovně přístupu v Visual Basic](access-levels.md).  
  
## <a name="private-and-public-access"></a>Privátní a veřejný přístup  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Aby byla proměnná přístupná pouze v rámci svého modulu, třídy nebo struktury  
  
1. Do modulu, třídy nebo struktury umístěte [příkaz Dim](../../../language-reference/statements/dim-statement.md) pro proměnnou, ale mimo jakoukoli proceduru.  
  
2. Do příkazu zahrňte klíčové slovo [Private](../../../language-reference/modifiers/private.md) `Dim` .  
  
     Můžete číst nebo zapisovat do proměnné odkudkoli v rámci modulu, třídy nebo struktury, ale ne z vnějšku.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Aby byla proměnná přístupná z libovolného kódu, který je uvidí  
  
1. Pro členskou proměnnou umístěte `Dim` příkaz pro proměnnou do modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu zahrňte klíčové slovo [Public](../../../language-reference/modifiers/public.md) `Dim` .  
  
     Můžete číst nebo zapisovat do proměnné z libovolného kódu, který spolupracuje s vaším sestavením.  
  
 -nebo-  
  
1. Pro místní proměnnou umístěte `Dim` příkaz pro proměnnou do procedury.  
  
2. Nezahrnujte `Public` klíčové slovo do `Dim` příkazu.  
  
     Můžete číst nebo zapisovat do proměnné z libovolného místa v rámci tohoto postupu, ale ne z vnějšku.  
  
## <a name="protected-and-friend-access"></a>Chráněný a přítel přístup  
 Úroveň přístupu proměnné lze omezit na její třídu a jakékoli odvozené třídy nebo na její sestavení. Můžete také zadat sjednocení těchto omezení, což umožňuje přístup z kódu v jakékoli odvozené třídě nebo na jakémkoli jiném místě ve stejném sestavení. Tuto sjednocení zadáte kombinováním `Protected` `Friend` klíčových slov a ve stejné deklaraci.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Chcete-li zpřístupnit proměnnou pouze v rámci své třídy a všech odvozených tříd  
  
1. Umístěte `Dim` příkaz pro proměnnou uvnitř třídy, ale vně jakékoli procedury.  
  
2. Do příkazu zahrňte klíčové slovo [Protected](../../../language-reference/modifiers/protected.md) `Dim` .  
  
     Můžete číst nebo zapisovat do proměnné odkudkoli v rámci třídy a také z jakékoli třídy odvozené z ní, ale ne z vnějšku žádné třídy v řetězu odvození.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Chcete-li nastavit přístup k proměnné pouze v rámci stejného sestavení  
  
1. Umístěte `Dim` příkaz pro proměnnou do modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu zahrňte klíčové slovo [Friend](../../../language-reference/modifiers/friend.md) `Dim` .  
  
     Můžete číst nebo zapisovat do proměnné odkudkoli v rámci modulu, třídy nebo struktury, jakož i z libovolného kódu ve stejném sestavení, ale nikoli mimo sestavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje deklarace proměnných s `Public` `Protected` úrovněmi přístupu,, `Friend` , `Protected Friend` a `Private` . Všimněte si, že když `Dim` příkaz určuje úroveň přístupu, nemusíte vkládat `Dim` klíčové slovo.  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Přísnější úroveň přístupu proměnné, menší riziko, že škodlivý kód může nevhodným způsobem používat.  
  
## <a name="see-also"></a>Viz také

- [Úrovně přístupu v Visual Basic](access-levels.md)
- [Dim – příkaz](../../../language-reference/statements/dim-statement.md)
- [Republik](../../../language-reference/modifiers/public.md)
- [Proti](../../../language-reference/modifiers/protected.md)
- [Friend](../../../language-reference/modifiers/friend.md)
- [Hlášen](../../../language-reference/modifiers/private.md)
