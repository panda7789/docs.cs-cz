---
title: Aspekty přetížení procedur (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac4bc47f9e781f83c7930efffedd40d9c25c2ec2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Aspekty přetížení procedur (Visual Basic)
Pokud jste přetížení procedury, je nutné použít jiné *podpis* pro každou přetížené verzi. To obvykle znamená, že každou verzi musíte zadat seznam různých parametrů. Další informace najdete v tématu "Jiný podpis" v [přetížení procedury](./procedure-overloading.md).  
  
 Můžete použít přetížení `Function` procedura s `Sub` postupu a naopak a poskytuje mají různé podpisy. Dvě přetížení nemůže se liší pouze v tom jeden má návratovou hodnotu a druhý není.  
  
 Můžete použít přetížení vlastnost stejným způsobem jako přetížení procedury a s stejná omezení. Nelze však přetížení procedury, vlastnost nebo naopak.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternativy k přetížené verze  
 Někdy máte alternativy přetížené verze, zvláště pokud přítomnost argumentů je volitelné nebo jejich počet proměnné.  
  
 Mějte na paměti, že volitelné argumenty nutně nepodporuje všechny jazyky a pole parametrů jsou omezeny na Visual Basic. Pokud píšete procedury, která je pravděpodobné, která se má volat z kódu napsaného v některém z několika různými jazyky, přetížený nabídka verze nejvyšší flexibilitu.  
  
### <a name="overloads-and-optional-arguments"></a>Přetížení a nepovinné argumenty  
 Při volání kód můžete volitelně zadat nebo vynechat jeden nebo více argumentů, můžete definovat několik verzí přetížené nebo použít volitelné parametry.  
  
#### <a name="when-to-use-overloaded-versions"></a>Při použití přetížených verzí  
 Můžete zvážit definování řadu přetížené verze v následujících případech:  
  
-   Logika kód postup se výrazně liší v závislosti na tom, zda kód volání poskytuje nepovinný argument, nebo ne.  
  
-   Kód procedury nelze spolehlivě otestovat, zda kód volání dodal za volitelným argumentem. Ano, například pokud není žádná možné kandidáta pro výchozí hodnotu, která kód volání nebylo se předpokládá, že zadat.  
  
#### <a name="when-to-use-optional-parameters"></a>Kdy použít volitelné parametry  
 Možná budete chtít jeden nebo více volitelné parametry v následujících případech:  
  
-   Pouze požadované akce při volání kód neposkytuje nepovinný argument je nastavit parametr na výchozí hodnotu. V takovém případě může být méně složitý kód postup při definování jedna verze s jedním nebo více `Optional` parametry.  
  
 Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Přetížení a ParamArrays  
 Při volání kód předat proměnný počet argumentů, můžete definovat několik verzí přetížené nebo použít pole parametrů.  
  
#### <a name="when-to-use-overloaded-versions"></a>Při použití přetížených verzí  
 Můžete zvážit definování řadu přetížené verze v následujících případech:  
  
-   Víte, že kód volání nikdy předá více než malý počet hodnot pole parametrů.  
  
-   Logika v postupu kódu je výrazně liší v závislosti na tom, kolik hodnot předá volání kódu.  
  
-   Volání kódu můžete předat hodnoty různých datových typů.  
  
#### <a name="when-to-use-a-parameter-array"></a>Kdy použít pole parametrů  
 Můžete se lépe vyhovovat `ParamArray` parametr v následujících případech:  
  
-   Nemůžete k předpovědi kolik hodnot volající kód můžete předat pole parametrů a může být velký počet.  
  
-   Postup logiku různě iterace v rámci všech hodnot kód volání úspěšně projde, provádění v podstatě stejné operace v každé hodnotě.  
  
 Další informace najdete v tématu [pole parametrů](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Implicitní přetížení pro volitelné parametry  
 Procedura se [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) je ekvivalentní přetížené dva postupy, jeden s volitelný parametr a jeden bez parametrů. Tento postup nelze přetížení s seznam parametrů odpovídající buď na kteroukoli z nich. Následující deklarace znázornění.  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Pro proceduru s více než jeden volitelný parametr je sada implicitní přetížení, které byly přijaty logikou podobné jako v předchozím příkladu.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Implicitní přetížení pro ParamArray parametr  
 Kompilátor zvažuje procedura se [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr mít libovolný počet přetížení, které se liší od sebe navzájem v co volací kód předá parametr pole, následujícím způsobem:  
  
-   Jednomu přetížení pro při volání kód neposkytuje argumentu `ParamArray`  
  
-   Jednomu přetížení pro při volání kód poskytuje jednorozměrného pole `ParamArray` typ elementu  
  
-   Pro každý kladné celé číslo, jeden přetížení pro při volání kód poskytuje tento počet argumentů, každý z `ParamArray` typ elementu  
  
 Následující deklarace znázorňují tyto implicitní přetížení.  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Tento postup se seznam parametrů, která přebírá jednorozměrné pole pro parametr pole nelze přetížení. Můžete však použít signatur implicitní přetížení. Následující deklarace znázornění.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programování bez psaní jako alternativu k přetížení  
 Pokud chcete povolit volání kódu pro různé datové typy předat parametru, je alternativní způsob programování bez psaní. Můžete nastavit typ kontroly přepínač tak, aby `Off` s buď [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru. Pak nemáte deklarovat datový typ parametru. Tento přístup má ale tyto nevýhody ve srovnání s přetížení:  
  
-   Programování bez psaní vytvoří méně efektivní provádění kódu.  
  
-   Postup, musíte otestovat pro každý typ dat je připravená na předávány.  
  
-   Kompilátor nelze signál chybu, pokud kód volání předá datový typ, který postup nepodporuje.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Řešení přetížení](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
