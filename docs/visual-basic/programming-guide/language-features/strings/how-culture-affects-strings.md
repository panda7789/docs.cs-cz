---
title: Vliv jazykové verze na řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d090a6e89a470958dd323c3f249ed0658dc1cefa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955092"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Vliv jazykové verze na řetězce v jazyce Visual Basic
Tato stránka HELP popisuje, jak Visual Basic používá informace o jazykové verzi k provádění převodů a porovnávání řetězců.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kdy použít řetězce specifické pro jazykovou verzi  
 Obvykle byste měli použít řetězce specifické pro jazykovou verzi pro všechna data, která jsou zobrazena a čtena uživateli, a používat pro interní data vaší aplikace neutrální řetězce jazykové verze.  
  
 Například pokud vaše aplikace požaduje, aby uživatel zadal datum jako řetězec, měl by očekávat, že uživatelé budou formátovat řetězce podle jejich kultury a aplikace by měla odpovídajícím způsobem převést řetězec. Pokud vaše aplikace následně uvede toto datum v uživatelském rozhraní, měla by být uvedena v jazykové verzi uživatele.  
  
 Pokud však aplikace nahraje datum na centrální server, měl by formátovat řetězec podle jedné konkrétní jazykové verze, aby nedocházelo k záměně mezi potenciálně odlišnými formáty data.  
  
## <a name="culture-sensitive-functions"></a>Funkce závislé na jazykové verzi  
 Všechny funkce Visual Basicho převodu řetězců (s výjimkou `Str` funkcí a `Val` ) používají informace o jazykové verzi aplikace k zajištění, že převody a porovnávání jsou vhodné pro jazykovou verzi aplikace. uživatelský.  
  
 Klíč k úspěšnému použití funkcí pro převod řetězců v aplikacích, které jsou spuštěny v počítačích s různými nastaveními jazykové verze, je pochopit, které funkce používají konkrétní nastavení jazykové verze a které používají aktuální nastavení jazykové verze. Všimněte si, že nastavení jazykové verze aplikace je ve výchozím nastavení zděděné z nastavení jazykové verze operačního systému. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Asc%2A>funkce <xref:Microsoft.VisualBasic.Strings.AscW%2A>pro <xref:Microsoft.VisualBasic.Strings.Chr%2A> [převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md), <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A> <xref:Microsoft.VisualBasic.Strings.Format%2A>,,, a.  
  
 Funkce (převádí čísla na řetězce) a `Val` (převede řetězce na čísla) nepoužívají při převodu mezi řetězci a čísly jazykové verze aplikace. `Str` Místo toho rozpoznávají pouze tečku (.) jako platný oddělovač desetinných míst. Mezi kulturní a analogické analogové funkce patří:  
  
- **Převody, které používají aktuální jazykovou verzi.** `CDbl` `CInt` Funkce a `Format`převádějí číslo na řetězec a funkce a převádějí řetězec na číslo. `CStr`  
  
- **Převody, které používají konkrétní jazykovou verzi.** Každý objekt Number má `ToString(IFormatProvider)` metodu, která převede číslo na řetězec `Parse(String, IFormatProvider)` a metodu, která převede řetězec na číslo. Například `Double` typ <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> poskytuje metody a. <xref:System.Double.ToString%28System.IFormatProvider%29>  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Conversion.Str%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Použití konkrétní jazykové verze  
 Představte si, že vyvíjíte aplikaci, která odesílá datum (formátovaná jako řetězec) webové službě. V takovém případě musí vaše aplikace používat specifickou jazykovou verzi pro převod řetězce. K ilustraci proč zvažte výsledek použití <xref:System.DateTime.ToString> metody Date: Pokud vaše aplikace používá tuto metodu k formátování data 4.2005, vrátí "7/4/2005 12:00:00 dop" při spuštění s jazykovou verzí USA English (EN-US), ale vrátí "04.07.2005 00:00:00" při spuštění s jazykovou verzí němčina (de-DE-DE).  
  
 Pokud potřebujete provést převod řetězce v konkrétním formátu jazykové verze, měli byste použít `CultureInfo` třídu, která je integrována do .NET Framework. Můžete vytvořit nový `CultureInfo` objekt pro konkrétní jazykovou verzi předáním názvu <xref:System.Globalization.CultureInfo.%23ctor%2A> jazykové verze konstruktoru. Podporované názvy jazykové verze jsou uvedeny na stránce <xref:System.Globalization.CultureInfo> s nápovědě třídy.  
  
 Alternativně můžete získat instanci *neutrální jazykové verze* z <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnosti. Invariantní jazyková verze je založena na anglické jazykové verzi, ale existuje několik rozdílů. Například invariantní jazyková verze určuje 24hodinové hodiny místo 12 hodin.  
  
 Chcete-li převést datum na řetězec jazykové verze, předejte <xref:System.Globalization.CultureInfo> objekt <xref:System.DateTime.ToString%28System.IFormatProvider%29> metodě objektu Date. Například následující kód zobrazí "07/04/2005 00:00:00", bez ohledu na nastavení jazykové verze aplikace.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Literály data jsou vždy interpretovány podle anglické jazykové verze.  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Existují dvě důležité situace, kdy je potřeba porovnávání řetězců:  
  
- **Řazení dat pro zobrazení uživateli** Použijte operace založené na aktuální jazykové verzi, aby se odpovídajícím způsobem seřadily řetězce.  
  
- **Určení, zda dvě řetězce interní aplikace odpovídají přesně (typicky pro účely zabezpečení).** Použijte operace, které ignorují aktuální jazykovou verzi.  
  
 Pomocí funkce Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A> můžete provádět oba typy porovnávání. Zadejte nepovinný `Compare` argument pro řízení typu porovnání: `Text` pro většinu vstupů a výstupů `Binary` pro určení přesné shody.  
  
 `StrComp` Funkce vrací celé číslo, které určuje vztah mezi dvěma porovnávaných řetězci na základě pořadí řazení. Kladná hodnota pro výsledek označuje, že první řetězec je větší než druhý řetězec. Záporný výsledek označuje, že první řetězec je menší a nula značí rovnost mezi řetězci.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Můžete také použít .NET Framework partnera `StrComp` funkce <xref:System.String.Compare%2A?displayProperty=nameWithType> , metody. Toto je statická, přetížená metoda základní řetězcové třídy. Následující příklad ukazuje, jak je tato metoda používána:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Pro lepší kontrolu nad tím, jak se provádí porovnávání, můžete použít další přetížení <xref:System.String.Compare%2A> metody. Pomocí metody můžete `comparisonType` použít argument k určení typu porovnání, které se má použít. <xref:System.String.Compare%2A?displayProperty=nameWithType>  
  
|`comparisonType` Hodnota argumentu|Typ porovnání|Kdy je použít|  
|---|---|---|  
|`Ordinal`|Porovnání na základě bajtů součásti řetězce|Tuto hodnotu použijte při porovnávání: Identifikátory rozlišující velká a malá písmena, nastavení související se zabezpečením nebo jiné nelingvistické identifikátory, kde se musí bajty přesně shodovat.|  
|`OrdinalIgnoreCase`|Porovnání na základě bajtů součásti řetězce<br /><br /> `OrdinalIgnoreCase`používá invariantní informace o jazykové verzi k určení, kdy se dva znaky liší pouze velkými písmeny.|Tuto hodnotu použijte při porovnávání: identifikátory bez rozlišení velkých a malých písmen, nastavení týkající se zabezpečení a data uložená v systému Windows.|  
|`CurrentCulture` Nebo `CurrentCultureIgnoreCase`|Porovnání na základě interpretace řetězců v aktuální jazykové verzi.|Při porovnávání použijte tyto hodnoty: data, která se zobrazují uživateli, většinu vstupu uživatele a další data, která vyžadují jazykovou interpretaci.|  
|`InvariantCulture` Nebo `InvariantCultureIgnoreCase`|Porovnání na základě interpretace řetězců v neutrální jazykové verzi.<br /><br /> To se liší od `Ordinal` a `OrdinalIgnoreCase`, protože invariantní jazyková verze zpracovává znaky mimo svůj přijatý rozsah jako ekvivalentní znaky invariant.|Tyto hodnoty použijte pouze při porovnávání trvalých dat nebo zobrazení lingvisticky relevantních dat, která vyžadují pevné pořadí řazení.|  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud vaše aplikace provádí rozhodnutí o zabezpečení na základě výsledku porovnání nebo operace změny velikosti písmen, pak by tato operace měla <xref:System.String.Compare%2A?displayProperty=nameWithType> používat metodu a metodu předat `Ordinal` nebo `OrdinalIgnoreCase` pro `comparisonType` argument.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo>
- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
