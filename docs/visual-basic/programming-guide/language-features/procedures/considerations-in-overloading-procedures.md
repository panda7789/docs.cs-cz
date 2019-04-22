---
title: Aspekty přetížení procedur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: f14cc28960af28530bda9a78c1309dea10c18b8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815588"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Aspekty přetížení procedur (Visual Basic)
Když je přetížení procedury, musíte použít jiný *podpis* jednotlivých přetížených verzí. To obvykle znamená, že každá verze musíte zadat seznam různých parametrů. Další informace najdete v tématu "Jiný podpis" [přetížení procedury](./procedure-overloading.md).  
  
 Můžete použít přetížení `Function` procedury s `Sub` postupu a naopak, pokud mají různé podpisy. Dvě přetížení nemůže se liší pouze v tom, jedna má návratovou hodnotu a druhá ne.  
  
 Vlastnost můžete přetížit stejným způsobem jako přetížení procedury a omezení. Nelze však přetížení procedury s vlastností nebo naopak.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternativy k přetížené verze  
 Máte někdy alternativy k přetížené verze, zejména pokud přítomnost argumentů je volitelný nebo jejich počet je proměnná.  
  
 Mějte na paměti, že volitelné argumenty nejsou nutně nepodporuje všechny jazyky a pole parametrů jsou omezené na Visual Basic. Pokud píšete procedury, která by mohla být volány kódem napsaným v některém z několika různých jazyků, přetížené verze nabídky nejvyšší flexibilitu.  
  
### <a name="overloads-and-optional-arguments"></a>Přetížení a nepovinné argumenty.  
 Pokud volající kód může volitelně můžete zadat nebo vynechat jeden nebo více argumentů, můžete definovat více přetížené verze nebo používat volitelné parametry.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kdy použít přetížené verze  
 Můžete zvážit, definování řadu přetížené verze v následujících případech:  
  
-   Logika v kódu procedury je výrazně liší v závislosti na tom, zda volající kód poskytuje volitelný argument nebo ne.  
  
-   Kód procedury nelze spolehlivě otestovat, zda volající kód dodal nepovinný argument. To platí, například, pokud neexistuje žádný možné Release candidate pro výchozí hodnotu, která volající kód nelze očekávat, že zadat.  
  
#### <a name="when-to-use-optional-parameters"></a>Kdy použít nepovinné parametry  
 Můžete dát přednost jeden nebo více volitelných parametrů v následujících případech:  
  
-   Pouze požadované akce, když volající kód neposkytuje nepovinný argument je nastavena na výchozí hodnotu parametru. V takovém případě může být méně složitý kód procedury definujete jednu verzi s jednou nebo více `Optional` parametry.  
  
 Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Přetížení a ParamArrays  
 Pokud volající kód může předat proměnlivý počet argumentů, můžete definovat více přetížené verze nebo použití pole parametrů.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kdy použít přetížené verze  
 Můžete zvážit, definování řadu přetížené verze v následujících případech:  
  
-   Víte, že volající kód nikdy neprocházejí více než malý počet hodnot pro pole parametrů.  
  
-   Logika v kódu procedury je výrazně liší v závislosti na tom, kolik hodnot volající kód předá.  
  
-   Volající kód může předat hodnoty z různých datových typů.  
  
#### <a name="when-to-use-a-parameter-array"></a>Kdy použít pole parametrů.  
 Budete se lépe vyhovovat `ParamArray` parametr v následujících případech:  
  
-   Nejste schopni předpovědět, kolik hodnot volající kód můžete předat pole parametrů a může to být hodně.  
  
-   Logiky postup slouží k procházení všech hodnot volající kód předá, provádí se v podstatě stejné operace v každé hodnotě.  
  
 Další informace najdete v tématu [pole parametrů](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Implicitní přetížení pro volitelné parametry  
 Procedura se [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametr je ekvivalentní na dvě přetížení procedury, jednu s volitelným parametrem a druhou bez parametru. Tento postup nejde přetížit se seznamem parametrů odpovídá buď z nich. Následující deklarace ukazuje to.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Pro proceduru s více než jeden volitelný parametr je sada implicitní přetížení, které byly přijaty logikou podobné jako v předchozím příkladu.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Implicitní přetížení pro ParamArray parametr  
 Kompilátor považuje postupu názvem [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr mít neomezený počet přetížení lišící se od sebe navzájem co volající kód předá pole parametrů, následujícím způsobem:  
  
-   Když volající kód neposkytuje argument pro jeden přetížená metoda `ParamArray`  
  
-   Jedním přetížením pro když volající kód poskytuje jednorozměrné pole `ParamArray` typ elementu  
  
-   Pro každý kladné celé číslo, jeden přetížení pro když volající kód poskytuje tento počet argumentů, každý z `ParamArray` typ elementu  
  
 Následující deklarace ukazují tyto implicitní přetížení.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Tento postup se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů nelze přetížit. Můžete však použít podpisy implicitní přetížení. Následující deklarace ukazuje to.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programování bez psaní jako alternativu k přetížení  
 Pokud chcete povolit, aby volající kód předat parametr různé datové typy, je alternativním přístupem programování bez psaní. Můžete nastavit typ kontroly přepínač tak, aby `Off` buď [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru. Potom není potřeba deklarovat datový typ parametru. Tento přístup má ale tyto nevýhody ve srovnání s přetížení:  
  
-   Programování bez psaní vytvoří méně efektivní provádění kódu.  
  
-   Postup, musíte otestovat pro každý typ dat je připraven předávaný.  
  
-   Kompilátor nemůže signalizujete chybu, pokud volající kód předá datový typ, který postup není podporován.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Řešení přetížení](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
