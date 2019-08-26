---
title: Třídy znaků v regulárních výrazech .NET
description: Naučte se, jak používat třídy znaků k reprezentaci sady znaků v regulárních výrazech .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 53dcbcfdcc9a8d04840bc91a563b6514153b9577
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963434"
---
# <a name="character-classes-in-regular-expressions"></a>Třídy znaků v regulárních výrazech

Třída znaků definuje množinu znaků, přičemž kterýkoli z nich se může vyskytovat ve vstupním řetězci tak, aby došlo ke shodě. Jazyk regulárních výrazů v rozhraní .NET podporuje následující třídy znaků:  
  
- Skupiny pozitivních znaků. Znak ve vstupním řetězci musí odpovídat jedné ze zadaných množin znaků. Další informace naleznete v tématu [Skupina pozitivních znaků](#PositiveGroup).  
  
- Skupiny negativních znaků. Znak ve vstupním řetězci nesmí odpovídat jedné ze zadaných množin znaků. Další informace naleznete v tématu [Skupina negativních znaků](#NegativeGroup).  
  
- Libovolný znak. Znak (tečka nebo tečka) v regulárním výrazu je zástupný znak, který odpovídá jakémukoli znaku s výjimkou `\n`. `.` Další informace naleznete v tématu [libovolný znak](#AnyCharacter).  
  
- Obecná kategorie nebo pojmenovaný blok sady Unicode. Pro úspěšné vyhledání shody musí být znak ve vstupním řetězci členem určité kategorie sady Unicode nebo musí spadat do souvislého rozsahu znaků sady Unicode. Další informace najdete v tématu [Kategorie sady Unicode nebo blok sady Unicode](#CategoryOrBlock).  
  
- Negativní obecná kategorie nebo pojmenovaný blok sady Unicode. Pro úspěšné vyhledání shody nesmí být znak ve vstupním řetězci členem určité kategorie sady Unicode ani nesmí spadat do souvislého rozsahu znaků sady Unicode. Další informace naleznete v tématu [negativní kategorie sady Unicode nebo blok sady Unicode](#NegativeCategoryOrBlock).  
  
- Znak slova. Znak ve vstupním řetězci může patřit do kterékoli kategorie sady Unicode, která je vhodná pro znaky ve slovech. Další informace naleznete v tématu [slovní znak](#WordCharacter).  
  
- Mimoslovní znak. Znak ve vstupním řetězci může patřit do jakékoli kategorie sady Unicode, která není znakem slova. Další informace naleznete v tématu [jiný znak než Word](#NonWordCharacter).  
  
- Prázdný znak. Znakem ve vstupním řetězci může být jakýkoli oddělovací znak sady Unicode nebo některý z mnoha řídicích znaků. Další informace naleznete v tématu [prázdný znak](#WhitespaceCharacter).  
  
- Neprázdný znak. Znakem ve vstupním řetězci může být libovolný znak, který není prázdným znakem. Další informace naleznete v tématu [jiný než prázdný znak](#NonWhitespaceCharacter).  
  
- Desítková číslice. Znakem ve vstupním řetězci může být kterýkoli ze znaků, který je klasifikován jako desítková číslice sady Unicode. Další informace naleznete v tématu [znak desítkové číslice](#DigitCharacter).  
  
- Nedesetinné číslo. Znakem ve vstupním řetězci může být jakýkoli jiný znak než desítková číslice sady Unicode. Další informace naleznete v tématu [znak desítkové číslice](#NonDigitCharacter).  
  
 Rozhraní .NET podporuje výrazy odčítání tříd znaků, které umožňují definovat sadu znaků jako výsledek vyloučení jedné třídy znaků z jiné třídy znaků. Další informace naleznete v tématu [odčítání třídy znaků](#CharacterClassSubtraction).  
  
> [!NOTE]
> Třídy znaků, které odpovídají znakům podle kategorie, jako je například [\w](#WordCharacter) pro porovnávání znaků Wordu nebo [\p{} ](#CategoryOrBlock) , aby odpovídaly kategorii <xref:System.Globalization.CharUnicodeInfo> sady Unicode, spoléhají na třídu k poskytnutí informací o kategoriích znaků.  Počínaje .NET Framework 4.6.2 jsou kategorie znaků založené na [standardu Unicode, verze 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). V .NET Framework 4 až do .NET Framework 4.6.1 jsou založené na [standardu Unicode verze 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>Skupina pozitivních znaků: []  
 Skupina pozitivních znaků určuje seznam znaků, které se mohou objevit ve vstupním řetězci, aby nastala shoda. Tento seznam znaků může být zadán jako jednotlivé znaky, jako rozsah nebo obojí.  
  
 Syntaxe pro určení seznamu jednotlivých znaků je následující:  

```  
[*character_group*]  
```

 kde *character_group* je seznam jednotlivých znaků, které se mohou objevit ve vstupním řetězci, aby byla shoda úspěšná. Třída *character_group* se může skládat z jakékoli kombinace jednoho nebo více literálních znaků, [řídicích znaků](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)nebo tříd znaků.  
  
 Syntaxe pro zadání rozsahu znaků je následující:  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 kde *firstCharacter* je znak, který začíná rozsah a *lastCharacter* je znak, který ukončuje rozsah. Rozsah znaků je souvislá řada znaků definovaná zadáním prvního znaku v řadě, spojovníku (-) a posledního znaku v řadě. Dva znaky jsou souvislé, pokud mají sousedící kódové body sady Unicode. *firstCharacter* musí být znak s nižším bodem kódu a *lastCharacter* musí být znak s vyšším bodem kódu.

> [!NOTE]
> Vzhledem k tomu, že skupina pozitivních znaků může zahrnovat jak množinu znaků, tak i rozsah znaků,`-`znak spojovníku () je vždy interpretován jako oddělovač rozsahu, pokud se nejedná o první nebo poslední znak skupiny.

Některé běžné vzory regulárních výrazů, které obsahují pozitivní třídy znaků, jsou uvedeny v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`[aeiou]`|Porovná se všemi samohláskami.|  
|`[\p{P}\d]`|Porovná se všemi interpunkčními znaky a znaky desítkových číslic.|  
|`[\s\p{P}]`|Porovnává všechny prázdné znaky a interpunkční znaménka.|  
  
 V následujícím příkladu je definována skupina pozitivních znaků obsahující znaky „a“ a „e“ tak, že vstupní řetězec musí obsahovat slovo „grey“ nebo „gray“ následované jiným slovem, aby došlo ke shodě.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 Regulární výraz `gr[ae]y\s\S+?[\s|\p{P}]` je definován následujícím způsobem:  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`gr`|Porovná s literálními znaky „gr“.|  
|`[ae]`|Porovná buď se znakem „a“, nebo s „e“.|  
|`y\s`|Porovná s literálním znakem „y“ následovaným prázdným znakem.|  
|`\S+?`|Porovná s jedním nebo několika neprázdnými znaky, avšak s co nejmenším počtem.|  
|`[\s\p{P}]`|Porovná s prázdným znakem nebo se znakem interpunkčního znaménka.|  
  
 V následujícím příkladu jsou vyhledána slova začínající kterýmkoli velkým písmenem. Pomocí dílčího výrazu `[A-Z]` představuje rozsah velkých písmen od A do Z.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Regulární výraz `\b[A-Z]\w*\b` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Porovná s libovolným znakem velkého písmene od A až do Z.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Porovná hranici slova.|  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a>Skupina negativních znaků: [^]  
 Skupina negativních znaků určuje seznam znaků, které se nesmí objevit ve vstupním řetězci, aby došlo ke shodě. Seznam znaků může být zadán jako jednotlivé znaky, jako rozsah nebo obojí.  
  
Syntaxe pro určení seznamu jednotlivých znaků je následující:  

```
[*^character_group*]  
```

 kde *character_group* je seznam jednotlivých znaků, které nemohou být zobrazeny ve vstupním řetězci, aby byla shoda úspěšná. Třída *character_group* se může skládat z jakékoli kombinace jednoho nebo více literálních znaků, [řídicích znaků](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)nebo tříd znaků.  
  
 Syntaxe pro zadání rozsahu znaků je následující:  

```
[^*firstCharacter*-*lastCharacter*]  
```

kde *firstCharacter* je znak, který začíná rozsah a *lastCharacter* je znak, který ukončuje rozsah. Rozsah znaků je souvislá řada znaků definovaná zadáním prvního znaku v řadě, spojovníku (-) a posledního znaku v řadě. Dva znaky jsou souvislé, pokud mají sousedící kódové body sady Unicode. *firstCharacter* musí být znak s nižším bodem kódu a *lastCharacter* musí být znak s vyšším bodem kódu.

> [!NOTE]
> Vzhledem k tomu, že skupina negativních znaků může zahrnovat množinu znaků a rozsah znaků, znak spojovníku`-`() je vždy interpretován jako oddělovač rozsahu, pokud se nejedná o první nebo poslední znak skupiny.
  
 Mohou být spojeny dva nebo více rozsahů znaků. Například pro určení rozsahu desítkových číslic od "0" až "9", rozsahu malých písmen od "a" až po "f" a rozsahu velkých písmen od "A" až po "F", použijte `[0-9a-fA-F]`.  
  
 Přední kosočtverce znak (`^`) v záporné skupině znaků je povinný a označuje, že skupina znaků je skupina negativních znaků, nikoli skupina pozitivních znaků.  
  
> [!IMPORTANT]
> Skupina negativních znaků ve větším vzoru regulárního výrazu není kontrolní výraz nulové šířky. To znamená, že po vyhodnocení skupiny negativních znaků modul regulárních výrazů postoupí o jeden znak ve vstupním řetězci.  
  
 Některé běžné vzory regulárních výrazů, které obsahují skupiny negativních znaků, jsou uvedeny v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`[^aeiou]`|Porovná se všemi znaky kromě samohlásek.|  
|`[^\p{P}\d]`|Porovná se všemi znaky kromě interpunkčních znaků a znaků desítkových číslic.|  
  
 Následující příklad porovná libovolné slovo, které začíná znaky „th“ a nenásleduje je „o“.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 Regulární výraz `\bth[^o]\w+\b` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`th`|Porovná s literálními znaky „th“.|  
|`[^o]`|Porovná s libovolným znakem, který není „o“.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Skončí na hranici slova.|  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>Libovolný znak:.  
 Znak tečky (.) odpovídá jakémukoli znaku kromě `\n` (znak nového řádku, \u000A), s následujícími dvěma kvalifikacemi:  
  
- Pokud je <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> vzor regulárního výrazu upraven možností nebo pokud část vzoru, který `.` obsahuje `s` třídu znaků, je upravena možností, `.` odpovídá jakémukoli znaku. Další informace najdete v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
     Následující příklad ilustruje různé chování `.` třídy znaků ve výchozím nastavení a <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> s možností. Regulární výraz `^.+` začíná na začátku řetězce a odpovídá každému znaku. Ve výchozím nastavení porovnávání končí na konci prvního řádku; vzorek regulárního výrazu se shoduje se znakem `\r` návratu na začátek řádku nebo \u000D, ale `\n`neodpovídá. Vzhledem k tomu, že `\n` možnostinterpretujecelývstupnířetězecjakojedinýřádek,odpovídákaždémuznakuvevstupnímřetězci,včetně.<xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> Vzhledem k `\n` `.` tomu, že odpovídá jakémukoli znaku s výjimkou, `\r` Třída znaků odpovídá také (znak návratu na začátek řádku, \u000D).  
  
- Ve skupině pozitivních nebo negativních znaků je tečka považována za literální znak tečky a nikoli za třídu znaků. Další informace naleznete v části [Skupina pozitivních znaků](#PositiveGroup) a [Skupina negativních znaků](#NegativeGroup) dříve v tomto tématu. Následující příklad poskytuje ilustraci definováním regulárního výrazu, který obsahuje znak tečky (`.`) jako třídu znaků a jako člen skupiny pozitivních znaků. Regulární výraz `\b.*[.?!;:](\s|\z)` začíná na hranici slova, odpovídá jakémukoli znaku, dokud se neobjeví v jednom z pěti interpunkčních znamének, včetně tečky, a pak odpovídá buď prázdnému znaku, nebo konci řetězce.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> Vzhledem k tomu, že odpovídá jakémukoli `.` znaku, prvek jazyka se často používá s opožděným kvantifikátorem, pokud se vzor regulárního výrazu pokusí porovnat libovolný znak několikrát. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Kategorie sady Unicode nebo blok sady Unicode: \p{}  
 Standard Unicode přiřadí každému znaku obecnou kategorii. Konkrétní znak může být například `Lu` velké písmeno (reprezentované kategorií), desítková číslice `Nd` (kategorie), matematický symbol ( `Sm` kategorie `Zl` ) nebo oddělovač odstavců (kategorie). Určité množiny znaků sady Unicode zabírají také určité oblasti nebo bloky po sobě následujících bodů kódu. Například množina znaků základní Latinky se nalézá od \u0000 až do \u007F, zatímco množina znaků Arabštiny se nalézá od \u0600 až do \u06FF.  
  
 Konstrukce regulárního výrazu  
  
 `\p{`*název*`}`  
  
 odpovídá jakémukoli znaku, který patří do obecné kategorie sady Unicode nebo pojmenovaného bloku, kde *Name* je zkratka kategorie nebo název pojmenovaného bloku. Seznam zkratek kategorií najdete v části [podporované obecné kategorie sady Unicode](#SupportedUnicodeGeneralCategories) dále v tomto tématu. Seznam pojmenovaných bloků najdete v části [podporované pojmenované bloky](#SupportedNamedBlocks) dále v tomto tématu.  
  
 V následujícím příkladu se používá `\p{`konstrukce *Name* `}` , aby se shodovala s obecnou kategorií Unicode (v tomto `Pd`případě se jedná o kategorii, nebo interpunkční znaménka `IsGreek` , pomlčka) `IsBasicLatin` a pojmenovaný blok (a s názvem. bloky).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 Regulární výraz `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`\p{IsGreek}+`|Porovná jeden nebo více znaků řecké abecedy.|  
|`(\s)?`|Porovná žádný nebo jeden prázdný znak.|  
|`(\p{IsGreek}+(\s)?)+`|Porovná vzorek jednoho nebo více znaků řecké abecedy následovaný žádným nebo jedním prázdným znakem jednou nebo vícekrát.|  
|`\p{Pd}`|Porovná se znakem interpunkce, svislé čáry.|  
|`\s`|Porovná prázdný znak.|  
|`\p{IsBasicLatin}+`|Porovná s jedním nebo více znaky základní Latinky.|  
|`(\s)?`|Porovná žádný nebo jeden prázdný znak.|  
|`(\p{IsBasicLatin}+(\s)?)+`|Porovná vzor jednoho nebo více znaků základní Latinky následovaný žádným nebo jedním prázdným znakem jednou nebo vícekrát.|  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a>Negativní kategorie sady Unicode nebo blok sady Unicode: \p{}  
 Standard Unicode přiřadí každému znaku obecnou kategorii. Konkrétní znak může být například `Lu` velké písmeno (reprezentované kategorií), desítková číslice `Nd` (kategorie), matematický symbol ( `Sm` kategorie `Zl` ) nebo oddělovač odstavců (kategorie). Určité množiny znaků sady Unicode zabírají také určité oblasti nebo bloky po sobě následujících bodů kódu. Například množina znaků základní Latinky se nalézá od \u0000 až do \u007F, zatímco množina znaků Arabštiny se nalézá od \u0600 až do \u06FF.  
  
 Konstrukce regulárního výrazu  
  
 `\P{`*název*`}`  
  
 odpovídá jakémukoli znaku, který nepatří do obecné kategorie sady Unicode nebo pojmenovaného bloku, kde *Name* je zkratka kategorie nebo název pojmenovaného bloku. Seznam zkratek kategorií najdete v části [podporované obecné kategorie sady Unicode](#SupportedUnicodeGeneralCategories) dále v tomto tématu. Seznam pojmenovaných bloků najdete v části [podporované pojmenované bloky](#SupportedNamedBlocks) dále v tomto tématu.  
  
 V následujícím příkladu je použita `\P{`konstrukce *názvu* `}` pro odebrání libovolných `Sc`symbolů měny (v tomto případě symbol, nebo, kategorie měny) z číselných řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Vzor `(\P{Sc})+` regulárního výrazu porovnává jeden nebo více znaků, které nejsou symboly měny; efektivně odříznout libovolný symbol měny z výsledného řetězce.  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>Znak slova: \w  
 `\w`odpovídá jakémukoli znaku slova. Znak slova je členem každé kategorie sady Unicode uvedených v následující tabulce.  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|Ll|písmeno, malé písmeno|  
|Lu|písmeno, velké písmeno|  
|Lt|písmeno, velké počáteční písmeno|  
|Lo|písmeno, jiné|  
|Lm|písmeno, modifikátor|  
|Mn|značka, bez mezer|  
|Nd|číslo, desítková číslice|  
|Pc|interpunkce, spojka. Tato kategorie zahrnuje deset znaků, z nichž nejčastěji používaný je LOWLINE znak (_), u+005F.|  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\w` je `[a-zA-Z_0-9]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Vzhledem k tomu, že odpovídá jakémukoli znaku `\w` slova, prvek jazyka se často používá s opožděným kvantifikátorem, pokud se vzor regulárního výrazu pokusí vyhledat libovolný slovní znak několikrát, následovaný určitým znakem slova. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Následující příklad používá `\w` prvek jazyka pro spárování duplicitních znaků ve slově. Příklad definuje vzor `(\w)\1`regulárního výrazu, který lze interpretovat následujícím způsobem.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|(\w)|Porovnává znak slova. Toto je první zachytávající skupina.|  
|\1|Porovnává hodnotu prvního zachycení.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>Znak jiný než Word: \w  
 `\W`odpovídá jakémukoli znaku, který není znakem slova. Prvek jazyka \W je ekvivalentní s následující třídou znaků:  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 Jinými slovy, odpovídá jakémukoli znaku kromě těch v kategoriích Unicode uvedených v následující tabulce.  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|Ll|písmeno, malé písmeno|  
|Lu|písmeno, velké písmeno|  
|Lt|písmeno, velké počáteční písmeno|  
|Lo|písmeno, jiné|  
|Lm|písmeno, modifikátor|  
|Mn|značka, bez mezer|  
|Nd|číslo, desítková číslice|  
|Pc|interpunkce, spojka. Tato kategorie zahrnuje deset znaků, z nichž nejčastěji používaný je LOWLINE znak (_), u+005F.|  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\W` je `[^a-zA-Z_0-9]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Vzhledem k tomu, že odpovídá jakémukoli neslovnímu `\W` znaku, prvek jazyka se často používá s opožděným kvantifikátorem, pokud se vzor regulárního výrazu pokusí vyhledat libovolný neslovní znak několikrát následovaný určitým znakem, který není slovní. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Následující příklad ilustruje `\W` třídu znaků.  Definuje vzor `\b(\w+)(\W){1,2}`regulárního výrazu, který se shoduje se slovem, za kterým následuje jeden nebo dva jiné znaky než slova, například prázdný znak nebo interpunkční znaménko. Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\b|Začne porovnání na hranici slova.|  
|(\w+)|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|(\W){1,2}|Porovnává s mimoslovním znakem jednou nebo dvakrát. Toto je druhá zachytávající skupina.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 Vzhledem k tomu, že <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> objektprodruhouzachytávajícískupinuobsahujepouzejedenzachycenýznak,kterýneníslovní,příkladnačtevšechnyzachycenénewordovéznakyzobjektu,který<xref:System.Text.RegularExpressions.Group> je vrácen vlastností.  
  
<a name="WhitespaceCharacter"></a>   
## <a name="whitespace-character-s"></a>Prázdný znak: \s  
 `\s`odpovídá jakémukoli prázdnému znaku. Je ekvivalentní s uvozovacími sekvencemi a kategoriemi sady Unicode, které jsou uvedeny v následující tabulce.  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|`\f`|Znak nové stránky, \u000C.|  
|`\n`|Znak nového řádku, \u000A.|  
|`\r`|Návratový znak, \u000D.|  
|`\t`|Znak tabulátoru, \u0009.|  
|`\v`|Znak svislého tabulátoru, \u000B.|  
|`\x85`|Znak tři tečky nebo znak NEXT LINE (NEL) (…), \u0085.|  
|`\p{Z}`|Porovnává s jakýmkoli znakem oddělovače.|  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\s` je `[ \f\n\r\t\v]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ilustruje `\s` třídu znaků. Definuje vzor `\b\w+(e)?s(\s|$)`regulárního výrazu, který odpovídá slovu končícím na "s" nebo "ES" následovaný prázdným znakem nebo koncem vstupního řetězce. Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\b|Začne porovnání na hranici slova.|  
|\w+|Porovná jeden nebo více znaků slova.|  
|(e)?|Porovnává s „e“ jednou nebo vůbec.|  
|s|Porovnává s „s“.|  
|(\s&#124;$)|Porovnává buď prázdný znak, nebo konec vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-whitespace-character-s"></a>Znak, který není prázdný,: \s  
 `\S`odpovídá jakémukoli neprázdnému znaku. Je ekvivalentní `[^\f\n\r\t\v\x85\p{Z}]` se vzorem regulárního výrazu nebo opakem vzoru regulárního výrazu, který je ekvivalentní k `\s`, který se shoduje s prázdnými znaky. Další informace najdete v tématu [prázdný znak: \s](#WhitespaceCharacter).  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\S` je `[^ \f\n\r\t\v]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje `\S` prvek jazyka. Vzor `\b(\S+)\s?` regulárního výrazu porovnává řetězce, které jsou odděleny prázdnými znaky. Druhý prvek v <xref:System.Text.RegularExpressions.GroupCollection> objektu shody obsahuje porovnávaný řetězec. Vzor regulárního výrazu může být interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\S+)`|Porovnává s jedním nebo více prázdnými znaky. Toto je první zachytávající skupina.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>Znak desítkové číslice: \d  
 `\d`odpovídá libovolné desítkové číslici. Je ekvivalentní `\p{Nd}` se vzorem regulárního výrazu, který zahrnuje standardní desítkové číslice 0-9 a také desítkové číslice řady dalších znakových sad.  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\d` je `[0-9]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje `\d` prvek jazyka. Ověřuje, zda vstupní řetězec představuje platné telefonní číslo ve Spojených státech a Kanadě. Vzor `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`\(?`|Porovnává s jedním nebo žádným literálním znakem "(".|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`\)?`|Porovnává s jedním nebo žádným literálním znakem ")".|  
|`[\s-]`|Porovnává spojovník nebo prázdný znak.|  
|`(\(?\d{3}\)?[\s-])?`|Porovnává volitelnou levou závorku následovanou třemi desítkovými číslicemi, volitelnou pravou závorku a prázdný znak nebo spojovník, jednou nebo vůbec. Toto je první zachytávající skupina.|  
|`\d{3}-\d{4}`|Porovnává tři desítkové číslice následované spojovníkem a čtyřmi dalšími desítkovými číslicemi.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a>Nečíselný znak: \d  
 `\D`odpovídá jakémukoli nenumerickému znaku. Je ekvivalentní `\P{Nd}` se vzorem regulárního výrazu.  
  
 Pokud je zadáno chování kompatibilní s ECMAScript, `\D` je `[^0-9]`ekvivalentem. Informace o regulárních výrazech ECMAScript naleznete v části "chování při shodě ECMAScript" v tématu [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje prvek jazyka \D. Ověřuje, zda se řetězec jako součást čísla skládá z vhodné kombinace desítkových a nedesítkových znaků. Vzor `^\D\d{1,5}\D*$` regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`\D`|Porovná nečíslicový znak.|  
|`\d{1,5}`|Porovná jednu až pět desítkových číslic.|  
|`\D*`|Porovná nula, jednu nebo více než desítkových znaků.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>Podporované obecné kategorie sady Unicode  
 Sada Unicode definuje obecné kategorie uvedené v následující tabulce. Další informace najdete v tématu "formát souboru UCD" a "Obecné hodnoty kategorií" v [databázi znaků Unicode](https://www.unicode.org/reports/tr44/).  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|`Lu`|písmeno, velké písmeno|  
|`Ll`|písmeno, malé písmeno|  
|`Lt`|písmeno, velké počáteční písmeno|  
|`Lm`|písmeno, modifikátor|  
|`Lo`|písmeno, jiné|  
|`L`|Všechny znaky písmena. To `Lu`zahrnuje znaky, `Ll`, `Lt`, `Lm`a. `Lo`|  
|`Mn`|značka, bez mezer|  
|`Mc`|značka, kombinování mezer|  
|`Me`|značka, uzavření|  
|`M`|Všechny značky diakritických znamének. To zahrnuje `Mn` Kategorie`Me` , `Mc`a.|  
|`Nd`|číslo, desítková číslice|  
|`Nl`|číslo, písmeno|  
|`No`|číslo, jiné|  
|`N`|Všechna čísla. To zahrnuje `Nd` Kategorie`No` , `Nl`a.|  
|`Pc`|interpunkce, spojka|  
|`Pd`|interpunkce, pomlčka|  
|`Ps`|interpunkce, otevřená|  
|`Pe`|interpunkce, uzavřená|  
|`Pi`|interpunkce, počáteční uvozovka (může se chovat jako Ps nebo Pe v závislosti na použití)|  
|`Pf`|interpunkce, koncová uvozovka (může se chovat jako Ps nebo Pe v závislosti na použití)|  
|`Po`|interpunkce, jiné|  
|`P`|Všechny znaky interpunkce. `Pc`To zahrnuje kategorie, `Pd`, `Ps`, `Pe` ,`Pf`, a .`Po` `Pi`|  
|`Sm`|symbol, matematický|  
|`Sc`|symbol, měna|  
|`Sk`|symbol, modifikátor|  
|`So`|symbol, jiný|  
|`S`|Všechny symboly. To zahrnuje `Sm`kategorie, `Sc`, `Sk`a. `So`|  
|`Zs`|oddělovač, mezera|  
|`Zl`|oddělovač, řádek|  
|`Zp`|oddělovač, odstavec|  
|`Z`|Všechny znaky oddělovačů. To zahrnuje `Zs` Kategorie`Zp` , `Zl`a.|  
|`Cc`|jiný, ovládací prvek|  
|`Cf`|jiný, formát|  
|`Cs`|jiný, náhradník|  
|`Co`|jiný, soukromé použití|  
|`Cn`|jiný, nepřiřazené (žádné znaky nemají tuto vlastnost)|  
|`C`|Všechny znaky ovládacích prvků. To `Cc`zahrnuje kategorie, `Cf`, `Cs`, `Co`a. `Cn`|  
  
 Můžete určit kategorii sady Unicode jakéhokoliv konkrétního znaku předáním tohoto znaku <xref:System.Char.GetUnicodeCategory%2A> metodě. Následující příklad používá <xref:System.Char.GetUnicodeCategory%2A> metodu k určení kategorie každého prvku v poli, které obsahuje vybrané znaky latinky.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>Podporované pojmenované bloky

Rozhraní .NET poskytuje pojmenované bloky uvedené v následující tabulce. Množina podporovaných pojmenovaných bloků je založena na sadě Unicode 4.0 a Perl 5.6. Regulární výraz, který používá pojmenované bloky, naleznete v části [Kategorie sady Unicode nebo blok sady \\Unicode{} : p](#unicode-category-or-unicode-block-p) .  
  
|Rozsah bodu kódu|Název bloku|  
|----------------------|----------------|  
|0000 - 007F|`IsBasicLatin`|  
|0080 - 00FF|`IsLatin-1Supplement`|  
|0100 - 017F|`IsLatinExtended-A`|  
|0180 - 024F|`IsLatinExtended-B`|  
|0250 - 02AF|`IsIPAExtensions`|  
|02B0 - 02FF|`IsSpacingModifierLetters`|  
|0300 - 036F|`IsCombiningDiacriticalMarks`|  
|0370 - 03FF|`IsGreek`<br /><br /> -nebo-<br /><br /> `IsGreekandCoptic`|  
|0400 - 04FF|`IsCyrillic`|  
|0500 - 052F|`IsCyrillicSupplement`|  
|0530 - 058F|`IsArmenian`|  
|0590 - 05FF|`IsHebrew`|  
|0600 - 06FF|`IsArabic`|  
|0700 - 074F|`IsSyriac`|  
|0780 - 07BF|`IsThaana`|  
|0900 - 097F|`IsDevanagari`|  
|0980 - 09FF|`IsBengali`|  
|0A00 - 0A7F|`IsGurmukhi`|  
|0A80 - 0AFF|`IsGujarati`|  
|0B00 - 0B7F|`IsOriya`|  
|0B80 - 0BFF|`IsTamil`|  
|0C00 - 0C7F|`IsTelugu`|  
|0C80 - 0CFF|`IsKannada`|  
|0D00 - 0D7F|`IsMalayalam`|  
|0D80 - 0DFF|`IsSinhala`|  
|0E00 - 0E7F|`IsThai`|  
|0E80 - 0EFF|`IsLao`|  
|0F00 - 0FFF|`IsTibetan`|  
|1000 - 109F|`IsMyanmar`|  
|10A0 - 10FF|`IsGeorgian`|  
|1100 - 11FF|`IsHangulJamo`|  
|1200 - 137F|`IsEthiopic`|  
|13A0 - 13FF|`IsCherokee`|  
|1400 - 167F|`IsUnifiedCanadianAboriginalSyllabics`|  
|1680 - 169F|`IsOgham`|  
|16A0 - 16FF|`IsRunic`|  
|1700 - 171F|`IsTagalog`|  
|1720 - 173F|`IsHanunoo`|  
|1740 - 175F|`IsBuhid`|  
|1760 - 177F|`IsTagbanwa`|  
|1780 - 17FF|`IsKhmer`|  
|1800 - 18AF|`IsMongolian`|  
|1900 - 194F|`IsLimbu`|  
|1950 - 197F|`IsTaiLe`|  
|19E0 - 19FF|`IsKhmerSymbols`|  
|1D00 - 1D7F|`IsPhoneticExtensions`|  
|1E00 - 1EFF|`IsLatinExtendedAdditional`|  
|1F00 - 1FFF|`IsGreekExtended`|  
|2000 - 206F|`IsGeneralPunctuation`|  
|2070 - 209F|`IsSuperscriptsandSubscripts`|  
|20A0 - 20CF|`IsCurrencySymbols`|  
|20D0 - 20FF|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> -nebo-<br /><br /> `IsCombiningMarksforSymbols`|  
|2100 - 214F|`IsLetterlikeSymbols`|  
|2150 - 218F|`IsNumberForms`|  
|2190 - 21FF|`IsArrows`|  
|2200 - 22FF|`IsMathematicalOperators`|  
|2300 - 23FF|`IsMiscellaneousTechnical`|  
|2400 - 243F|`IsControlPictures`|  
|2440 - 245F|`IsOpticalCharacterRecognition`|  
|2460 - 24FF|`IsEnclosedAlphanumerics`|  
|2500 - 257F|`IsBoxDrawing`|  
|2580 - 259F|`IsBlockElements`|  
|25A0 - 25FF|`IsGeometricShapes`|  
|2600 - 26FF|`IsMiscellaneousSymbols`|  
|2700 - 27BF|`IsDingbats`|  
|27C0 - 27EF|`IsMiscellaneousMathematicalSymbols-A`|  
|27F0 - 27FF|`IsSupplementalArrows-A`|  
|2800 - 28FF|`IsBraillePatterns`|  
|2900 - 297F|`IsSupplementalArrows-B`|  
|2980 - 29FF|`IsMiscellaneousMathematicalSymbols-B`|  
|2A00 - 2AFF|`IsSupplementalMathematicalOperators`|  
|2B00 - 2BFF|`IsMiscellaneousSymbolsandArrows`|  
|2E80 - 2EFF|`IsCJKRadicalsSupplement`|  
|2F00 - 2FDF|`IsKangxiRadicals`|  
|2FF0 - 2FFF|`IsIdeographicDescriptionCharacters`|  
|3000 - 303F|`IsCJKSymbolsandPunctuation`|  
|3040 - 309F|`IsHiragana`|  
|30A0 - 30FF|`IsKatakana`|  
|3100 - 312F|`IsBopomofo`|  
|3130 - 318F|`IsHangulCompatibilityJamo`|  
|3190 - 319F|`IsKanbun`|  
|31A0 - 31BF|`IsBopomofoExtended`|  
|31F0 - 31FF|`IsKatakanaPhoneticExtensions`|  
|3200 - 32FF|`IsEnclosedCJKLettersandMonths`|  
|3300 - 33FF|`IsCJKCompatibility`|  
|3400 - 4DBF|`IsCJKUnifiedIdeographsExtensionA`|  
|4DC0 - 4DFF|`IsYijingHexagramSymbols`|  
|4E00 - 9FFF|`IsCJKUnifiedIdeographs`|  
|A000 - A48F|`IsYiSyllables`|  
|A490 - A4CF|`IsYiRadicals`|  
|AC00 - D7AF|`IsHangulSyllables`|  
|D800 - DB7F|`IsHighSurrogates`|  
|DB80 - DBFF|`IsHighPrivateUseSurrogates`|  
|DC00 - DFFF|`IsLowSurrogates`|  
|E000 - F8FF|`IsPrivateUse` Nebo `IsPrivateUseArea`|  
|F900 - FAFF|`IsCJKCompatibilityIdeographs`|  
|FB00 - FB4F|`IsAlphabeticPresentationForms`|  
|FB50 - FDFF|`IsArabicPresentationForms-A`|  
|FE00 - FE0F|`IsVariationSelectors`|  
|FE20 - FE2F|`IsCombiningHalfMarks`|  
|FE30 - FE4F|`IsCJKCompatibilityForms`|  
|FE50 - FE6F|`IsSmallFormVariants`|  
|FE70 - FEFF|`IsArabicPresentationForms-B`|  
|FF00 - FFEF|`IsHalfwidthandFullwidthForms`|  
|FFF0 - FFFF|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-base_group---excluded_group"></a>Odčítání tříd znaků: [Base_group-[excluded_group]]  
 Třída znaků definuje množinu znaků. Odčítání třídy znaků získává množinu znaků, která je výsledkem vyloučení znaků jedné třídy znaků, které jsou obsaženy v jiné třídě znaků.  
  
 Výraz odčítání třídy znaků má následující tvar:  
  
 `[` *base_group* `-[` *excluded_group* `]]`  
  
 Hranaté závorky`[]`() a spojovníky (`-`) jsou povinné. *Base_group* je [Skupina pozitivních znaků](#PositiveGroup) nebo [Skupina negativních znaků](#NegativeGroup). Komponenta *excluded_group* je další pozitivní nebo negativní skupina znaků nebo jiný výraz odčítání třídy znaků (to znamená, že je možné vnořit výrazy odčítání třídy znaků).  
  
 Předpokládejme například, že máte základní skupinu, která se skládá z rozsahu znaků od „a“ až do „z“. Chcete-li definovat množinu znaků, která se skládá ze základní skupiny s výjimkou znaku "m" `[a-z-[m]]`, použijte. Chcete-li definovat množinu znaků, která se skládá ze základní skupiny s výjimkou sady znaků "d", "j" a "p", použijte `[a-z-[djp]]`. Chcete-li definovat množinu znaků, která se skládá ze základní skupiny s výjimkou rozsahu znaků od "m" do "p" `[a-z-[m-p]]`, použijte.  
  
 Zvažte výraz odčítání třídy vnořeného znaku, `[a-z-[d-w-[m-o]]]`. Výraz je vyhodnocen od nejvnitřnějšího rozsahu znaků ven. Nejdříve se rozsah znaků od „m“ do „o“ odečte od rozsahu znaků „d“ až „w“, který dává množinu znaků od „d“ až „l“ a „p“ až „w“. Tato sada se pak odečte od rozsahu znaků od "a" do "z", který vrací sadu znaků `[abcmnoxyz]`.  
  
 Při odčítání třídy znaků můžete použít libovolnou třídu znaků. Chcete-li definovat množinu znaků, které se skládají ze všech znaků Unicode z \u0000 až \uFFFF s výjimkou`\s`prázdných znaků (), znaky v`\p{P}`poli `IsGreek` s názvem Block (`\p{IsGreek}`) a znak ovládacího prvku další řádek sady Unicode (\x85) použijte `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 Zvolte třídy znaků pro výraz odčítání třídy znaků, které budou poskytovat užitečné výsledky. Vyhněte se výrazu, jehož výsledkem jsou prázdné množiny znaků, které nemohou odpovídat ničemu, nebo výrazu, který odpovídá původní základní skupině. Například prázdná sada je výsledkem výrazu `[\p{IsBasicLatin}-[\x00-\x7F]]`, který odečte všechny znaky `IsBasicLatin` v rozsahu znaků z `IsBasicLatin` kategorie Obecné. Podobně je původní základní skupina výsledkem výrazu `[a-z-[0-9]]`.  Důvodem je skutečnost, že základní skupina, která je rozsahem znaků písmen od „a“ až do „z“, neobsahuje žádné znaky ve vyloučené skupině, která je rozsahem znaků desítkových číslic od „0“ až po „9“.  
  
 Následující příklad definuje regulární výraz `^[0-9-[2468]]+$`, který odpovídá nule a lichým číslicím ve vstupním řetězci.  Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|^|Začne porovnávání na začátku vstupního řetězce.|  
|`[0-9-[2468]]+`|Porovnává jeden nebo více výskytů libovolného znaku od 0 do 9 s výjimkou 2, 4, 6 a 8. Jinými slovy, porovnává jeden nebo více výskytů nuly nebo liché číslice.|  
|$|Ukončí porovnávání na konci vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Char.GetUnicodeCategory%2A>
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
