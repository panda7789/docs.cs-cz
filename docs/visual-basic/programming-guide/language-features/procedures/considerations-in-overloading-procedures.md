---
title: Aspekty přetížení procedur
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
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351001"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Aspekty přetížení procedur (Visual Basic)
Pokud převedete proceduru, musíte pro každou přetíženou verzi použít jiný *podpis* . To obvykle znamená, že každá verze musí určovat jiný seznam parametrů. Další informace naleznete v části "různé signatury" v tématu [Process Overloads](./procedure-overloading.md).  
  
 Můžete přetížit `Function` proceduru pomocí `Sub` procedury a naopak, pokud mají různé signatury. Dvě přetížení se nemohou lišit pouze v tom, že jedna má návratovou hodnotu a druhá ne.  
  
 Můžete přetížit vlastnost stejným způsobem jako procedura přetížení a se stejnými omezeními. Nemůžete však přetížit proceduru s vlastností, ani naopak.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternativy k přetíženým verzím  
 Někdy máte alternativu k přetíženým verzím, zejména v případě, že je přítomnost argumentů volitelná nebo jejich počet je proměnná.  
  
 Mějte na paměti, že volitelné argumenty nejsou nutně podporovány všemi jazyky a pole parametrů jsou omezeny na Visual Basic. Pokud píšete proceduru, která je pravděpodobně volána z kódu napsaného v některém z několika různých jazyků, přetížené verze nabízejí největší flexibilitu.  
  
### <a name="overloads-and-optional-arguments"></a>Přetížení a volitelné argumenty  
 Když volající kód může volitelně zadat nebo vynechat jeden nebo více argumentů, můžete definovat více přetížených verzí nebo použít volitelné parametry.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kdy použít přetížené verze  
 Můžete zvážit definování řady přetížených verzí v následujících případech:  
  
- Logika v kódu procedury je výrazně odlišná v závislosti na tom, zda volající kód dodává nepovinný argument nebo ne.  
  
- Kód procedury nemůže spolehlivě testovat, zda volající kód zadal volitelný argument. Jedná se například o případ, kdy není možný kandidát na výchozí hodnotu, kterou by volající kód nemohl dodat.  
  
#### <a name="when-to-use-optional-parameters"></a>Kdy použít volitelné parametry  
 V následujících případech můžete preferovat jeden nebo více volitelných parametrů:  
  
- Jediná požadovaná akce, když volající kód neposkytne volitelný argument, je nastavit parametr na výchozí hodnotu. V takovém případě může být kód procedury méně komplikovaný, pokud definujete jednu verzi s jedním nebo více `Optional` parametry.  
  
 Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Přetížení a ParamArray  
 Když volající kód může předat proměnný počet argumentů, můžete definovat více přetížených verzí nebo použít pole parametrů.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kdy použít přetížené verze  
 Můžete zvážit definování řady přetížených verzí v následujících případech:  
  
- Víte, že volající kód nikdy nepředává více než malý počet hodnot do pole parametrů.  
  
- Logika v kódu procedury je výrazně odlišná v závislosti na tom, kolik hodnot volající kód předává.  
  
- Volající kód může předat hodnoty různých datových typů.  
  
#### <a name="when-to-use-a-parameter-array"></a>Kdy použít pole parametrů  
 V následujících případech je lepší obsluhou `ParamArray` parametrem:  
  
- Nemůžete odhadnout, kolik hodnot může volající kód předat poli parametrů, a může to být velké číslo.  
  
- Procedura procedury je sama o sobě k iterování všech hodnot, které volající kód projde, a provádí v podstatě stejné operace na každé hodnotě.  
  
 Další informace naleznete v tématu [pole parametrů](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Implicitní přetížení pro volitelné parametry  
 Procedura s [volitelným](../../../../visual-basic/language-reference/modifiers/optional.md) parametrem je ekvivalentní dvou přetíženým procedurám, jeden s volitelným parametrem a druhý bez něj. Taková procedura se nedá přetížit se seznamem parametrů, který odpovídá některé z nich. Tuto ilustraci ilustrují následující deklarace.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Pro proceduru s více než jedním volitelným parametrem je množina implicitních přetížení, kterou dorazila v logice podobně jako v předchozím příkladu.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Implicitní přetížení parametru ParamArray  
 Kompilátor považuje proceduru s parametrem [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) za nekonečný počet přetížení a liší se od sebe v tom, co volající kód předává do pole parametrů, následovně:  
  
- Jedno přetížení pro, když volající kód nedodá argument pro `ParamArray`  
  
- Jedno přetížení pro, když volající kód dodá jednorozměrné pole typu elementu `ParamArray`.  
  
- Pro každé kladné celé číslo jedno přetížení pro, když volající kód dodá tento počet argumentů, každý z `ParamArray` typ elementu.  
  
 Následující deklarace ilustrují tato implicitní přetížení.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Taková procedura se nedá přetížit se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů. Můžete však použít signatury dalších implicitních přetížení. Tuto ilustraci ilustrují následující deklarace.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programování jako alternativa k přetížení  
 Pokud chcete, aby volající kód předával jiné datové typy parametru, alternativním přístupem je beztyp programování. Můžete nastavit přepínač pro kontrolu typu na `Off` s použitím [příkazu Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo pomocí možnosti kompilátoru [-OptionStrict –](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) . Pak nemusíte deklarovat datový typ parametru. Tento přístup ale má v porovnání s přetížením následující nevýhody:  
  
- Programování bez typů produkuje méně efektivní kód spuštění.  
  
- Procedura musí být testována pro každý datový typ, který předpokládá předání.  
  
- Kompilátor nemůže signalizovat chybu, pokud volající kód předává datový typ, který procedura nepodporuje.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Řešení přetížení](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
