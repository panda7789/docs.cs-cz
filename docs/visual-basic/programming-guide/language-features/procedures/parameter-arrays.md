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
ms.openlocfilehash: a91da0d9e16ff11fdd4980588fee64b3e4a603c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652374"
---
# <a name="parameter-arrays-visual-basic"></a>Pole parametrů (Visual Basic)
Obvykle nelze volání procedury s další argumenty, než určuje postup deklarace. Pokud budete potřebovat nekonečný počet argumentů, můžou deklarovat *parametr pole*, což umožňuje postupu tak, aby přijímal pole hodnot parametru. Nemusíte vědět počet prvků v poli parametrů, když definujete postup. Velikost pole je určena jednotlivě každý volání k postupu.  
  
## <a name="declaring-a-paramarray"></a>Deklarace ParamArray  
 Můžete použít [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) – klíčové slovo k označení parametr pole v seznamu parametrů. Platí následující pravidla:  
  
-   Procedury můžete definovat jenom jeden parametr pole a musí být poslední parametr v definici postupu.  
  
-   Hodnotou musí být předán pole parametrů. Je dobrým zvykem explicitně zahrnovat programování [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo v definici postupu.  
  
-   Pole parametrů je automaticky volitelné. Výchozí hodnota je prázdná jednorozměrné pole typu prvku pole parametrů.  
  
-   Všechny parametry předcházející pole parametrů je nutné zadat. Pole parametrů musí být pouze volitelný parametr.  
  
## <a name="calling-a-paramarray"></a>Volání metody ParamArray  
 Při volání procedury, která definuje pole parametrů můžete zadat argument v některém z následujících způsobů:  
  
-   Nothing – to znamená, můžete vynechat [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument. V takovém případě je prázdné pole předaný postupu. Také můžete předat [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo pomocí stejného efektu.  
  
-   Seznam libovolný počet argumentů, oddělených čárkami. Datový typ jednotlivých argumentu musí být implicitně převést na `ParamArray` typ elementu.  
  
-   Pole s stejný typ elementu jako parametr pole typu elementu.  
  
 Ve všech případech se kód v rámci procesu považuje za jednorozměrné pole s prvky stejný datový typ jako parametr pole `ParamArray` datového typu.  
  
> [!IMPORTANT]
>  Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace. Pokud přijmete pole parametrů, měli byste otestovat pro velikost pole, které do ní předán volající kód. Proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci. Další informace najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje a volá funkci `calcSum`. `ParamArray` Modifikátor pro parametr `args` umožňuje funkci tak, aby přijímal proměnný počet argumentů.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 V následujícím příkladu definuje procedura se pole parametrů a výstupy hodnoty všechny elementy pole Předaný parametr pole.  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Předávání argumentů podle hodnoty a reference](./passing-arguments-by-value-and-by-reference.md)  
 [Předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md)  
 [Nepovinné parametry](./optional-parameters.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
