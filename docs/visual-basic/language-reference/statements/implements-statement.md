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
ms.openlocfilehash: 7fb43934d8c200ff29b1caf63cec830b2c6633ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404547"
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
 Povinná hodnota. Rozhraní, jehož vlastnosti, procedury a události mají být implementovány odpovídajícími členy třídy nebo struktury.  
  
 `interfacemember`  
 Povinná hodnota. Člen rozhraní, které je implementováno.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní je kolekce prototypů představujících členy (vlastnosti, procedury a události) zapouzdření rozhraní. Rozhraní obsahují pouze deklarace členů; třídy a struktury implementují tyto členy. Další informace naleznete v tématu [rozhraní](../../programming-guide/language-features/interfaces/index.md).  
  
 `Implements`Příkaz musí následovat po `Class` `Structure` příkazu or.  
  
 Při implementaci rozhraní je nutné implementovat všechny členy deklarované v rozhraní. Vynechání všech členů je považováno za chybu syntaxe. Chcete-li implementovat jednotlivé členy, zadáte klíčové slovo [Implements](implements-clause.md) (které je odděleno od `Implements` příkazu) při deklaraci člena ve třídě nebo struktuře. Další informace naleznete v tématu [rozhraní](../../programming-guide/language-features/interfaces/index.md).  
  
 Třídy mohou používat [privátní](../modifiers/private.md) implementace vlastností a postupů, ale tyto členy jsou přístupné pouze přetypováním instance implementující třídy do proměnné deklarované jako typ rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `Implements` příkaz k implementaci členů rozhraní. Definuje rozhraní s názvem `ICustomerInfo` událost, vlastnost a procedura. Třída `customerInfo` implementuje všechny členy definované v rozhraní.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Všimněte si, že třída `customerInfo` používá `Implements` příkaz na samostatné řádce zdrojového kódu k označení toho, že třída implementuje všechny členy `ICustomerInfo` rozhraní. Pak každý člen ve třídě používá `Implements` klíčové slovo jako součást deklarace členu, aby označoval, že implementuje tento člen rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu. Chcete-li otestovat implementaci, přidejte tyto procedury do projektu a zavolejte `testImplements` proceduru.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Viz také

- [Implementuje](implements-clause.md)
- [Interface – příkaz](interface-statement.md)
- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
