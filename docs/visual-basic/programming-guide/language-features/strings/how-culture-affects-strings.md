---
title: Vliv jazykové verze na řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 9cbd3a5b8685178259b76d97919ea097ae72f6ae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401963"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Vliv jazykové verze na řetězce v jazyce Visual Basic
Tato stránka HELP popisuje, jak Visual Basic používá informace o jazykové verzi k provádění převodů a porovnávání řetězců.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kdy použít řetězce specifické pro jazykovou verzi  
 Obvykle byste měli použít řetězce specifické pro jazykovou verzi pro všechna data, která jsou zobrazena a čtena uživateli, a používat pro interní data vaší aplikace neutrální řetězce jazykové verze.  
  
 Například pokud vaše aplikace požaduje, aby uživatel zadal datum jako řetězec, měl by očekávat, že uživatelé budou formátovat řetězce podle jejich kultury a aplikace by měla odpovídajícím způsobem převést řetězec. Pokud vaše aplikace následně uvede toto datum v uživatelském rozhraní, měla by být uvedena v jazykové verzi uživatele.  
  
 Pokud však aplikace nahraje datum na centrální server, měl by formátovat řetězec podle jedné konkrétní jazykové verze, aby nedocházelo k záměně mezi potenciálně odlišnými formáty data.  
  
## <a name="culture-sensitive-functions"></a>Funkce závislé na jazykové verzi  
 Všechny Visual Basic funkce převodu řetězce (s výjimkou `Str` `Val` funkcí a) používají informace o jazykové verzi aplikace k zajištění, že převody a porovnávání jsou vhodné pro jazykovou verzi uživatele aplikace.  
  
 Klíč k úspěšnému použití funkcí pro převod řetězců v aplikacích, které jsou spuštěny v počítačích s různými nastaveními jazykové verze, je pochopit, které funkce používají konkrétní nastavení jazykové verze a které používají aktuální nastavení jazykové verze. Všimněte si, že nastavení jazykové verze aplikace je ve výchozím nastavení zděděné z nastavení jazykové verze operačního systému. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkce pro <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Hex%2A> <xref:Microsoft.VisualBasic.Conversion.Oct%2A> [převod typů](../../../language-reference/functions/type-conversion-functions.md),,,,,, a.  
  
 `Str`Funkce (převádí čísla na řetězce) a `Val` (převede řetězce na čísla) nepoužívají při převodu mezi řetězci a čísly jazykové verze aplikace. Místo toho rozpoznávají pouze tečku (.) jako platný oddělovač desetinných míst. Mezi kulturní a analogické analogové funkce patří:  
  
- **Převody, které používají aktuální jazykovou verzi.** `CStr`Funkce a `Format` převádějí číslo na řetězec a `CDbl` `CInt` funkce a převádějí řetězec na číslo.  
  
- **Převody, které používají konkrétní jazykovou verzi.** Každý objekt Number má `ToString(IFormatProvider)` metodu, která převede číslo na řetězec a `Parse(String, IFormatProvider)` metodu, která převede řetězec na číslo. Například `Double` Typ poskytuje <xref:System.Double.ToString%28System.IFormatProvider%29> <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> metody a.  
  
 Další informace naleznete v tématech <xref:Microsoft.VisualBasic.Conversion.Str%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Použití konkrétní jazykové verze  
 Představte si, že vyvíjíte aplikaci, která odesílá datum (formátovaná jako řetězec) webové službě. V takovém případě musí vaše aplikace používat specifickou jazykovou verzi pro převod řetězce. Pro ilustraci příčiny zvažte výsledek použití <xref:System.DateTime.ToString> metody data: Pokud vaše aplikace používá tuto metodu k formátování data 4. července 2005, vrátí "7/4/2005 12:00:00 dop" při spuštění USA s jazykovou verzí 04.07.2005 English (EN-US), ale vrátí "00:00:00" při spuštění s jazykovou verzí němčina (de-de-de).  
  
 Pokud potřebujete provést převod řetězce v konkrétním formátu jazykové verze, měli byste použít `CultureInfo` třídu, která je integrována do .NET Framework. Můžete vytvořit nový `CultureInfo` objekt pro konkrétní jazykovou verzi předáním názvu jazykové verze <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktoru. Podporované názvy jazykové verze jsou uvedeny na <xref:System.Globalization.CultureInfo> stránce s nápovědě třídy.  
  
 Alternativně můžete získat instanci *neutrální jazykové verze* z <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> Vlastnosti. Invariantní jazyková verze je založena na anglické jazykové verzi, ale existuje několik rozdílů. Například invariantní jazyková verze určuje 24hodinové hodiny místo 12 hodin.  
  
 Chcete-li převést datum na řetězec jazykové verze, předejte <xref:System.Globalization.CultureInfo> objekt metodě objektu Date <xref:System.DateTime.ToString%28System.IFormatProvider%29> . Například následující kód zobrazí "07/04/2005 00:00:00", bez ohledu na nastavení jazykové verze aplikace.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Literály data jsou vždy interpretovány podle anglické jazykové verze.  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Existují dvě důležité situace, kdy je potřeba porovnávání řetězců:  
  
- **Řazení dat pro zobrazení uživateli** Použijte operace založené na aktuální jazykové verzi, aby se odpovídajícím způsobem seřadily řetězce.  
  
- **Určení, zda dvě řetězce interní aplikace odpovídají přesně (typicky pro účely zabezpečení).** Použijte operace, které ignorují aktuální jazykovou verzi.  
  
 Pomocí funkce Visual Basic můžete provádět oba typy porovnávání <xref:Microsoft.VisualBasic.Strings.StrComp%2A> . Zadejte nepovinný `Compare` argument pro řízení typu porovnání: `Text` pro většinu vstupů a výstupů `Binary` pro určení přesné shody.  
  
 `StrComp`Funkce vrací celé číslo, které určuje vztah mezi dvěma porovnávaných řetězci na základě pořadí řazení. Kladná hodnota pro výsledek označuje, že první řetězec je větší než druhý řetězec. Záporný výsledek označuje, že první řetězec je menší a nula značí rovnost mezi řetězci.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Můžete také použít .NET Framework partnera `StrComp` funkce, <xref:System.String.Compare%2A?displayProperty=nameWithType> metody. Toto je statická, přetížená metoda základní řetězcové třídy. Následující příklad ukazuje, jak je tato metoda používána:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Pro lepší kontrolu nad tím, jak se provádí porovnávání, můžete použít další přetížení <xref:System.String.Compare%2A> metody. Pomocí <xref:System.String.Compare%2A?displayProperty=nameWithType> metody můžete použít `comparisonType` argument k určení typu porovnání, které se má použít.  
  
|Hodnota `comparisonType` argumentu|Typ porovnání|Kdy je použít|  
|---|---|---|  
|`Ordinal`|Porovnání na základě bajtů součásti řetězce|Tuto hodnotu použijte při porovnávání: Identifikátory rozlišující velká a malá písmena, nastavení související se zabezpečením nebo jiné nelingvistické identifikátory, kde se musí bajty přesně shodovat.|  
|`OrdinalIgnoreCase`|Porovnání na základě bajtů součásti řetězce<br /><br /> `OrdinalIgnoreCase`používá invariantní informace o jazykové verzi k určení, kdy se dva znaky liší pouze velkými písmeny.|Tuto hodnotu použijte při porovnávání: identifikátory bez rozlišení velkých a malých písmen, nastavení týkající se zabezpečení a data uložená v systému Windows.|  
|`CurrentCulture` nebo `CurrentCultureIgnoreCase`|Porovnání na základě interpretace řetězců v aktuální jazykové verzi.|Při porovnávání použijte tyto hodnoty: data, která se zobrazují uživateli, většinu vstupu uživatele a další data, která vyžadují jazykovou interpretaci.|  
|`InvariantCulture` nebo `InvariantCultureIgnoreCase`|Porovnání na základě interpretace řetězců v neutrální jazykové verzi.<br /><br /> To se liší od `Ordinal` a `OrdinalIgnoreCase` , protože invariantní jazyková verze zpracovává znaky mimo svůj přijatý rozsah jako ekvivalentní znaky invariant.|Tyto hodnoty použijte pouze při porovnávání trvalých dat nebo zobrazení lingvisticky relevantních dat, která vyžadují pevné pořadí řazení.|  
  
### <a name="security-considerations"></a>Aspekty zabezpečení  
 Pokud vaše aplikace provádí rozhodnutí o zabezpečení na základě výsledku porovnání nebo operace změny velikosti písmen, pak by tato operace měla používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu a metodu předat `Ordinal` nebo `OrdinalIgnoreCase` pro `comparisonType` argument.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.CultureInfo>
- [Představení řetězců v jazyce Visual Basic](introduction-to-strings.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
