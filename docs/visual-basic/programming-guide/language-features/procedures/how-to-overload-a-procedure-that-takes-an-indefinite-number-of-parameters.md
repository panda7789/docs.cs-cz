---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838986"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic)
Pokud má procedura [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nelze definovat přetížené verze, přičemž jednorozměrné pole pro pole parametrů. Další informace najdete v tématu "Implicitní přetížení pro parametrem ParamArray" [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Přetížení procedury, která přijímá proměnný počet parametrů  
  
1.  Ověření, že postup a výhody logiku kódu z volání přetížené verze víc než `ParamArray` parametru. Viz "Přetížení a ParamArrays" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
2.  Určení, která čísla zadané hodnoty by měla přijímat podle postupu v části proměnných ze seznamu parametrů. To může zahrnovat i v případě žádnou hodnotu a může obsahovat velikost písmen jednoho jednorozměrné pole.  
  
3.  Pro každý přijatelné počet zadaných hodnot, zápisu `Sub` nebo `Function` příkazu deklarace, která definuje odpovídající seznamu parametrů. Nepoužívejte buď `Optional` nebo `ParamArray` – klíčové slovo v této verzi přetížená.  
  
4.  V deklaraci, předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.  
  
5.  Po deklaraci psát kód postup, který by se měl spustit, když volající kód poskytuje hodnoty pro tato deklarace seznamu parametrů.  
  
6.  Ukončit každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definované pomocí procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr a ekvivalentní sadu přetížené procedury.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Tento postup se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů nelze přetížit. Můžete však použít podpisy implicitní přetížení. Následující deklarace ukazuje to.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Není potřeba otestovat, zda volající kód zadali jednu nebo více hodnot pro kód v přetížené verze `ParamArray` parametr, nebo pokud ano, kolik. Visual Basic předá řízení verzi, která odpovídá seznamu argumentů volání.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Protože procedura se `ParamArray` parametr je ekvivalentní k sadě přetížené verze, nejde přetížit tento postup se seznamem parametrů odpovídá některé z těchto implicitní přetížení. Další informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace. Pokud souhlasíte s polem parametrů, by měl test pro délku pole do něho předaný volající kód a proveďte příslušné kroky, pokud je příliš velký pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Řešení přetížení](./overload-resolution.md)
