---
title: Implements – Příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351150"
---
# <a name="implements-statement"></a>Implements – Příkaz
Určuje jedno nebo více rozhraní nebo členů rozhraní, které musí být implementovány v definici třídy nebo struktury, ve které se zobrazí.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Součásti  
 `interfacename`  
 Požadováno. Rozhraní, jehož vlastnosti, procedury a události mají být implementovány odpovídajícími členy třídy nebo struktury.  
  
 `interfacemember`  
 Požadováno. Člen rozhraní, které je implementováno.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní je kolekce prototypů představujících členy (vlastnosti, procedury a události) zapouzdření rozhraní. Rozhraní obsahují pouze deklarace členů; třídy a struktury implementují tyto členy. Další informace naleznete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Příkaz `Implements` musí bezprostředně následovat po příkazu `Class` nebo `Structure`.  
  
 Při implementaci rozhraní je nutné implementovat všechny členy deklarované v rozhraní. Vynechání všech členů je považováno za chybu syntaxe. Chcete-li implementovat jednotlivé členy, zadáte klíčové slovo [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (které je odděleno od příkazu `Implements`), pokud deklarujete člena ve třídě nebo struktuře. Další informace naleznete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Třídy mohou používat [privátní](../../../visual-basic/language-reference/modifiers/private.md) implementace vlastností a postupů, ale tyto členy jsou přístupné pouze přetypováním instance implementující třídy do proměnné deklarované jako typ rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít příkaz `Implements` pro implementaci členů rozhraní. Definuje rozhraní s názvem `ICustomerInfo` s událostí, vlastností a procedurou. Třída `customerInfo` implementuje všechny členy definované v rozhraní.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Všimněte si, že třída `customerInfo` používá příkaz `Implements` na samostatné řádce zdrojového kódu k označení toho, že třída implementuje všechny členy rozhraní `ICustomerInfo`. Pak každý člen ve třídě používá klíčové slovo `Implements` jako součást své deklarace členů, aby označoval, že implementuje tento člen rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu. Chcete-li otestovat implementaci, přidejte tyto procedury do projektu a zavolejte `testImplements` proceduru.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Viz také:

- [Implementace](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
