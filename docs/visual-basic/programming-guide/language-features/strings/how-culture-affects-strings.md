---
title: Vliv jazykové verze na řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834618"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Vliv jazykové verze na řetězce v jazyce Visual Basic
Tato stránka nápovědy popisuje, jak jazyka Visual Basic používá informace o jazykové verzi provádět převody řetězce a porovnávání řetězců.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kdy použít řetězců specifické pro jazykovou verzi  
 By obvykle řetězce specifické pro jazykovou verzi použít pro všechna data budou zobrazovat a číst od uživatelů a použít invariantní jazyková verze řetězce pro interní data vaší aplikace.  
  
 Pokud vaše aplikace zobrazí uživatelé zadat datum jako řetězec, očekávat uživatelé k formátování řetězce podle jeho jazykovou verzi a aplikace by měla odpovídajícím způsobem převést řetězec. Pokud vaše aplikace se pak zobrazí data ve svém uživatelském rozhraní, se by se měl prokázat v jazykové verzi uživatele.  
  
 Nicméně pokud aplikace odešle data do centrálního serveru, by měl formátu řetězce podle jeden konkrétní jazykovou verzi, aby se zabránilo záměny potenciálně různé formáty.  
  
## <a name="culture-sensitive-functions"></a>Jazykové funkce  
 Všechny funkce pro převod řetězců jazyka Visual Basic (s výjimkou `Str` a `Val` funkce) ujistěte se, že převod a porovnání jsou vhodné pro jazykovou verzi vaší aplikace pomocí informací o jazykové verzi aplikace uživatel.  
  
 Klíčem k úspěšně pomocí funkce pro převod řetězců v aplikacích, které běží na počítačích s nastavením jinou jazykovou verzi je pochopit, které funkce pomocí konkrétní jazykové verze nastavení a nastavení aktuální jazykové verze, která použít. Všimněte si, že nastavení jazykové verze aplikace se ve výchozím nastavení, dědí z nastavení jazykové verze operačního systému. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (Převádí čísla na řetězce) a `Val` (převede řetězců na čísla) funkce nepoužívejte informace o jazykové verzi aplikace, když převod mezi řetězci a čísla. Místo toho jsou pouze tečkou (.) rozpoznán jako platný oddělovač desetinných míst. V kulturách s ohledem na analogy z těchto funkcí jsou:  
  
-   **Převody, které používají aktuální jazykovou verzi.** `CStr` a `Format` funkcí převede číslo na řetězec a `CDbl` a `CInt` funkce převádějí řetězec na číslo.  
  
-   **Převody, které používají konkrétní jazykovou verzi.** Má každé číslo objekt `ToString(IFormatProvider)` metodu, která převede číslo na řetězec a `Parse(String, IFormatProvider)` metodu, která převede řetězec na číslo. Například `Double` typ poskytuje <xref:System.Double.ToString%28System.IFormatProvider%29> a <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> metody.  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Conversion.Str%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Pomocí konkrétní jazykové verze  
 Představte si, že vyvíjíte aplikaci, která odesílá data (naformátovaná jako řetězec) k webové službě. V takovém případě musí aplikace použít konkrétní jazykovou verzi pro převod řetězce. Pro ilustraci, důvod, proč, vezměte v úvahu výsledek použití datum <xref:System.DateTime.ToString> metody: Pokud vaše aplikace používá k formátování data 4. července 2005, tato metoda vrátí "7/4/2005 12:00:00 AM" při spuštění pomocí jazykové verze Angličtina-Spojené státy (en US), ale vrátí "04.07.2005 00:00:00" při spuštění s němčina (de-DE) jazykovou verzi.  
  
 Když potřebujete provést konverzi na řetězec ve formátu konkrétní jazykové verze, byste měli použít `CultureInfo` třídu, která je integrovaná [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Můžete vytvořit nový `CultureInfo` pro konkrétní jazykovou verzi předáním název pro jazykovou verzi <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktoru. Názvy podporované jazykové verze jsou uvedeny v <xref:System.Globalization.CultureInfo> třídy stránku nápovědy.  
  
 Alternativně můžete získat instanci *invariantní jazyková verze* z <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Neutrální jazykové verze je založená na anglické jazykové verzi, ale existují určité rozdíly. Například určuje neutrální jazykové verze 24hodinový formát místo 12 hodin.  
  
 Datum převést na řetězec pro jazykovou verzi, předejte <xref:System.Globalization.CultureInfo> do objektu date <xref:System.DateTime.ToString%28System.IFormatProvider%29> metoda. Například následující kód zobrazí "07/04/2005 00:00:00", bez ohledu na nastavení jazykové verze vaší aplikace.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Date – literály jsou vždy interpretováno podle jazykové verze Angličtina.  
  
## <a name="comparing-strings"></a>Porovnávání řetězců  
 Existují dvě důležité situace, kde jsou potřeba porovnávání řetězců:  
  
-   **Řazení dat v zobrazení pro uživatele.** Použití operací na základě aktuální jazykovou verzi tak řazení řetězců odpovídajícím způsobem.  
  
-   **Určení, pokud dva řetězce interní aplikace přesně odpovídat (obvykle pro účely zabezpečení).** Pomocí operace, které ignorovat aktuální jazykové verze.  
  
 Oba typy porovnání s jazykem Visual Basic můžete provádět <xref:Microsoft.VisualBasic.Strings.StrComp%2A> funkce. Zadejte nepovinný `Compare` argument řídit typ porovnání: `Text` pro většinu vstupů a výstupů `Binary` pro určení přesné shody.  
  
 `StrComp` Funkce vrátí celé číslo, které označuje vztah mezi dvěma porovnání řetězce podle pořadí řazení. Kladnou hodnotu pro výsledek označuje, zda je první řetězec větší než druhý řetězec. Záporný výsledek označuje první řetězec, který je menší a nula znamená rovnost řetězců.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Můžete také použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] partner `StrComp` funkce, <xref:System.String.Compare%2A?displayProperty=nameWithType> metody. Toto je statické, přetížené metody třídy base řetězec. Následující příklad ukazuje, jak tato metoda se používá:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Pro lepší kontrolu nad jak porovnání se provádí, můžete použít další přetížení <xref:System.String.Compare%2A> metody. S <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu, můžete použít `comparisonType` argument určit typ porovnání, které se použít.  
  
|Hodnota pro `comparisonType` argument|Typ porovnání|Kdy je použít|  
|---|---|---|  
|`Ordinal`|Porovnání podle bajtů součást řetězců.|Tuto hodnotu použijte, pokud porovnávání: malá a velká písmena identifikátorů, nastavení související se zabezpečením nebo jiné nejazykové identifikátory, kde počet bajtů se musí přesně shodovat.|  
|`OrdinalIgnoreCase`|Porovnání podle bajtů součást řetězců.<br /><br /> `OrdinalIgnoreCase` používá invariantní jazyková verze informace k určení, kdy dva znaky se liší pouze velikostí malá a velká písmena.|Tuto hodnotu použijte, pokud porovnávání: malá a velká písmena identifikátorů, bezpečnostních nastavení a data uložená ve Windows.|  
|`CurrentCulture` Nebo `CurrentCultureIgnoreCase`|Porovnání podle interpretace řetězců v aktuální jazykové verze.|Použijte tyto hodnoty při porovnání: data, která se zobrazí uživateli, většina vstup uživatele a další data, která vyžaduje lingvistické výkladu.|  
|`InvariantCulture` Nebo `InvariantCultureIgnoreCase`|Porovnání podle interpretace řetězců v invariantní jazykové verzi.<br /><br /> To se liší od `Ordinal` a `OrdinalIgnoreCase`, protože invariantní jazyková verze považuje za znaky mimo rozsah přijatelných ekvivalentní invariantní znaků.|Tyto hodnoty použijte jen při porovnávání trvalá data nebo zobrazení lingvistických relevantní data, která vyžaduje pevnou řazení.|  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud vaše aplikace provádí rozhodnutí o zabezpečení založeno na výsledku porovnání nebo operaci změny velikosti písmen, pak by měl použít operaci <xref:System.String.Compare%2A?displayProperty=nameWithType> a předáte `Ordinal` nebo `OrdinalIgnoreCase` pro `comparisonType` argument.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo>
- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
