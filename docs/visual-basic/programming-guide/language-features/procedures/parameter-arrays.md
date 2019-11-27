---
title: Pole parametrů
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
ms.openlocfilehash: ffb532fbac70b9aa8ab210450e4d9207f5e0291f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351128"
---
# <a name="parameter-arrays-visual-basic"></a>Pole parametrů (Visual Basic)
Obvykle nemůžete volat proceduru s více argumenty, než určuje deklarace procedury. Pokud potřebujete nekonečný počet argumentů, můžete deklarovat *pole parametrů*, které umožňuje proceduře přijmout pole hodnot pro parametr. Při definování procedury není nutné znát počet prvků v poli parametrů. Velikost pole je určena jednotlivě každým voláním procedury.  
  
## <a name="declaring-a-paramarray"></a>Deklarace ParamArray  
 Použijete klíčové slovo [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) k označení pole parametrů v seznamu parametrů. Platí následující pravidla:  
  
- Procedura může definovat pouze jedno pole parametrů a musí se jednat o poslední parametr v definici procedury.  
  
- Pole parametrů musí být předáno hodnotou. Je dobrým postupem, jak explicitně do definice procedury přidat klíčové slovo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .  
  
- Pole parametrů je automaticky volitelné. Výchozí hodnota je prázdné jednorozměrné pole typu elementu pole parametrů.  
  
- Musí být požadovány všechny parametry předcházející poli parametrů. Pole parametrů musí být jediným volitelným parametrem.  
  
## <a name="calling-a-paramarray"></a>Volání ParamArray  
 Když zavoláte proceduru, která definuje pole parametrů, můžete dodat argument jedním z následujících způsobů:  
  
- Nothing – argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) můžete vynechat. V tomto případě je do procedury předáno prázdné pole. Pokud explicitně předáte klíčové slovo [Nothing](../../../../visual-basic/language-reference/nothing.md) , je do procedury předáno pole s hodnotou null a výsledkem volání NullReferenceException je, že volaná procedura tuto podmínku nekontroluje.
  
- Seznam libovolného počtu argumentů oddělených čárkami. Datový typ každého argumentu musí být implicitně převoditelné na `ParamArray` typ elementu.  
  
- Pole se stejným typem prvku jako typ elementu pole parametru.  
  
 Ve všech případech kód v proceduře zpracovává pole parametrů jako jednorozměrné pole s prvky stejného datového typu jako datový typ `ParamArray`.  
  
> [!IMPORTANT]
> Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace. Pokud přijmete pole parametrů, měli byste otestovat velikost pole, do kterého se předává volající kód. Pokud je pro vaši aplikaci moc velká, proveďte příslušné kroky. Další informace naleznete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje a volá funkci `calcSum`. Modifikátor `ParamArray` pro parametr `args` umožňuje funkci přijmout proměnný počet argumentů.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Následující příklad definuje proceduru s polem parametrů a vytvoří výstup hodnot všech prvků pole předaných do pole parametrů.  
  
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
