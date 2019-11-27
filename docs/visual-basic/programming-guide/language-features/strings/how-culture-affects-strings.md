---
title: Vliv jazykové verze na řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 2520a7684b8710abd949543e3f17f77d3c631d22
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352469"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Vliv jazykové verze na řetězce v jazyce Visual Basic
Tato stránka HELP popisuje, jak Visual Basic používá informace o jazykové verzi k provádění převodů a porovnávání řetězců.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kdy použít řetězce specifické pro jazykovou verzi  
 Obvykle byste měli použít řetězce specifické pro jazykovou verzi pro všechna data, která jsou zobrazena a čtena uživateli, a používat pro interní data vaší aplikace neutrální řetězce jazykové verze.  
  
 Například pokud vaše aplikace požaduje, aby uživatel zadal datum jako řetězec, měl by očekávat, že uživatelé budou formátovat řetězce podle jejich kultury a aplikace by měla odpovídajícím způsobem převést řetězec. Pokud vaše aplikace následně uvede toto datum v uživatelském rozhraní, měla by být uvedena v jazykové verzi uživatele.  
  
 Pokud však aplikace nahraje datum na centrální server, měl by formátovat řetězec podle jedné konkrétní jazykové verze, aby nedocházelo k záměně mezi potenciálně odlišnými formáty data.  
  
## <a name="culture-sensitive-functions"></a>Funkce závislé na jazykové verzi  
 Všechny funkce Visual Basicho převodu řetězce (s výjimkou funkcí `Str` a `Val`) používají informace o jazykové verzi aplikace k zajištění, že převody a porovnávání jsou vhodné pro jazykovou verzi uživatele aplikace.  
  
 Klíč k úspěšnému použití funkcí pro převod řetězců v aplikacích, které jsou spuštěny v počítačích s různými nastaveními jazykové verze, je pochopit, které funkce používají konkrétní nastavení jazykové verze a které používají aktuální nastavení jazykové verze. Všimněte si, že nastavení jazykové verze aplikace je ve výchozím nastavení zděděné z nastavení jazykové verze operačního systému. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (převede čísla na řetězce) a `Val` (převede řetězce na čísla) funkce při převodu mezi řetězci a čísly nepoužívají jazykové verze aplikace. Místo toho rozpoznávají pouze tečku (.) jako platný oddělovač desetinných míst. Mezi kulturní a analogické analogové funkce patří:  
  
- **Převody, které používají aktuální jazykovou verzi.** Funkce `CStr` a `Format` převádějí číslo na řetězec a funkce `CDbl` a `CInt` převádějí řetězec na číslo.  
  
- **Převody, které používají konkrétní jazykovou verzi.** Každý objekt Number má `ToString(IFormatProvider)` metodu, která převede číslo na řetězec a metodu `Parse(String, IFormatProvider)`, která převede řetězec na číslo. Například typ `Double` poskytuje metody <xref:System.Double.ToString%28System.IFormatProvider%29> a <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>.  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Conversion.Str%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Použití konkrétní jazykové verze  
 Představte si, že vyvíjíte aplikaci, která odesílá datum (formátovaná jako řetězec) webové službě. V takovém případě musí vaše aplikace používat specifickou jazykovou verzi pro převod řetězce. K ilustraci, proč zvažte výsledek použití <xref:System.DateTime.ToString> metody data: Pokud vaše aplikace používá tuto metodu k formátování data 4. července 2005, vrátí "7/4/2005 12:00:00 AM" při spuštění s jazykovou verzí USA English (EN-US), ale vrátí "04.07.2005 00:00:00" při spuštění s jazykovou verzí němčina (de-DE-DE).  
  
 Pokud potřebujete provést převod řetězce v konkrétní jazykové verzi, měli byste použít třídu `CultureInfo`, která je integrována do .NET Framework. Můžete vytvořit nový objekt `CultureInfo` pro konkrétní jazykovou verzi předáním názvu jazykové verze do konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%2A>. Podporované názvy jazykové verze jsou uvedeny na stránce s technickou podporou pro <xref:System.Globalization.CultureInfo> třídy.  
  
 Alternativně můžete získat instanci *neutrální jazykové verze* z vlastnosti <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Invariantní jazyková verze je založena na anglické jazykové verzi, ale existuje několik rozdílů. Například invariantní jazyková verze určuje 24hodinové hodiny místo 12 hodin.  
  
 Chcete-li převést datum na řetězec jazykové verze, předejte objekt <xref:System.Globalization.CultureInfo> do metody <xref:System.DateTime.ToString%28System.IFormatProvider%29> objektu Date. Například následující kód zobrazí "07/04/2005 00:00:00", bez ohledu na nastavení jazykové verze aplikace.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Literály data jsou vždy interpretovány podle anglické jazykové verze.  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Existují dvě důležité situace, kdy je potřeba porovnávání řetězců:  
  
- **Řazení dat pro zobrazení uživateli** Použijte operace založené na aktuální jazykové verzi, aby se odpovídajícím způsobem seřadily řetězce.  
  
- **Určení, zda dvě řetězce interní aplikace odpovídají přesně (typicky pro účely zabezpečení).** Použijte operace, které ignorují aktuální jazykovou verzi.  
  
 Můžete provést oba typy porovnávání pomocí funkce Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A>. Zadejte volitelný `Compare` argument pro kontrolu typu porovnání: `Text` pro většinu vstupních a výstupních `Binary` pro určení přesné shody.  
  
 Funkce `StrComp` vrací celé číslo, které označuje vztah mezi dvěma porovnávaných řetězci na základě pořadí řazení. Kladná hodnota pro výsledek označuje, že první řetězec je větší než druhý řetězec. Záporný výsledek označuje, že první řetězec je menší a nula značí rovnost mezi řetězci.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Můžete také použít .NET Framework partnera funkce `StrComp`, <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda. Toto je statická, přetížená metoda základní řetězcové třídy. Následující příklad ukazuje, jak je tato metoda používána:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Pro lepší kontrolu nad tím, jak se provádí porovnávání, můžete použít další přetížení metody <xref:System.String.Compare%2A>. Pomocí metody <xref:System.String.Compare%2A?displayProperty=nameWithType> lze použít argument `comparisonType` k určení typu porovnání, které se má použít.  
  
|Hodnota pro `comparisonType` argument|Typ porovnání|Kdy je použít|  
|---|---|---|  
|`Ordinal`|Porovnání na základě bajtů součásti řetězce|Tuto hodnotu použijte při porovnávání: Identifikátory rozlišující velká a malá písmena, nastavení související se zabezpečením nebo jiné nelingvistické identifikátory, kde se musí bajty přesně shodovat.|  
|`OrdinalIgnoreCase`|Porovnání na základě bajtů součásti řetězce<br /><br /> `OrdinalIgnoreCase` používá invariantní informace o jazykové verzi k určení, kdy se dva znaky liší pouze velkými písmeny.|Tuto hodnotu použijte při porovnávání: identifikátory bez rozlišení velkých a malých písmen, nastavení týkající se zabezpečení a data uložená v systému Windows.|  
|`CurrentCulture` nebo `CurrentCultureIgnoreCase`|Porovnání na základě interpretace řetězců v aktuální jazykové verzi.|Při porovnávání použijte tyto hodnoty: data, která se zobrazují uživateli, většinu vstupu uživatele a další data, která vyžadují jazykovou interpretaci.|  
|`InvariantCulture` nebo `InvariantCultureIgnoreCase`|Porovnání na základě interpretace řetězců v neutrální jazykové verzi.<br /><br /> To se liší od `Ordinal` a `OrdinalIgnoreCase`, protože invariantní jazyková verze považuje znaky mimo přijatý rozsah za ekvivalentní znaky invariant.|Tyto hodnoty použijte pouze při porovnávání trvalých dat nebo zobrazení lingvisticky relevantních dat, která vyžadují pevné pořadí řazení.|  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud vaše aplikace provádí rozhodnutí o zabezpečení na základě výsledku porovnání nebo operace změny velikosti písmen, musí operace použít metodu <xref:System.String.Compare%2A?displayProperty=nameWithType> a předat `Ordinal` nebo `OrdinalIgnoreCase` pro `comparisonType` argument.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo>
- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
