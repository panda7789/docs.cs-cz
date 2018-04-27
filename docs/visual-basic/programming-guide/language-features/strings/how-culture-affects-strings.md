---
title: Vliv jazykové verze na řetězce v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c95dcc8d04725f7a072e8c8bc7fe058e53a95c05
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Vliv jazykové verze na řetězce v jazyce Visual Basic
Tato stránka nápovědy popisuje, jak Visual Basic používá provést převod řetězců a porovnávání informací o jazykové verzi.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kdy použít řetězce specifické pro jazykovou verzi  
 By měl obvykle použijte řetězce specifické pro jazykovou verzi pro všechna data prezentovaná a číst od uživatelů a použijte řetězce neutrální jazykovou verzi pro interní data aplikace.  
  
 Například pokud vaše aplikace zobrazí uživatelům zadat datum jako řetězec, očekávat uživatelům řetězce podle jejich jazykovou verzi formátu a aplikace by měl správně převést řetězec. Pokud vaše aplikace se pak uvede datum ve svém uživatelském rozhraní, se musí zobrazit ve jazykovou verzi uživatele.  
  
 Ale pokud aplikace odesílá data do centrální server, měli formátu řetězce podle jeden konkrétní jazykové verzi, aby nedošlo k záměně mezi formáty potenciálně jiné datum.  
  
## <a name="culture-sensitive-functions"></a>Jazykové funkce  
 Všechny funkce Převod řetězce jazyka Visual Basic (s výjimkou `Str` a `Val` funkce) pomocí informací o jazykové verzi aplikace se ujistěte, že převody a porovnání jsou vhodné pro jazykovou verzi aplikace uživatel.  
  
 Klíč k úspěšně pomocí funkcí převod řetězce na aplikace, které běží na počítačích s jinou jazykovou verzi nastavení je pochopit funkcích, které používají nastavení konkrétní jazykové verze a které používají nastavení aktuální jazykové verze. Všimněte si, že nastavení jazykové verze aplikace, ve výchozím nastavení, dědí z nastavení jazykové verze operačního systému. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (Převádí čísla do řetězců) a `Val` funkce (převede řetězců na čísla) při převádění mezi řetězci a čísla nepoužívejte informací o jazykové verzi aplikace. Místo toho budou pouze tečku (.) rozpoznat jako platný oddělovač desetinných míst. Zohledňuje podobných operací těchto funkcí jsou:  
  
-   **Převody, které používají aktuální jazykovou verzi.** `CStr` a `Format` funkce převést na řetězec, číslo a `CDbl` a `CInt` funkce převést řetězec na číslo.  
  
-   **Převody, které používají konkrétní jazykové verze.** Každý objekt číslo má `ToString(IFormatProvider)` metoda, která převádí číslo na řetězec, a `Parse(String, IFormatProvider)` metoda, která převede řetězec na číslo. Například `Double` typ poskytuje <xref:System.Double.ToString%28System.IFormatProvider%29> a <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> metody.  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Conversion.Str%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Pomocí konkrétní jazykové verze  
 Představte si, že vyvíjíte aplikaci, která odesílá data (naformátovaná jako řetězec) k webové službě. V takovém případě musí vaše aplikace používat konkrétní jazykové verze pro převod řetězce. Pro ilustraci důvod, proč, zvažte výsledek pomocí datum <xref:System.DateTime.ToString> metoda: Pokud vaše aplikace používá dané metody k formátování data 4 červenec 2005, vrátí "4/7/2005 12:00:00 AM" spuštění s jazykové verze Angličtina USA (en US), ale vrátí " 04.07.2005 00:00:00 "spuštění s jazykovou verzi němčina (de-DE).  
  
 Pokud potřebujete provést převod řetězce ve formátu konkrétní jazykové verzi, měli byste použít `CultureInfo` třídu, která je integrovaná [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Můžete vytvořit nový `CultureInfo` objekt pro konkrétní jazykové verzi předáním název pro jazykovou verzi <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktor. Názvy jazykové verze jsou uvedeny v <xref:System.Globalization.CultureInfo> stránku nápovědy třídy.  
  
 Alternativně můžete získat instanci *neutrální jazykovou verzi* z <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Neutrální jazykovou verzi je založena na anglické jazykové verzi, ale existují určité rozdíly. Například neutrální jazykovou verzi určuje 24 hodin místo 12 hodin.  
  
 Datum převést na řetězec pro jazykovou verzi, předat <xref:System.Globalization.CultureInfo> objekt k objektu datum <xref:System.DateTime.ToString%28System.IFormatProvider%29> metoda. Například následující kód zobrazí "07/04/2005 00:00:00", bez ohledu na to nastavení jazykové verze aplikace.  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  Date – literály se vždy interpretují podle jazykové verze Angličtina.  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Existují dvě důležité situacích, kde jsou potřeba porovnání řetězců:  
  
-   **Řazení dat pro zobrazení pro uživatele.** Pomocí operace založené na aktuální jazykové verze, takže řetězce seřadit správně.  
  
-   **Zjišťuje se, pokud dva řetězce interní aplikace přesně shodovat (obvykle pro účely zabezpečení).** Pomocí operace, které ignorovat aktuální jazykovou verzi.  
  
 Můžete provádět oba typy porovnání v jazyce Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A> funkce. Zadejte nepovinný `Compare` argument řídit typ porovnání: `Text` pro většinu vstup a výstup `Binary` pro určení přesné shody.  
  
 `StrComp` Funkce vrátí celé číslo, které určuje vztah mezi dvěma porovnání řetězce podle pořadí řazení. Kladné číslo pro výsledek označuje, že první řetězec je větší než druhý řetězec. Záporný výsledek označuje první řetězec je menší, a nula označuje rovnosti mezi řetězce.  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 Můžete také [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] partnera `StrComp` funkce, <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda. Toto je statická, přetížené metoda řetězec základní třídy. Následující příklad ilustruje, jak tato metoda se používá:  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 Pro lepší kontrolu nad jak porovnání se provádí, můžete použít další přetížení <xref:System.String.Compare%2A> metoda. S <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu, můžete použít `comparisonType` argument určit typ porovnání používat.  
  
|Hodnota `comparisonType` argument|Typ porovnání|Kdy použít|  
|---|---|---|  
|`Ordinal`|Porovnání podle bajtů řetězce se součástí.|Tuto hodnotu použijte, pokud porovnávání: malá a velká písmena identifikátorů, nastavení související se zabezpečením nebo dalších mimo jazykových identifikátorů kde bajtů musí přesně shodovat.|  
|`OrdinalIgnoreCase`|Porovnání podle bajtů řetězce se součástí.<br /><br /> `OrdinalIgnoreCase` používá informace neutrální jazykovou verzi pro určení, kdy dva znaky se liší pouze ve velkých písmen.|Tuto hodnotu použijte, pokud porovnávání: velká a malá písmena identifikátorů, související se zabezpečením nastavení a data uložená v systému Windows.|  
|`CurrentCulture` Nebo `CurrentCultureIgnoreCase`|Porovnání podle interpretace na řetězce v aktuální jazykovou verzi.|Při porovnávání používají tyto hodnoty: data, která se zobrazí uživateli, většina vstup uživatele a další data, která vyžaduje lingvistické interpretace.|  
|`InvariantCulture` Nebo `InvariantCultureIgnoreCase`|Porovnání podle interpretace na řetězce v neutrální jazykovou verzi.<br /><br /> Liší se od `Ordinal` a `OrdinalIgnoreCase`, protože neutrální jazykovou verzi považuje za odpovídající invariantní znaky znaky mimo jeho přijatém rozsahu.|Tyto hodnoty použijte, pouze při porovnávání zachování dat nebo zobrazování jazykově relevantní data, která vyžaduje pevnou řazení.|  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud vaše aplikace provede rozhodnutí o zabezpečení na základě výsledku porovnání nebo operace změny velikosti písmen, pak by měl použít operaci <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda a předejte jí `Ordinal` nebo `OrdinalIgnoreCase` pro `comparisonType` argument.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.CultureInfo>  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
