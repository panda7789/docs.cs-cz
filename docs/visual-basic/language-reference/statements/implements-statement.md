---
title: Implements – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 75776e0d78bc1d8a834333ea4c3cc0a9291d1ed1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965008"
---
# <a name="implements-statement"></a>Implements – Příkaz
Určuje jeden nebo více rozhraní, nebo člen rozhraní, které musí být implementován ve třídě nebo definice struktury, ve kterém se zobrazí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Součásti  
 `interfacename`  
 Povinný parametr. Rozhraní, jehož vlastnosti, procedury a události jsou k implementaci odpovídající členy třídy nebo struktury.  
  
 `interfacemember`  
 Povinný parametr. Člen rozhraní, které se implementuje.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní je kolekce představující členy (vlastnosti, procedury a události) prototypů zapouzdřuje rozhraní. Rozhraní obsahovat pouze deklarace pro členy. třídy a struktury implementace těchto členů. Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Implements` Příkaz musí následovat bezprostředně `Class` nebo `Structure` příkazu.  
  
 Při implementaci rozhraní, musí implementovat všechny členy deklarované v rozhraní. Každý člen s vynecháním se považuje za chybu syntaxe. Chcete-li implementovat jednotliví členové, zadejte [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) – klíčové slovo (které jsou oddělené od `Implements` příkaz) Pokud deklarujete člena třídy nebo struktury. Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Můžete použít třídy [privátní](../../../visual-basic/language-reference/modifiers/private.md) implementace vlastnosti a postupy, ale tyto členy jsou přístupné pouze pomocí přetypování instance implementující třídu do proměnné deklarované se typ rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `Implements` příkaz implementovat členy rozhraní. Definuje rozhraní s názvem `ICustomerInfo` událost, vlastnosti a procedury. Třída `customerInfo` implementuje všechny členy definované v rozhraní.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Všimněte si, že třída `customerInfo` používá `Implements` příkazem na řádku samostatného zdrojového kódu k označení, že třída implementuje všechny členy `ICustomerInfo` rozhraní. Poté každý člen ve třídě, použije `Implements` – klíčové slovo jako součást její deklarace člena k označení, že implementuje člena rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu. K otestování implementace, přidejte do projektu a volání těchto postupů `testImplements` postup.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Viz také:
- [Implementuje](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
