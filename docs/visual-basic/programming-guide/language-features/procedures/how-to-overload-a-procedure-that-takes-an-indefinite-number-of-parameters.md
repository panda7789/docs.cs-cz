---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.'
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
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387878"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).
Pokud má procedura parametr [ParamArray](../../../language-reference/modifiers/paramarray.md) , nemůžete definovat přetíženou verzi, která vezme jednorozměrné pole pro pole parametrů. Další informace naleznete v části "implicitní přetížení pro parametr ParamArray" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Přetížení procedury, která přebírá proměnný počet parametrů  
  
1. Zajistěte, aby procedura a volání logiky kódu byly přínosem z přetížených verzí více než z `ParamArray` parametru. Viz "přetížení a ParamArray" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).  
  
2. Určete, která čísla zadaných hodnot má procedura přijmout v proměnné části seznamu parametrů. To může zahrnovat případ bez hodnoty a může obsahovat případ jednorozměrného pole.  
  
3. Pro každý přijatelný počet zadaných hodnot, zápis `Sub` nebo `Function` příkaz deklarace, který definuje odpovídající seznam parametrů. V této přetížené verzi nepoužívejte `Optional` ani `ParamArray` klíčové slovo or.  
  
4. V každé deklaraci uveďte klíčové slovo `Sub` OR `Function` s klíčovým slovem [Overloads](../../../language-reference/modifiers/overloads.md) .  
  
5. Podle každé deklarace napište kód procedury, který by měl být proveden, když volající kód dodá hodnoty odpovídající seznamu parametrů dané deklarace.  
  
6. V případě potřeby ukončete jednotlivé postupy pomocí `End Sub` `End Function` příkazu nebo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje proceduru, která je definována s parametrem [ParamArray](../../../language-reference/modifiers/paramarray.md) , a pak ekvivalentní sadu přetížených procedur.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Taková procedura se nedá přetížit se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů. Můžete však použít signatury dalších implicitních přetížení. Tuto ilustraci ilustrují následující deklarace.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Kód v přetížených verzích nemusí testovat, zda volající kód zadal jednu nebo více hodnot pro `ParamArray` parametr, nebo pokud ano, kolik jich má. Visual Basic předá řízení verzi, která odpovídá seznamu argumentů volání.  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Vzhledem k tomu, že procedura s `ParamArray` parametrem je ekvivalentem sady přetížených verzí, nelze takovou proceduru přetížit se seznamem parametrů odpovídajícím žádné z těchto implicitních přetížení. Další informace najdete v tématu věnovaném [důležitým postupům při přetížení](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace. Pokud přijmete pole parametrů, měli byste otestovat délku pole, na které se předává volající kód, a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Volitelné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Rozlišení přetěžování](./overload-resolution.md)
