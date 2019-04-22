---
title: Pole parametrů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834154"
---
# <a name="parameter-arrays-visual-basic"></a>Pole parametrů (Visual Basic)
Obvykle nelze volat proceduru s více argumentů, než určuje deklaraci procedury. Když budete potřebovat nekonečný počet argumentů, je možné deklarovat *pole parametrů*, který umožňuje procedury tak, aby přijímal pole hodnot pro parametr. Není nutné znát počet prvků v poli parametrů při definování procesu. Velikost pole je samostatně určeno každé volání do procedury.  
  
## <a name="declaring-a-paramarray"></a>Deklarace ParamArray  
 Můžete použít [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) – klíčové slovo k označení pole parametrů. v seznamu parametrů. Platí následující pravidla:  
  
-   Postup lze definovat pouze jeden parametr pole a musí být poslední parametr v definici procedury.  
  
-   Pole parametrů musí být předán podle hodnoty. To při programování je dobrým zvykem zahrnout explicitně [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo v definici procedury.  
  
-   Pole parametrů je automaticky volitelné. Výchozí hodnota je prázdné jednorozměrné pole typu prvku pole parametrů.  
  
-   Všechny parametry předchozí pole parametrů musí být povinné. Pole parametrů musí být pouze volitelný parametr.  
  
## <a name="calling-a-paramarray"></a>Volání ParamArray  
 Při volání procedury, která definuje pole parametrů můžete zadat argument do některého z následujících způsobů:  
  
-   Nothing – to znamená, můžete vynechat [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument. V takovém případě prázdné pole je předán do procedury. Můžete také předat [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo se stejný účinek.  
  
-   Seznam libovolný počet argumentů, oddělené čárkami. Datový typ každého argumentu musí být implicitně převeditelný na `ParamArray` typ elementu.  
  
-   Pole se stejným typem elementu jako typ elementu pole parametrů.  
  
 Ve všech případech se kód v rámci postupu považuje za jednorozměrné pole s prvky stejného datového typu jako pole parametrů `ParamArray` datového typu.  
  
> [!IMPORTANT]
>  Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace. Pokud souhlasíte s polem parametrů, měli byste otestovat pro velikost pole, které do něho předaný volajícímu kódu. Přijmout vhodná opatření, pokud je příliš velký pro vaši aplikaci. Další informace najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje a volá funkci `calcSum`. `ParamArray` Modifikátor parametru `args` umožňuje funkci tak, aby přijímal proměnný počet argumentů.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Následující příklad definuje proceduru s polem parametrů a vypíše hodnoty ze všech prvků pole předat pole parametrů.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)
- [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
