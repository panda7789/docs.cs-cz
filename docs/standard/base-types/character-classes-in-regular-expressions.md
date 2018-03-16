---
title: "Třídy znaků v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 98aaa5c7bbd28facf9cc06fd0d0898b72ea7dbc2
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="character-classes-in-regular-expressions"></a>Třídy znaků v regulárních výrazech
<a name="Top"></a> Třídy znaků definuje sadu znaků, které může dojít ve vstupním řetězci pro úspěšnou shodu. Jazyk regulárních výrazů v .NET podporuje následujících tříd znaků:  
  
-   Skupiny pozitivních znaků. Znak ve vstupním řetězci musí odpovídat jedné ze zadaných množin znaků. Další informace najdete v tématu [skupina pozitivních znaků](#PositiveGroup).  
  
-   Skupiny negativních znaků. Znak ve vstupním řetězci nesmí odpovídat jedné ze zadaných množin znaků. Další informace najdete v tématu [Skupina negativních znaků](#NegativeGroup).  
  
-   Libovolný znak. `.` (Tečka) znak v regulárním výrazu je zástupný znak, který odpovídá jakémukoli znaku kromě `\n`. Další informace najdete v tématu [jakýkoli znak](#AnyCharacter).  
  
-   Obecná kategorie nebo pojmenovaný blok sady Unicode. Pro úspěšné vyhledání shody musí být znak ve vstupním řetězci členem určité kategorie sady Unicode nebo musí spadat do souvislého rozsahu znaků sady Unicode. Další informace najdete v tématu [kategorii Unicode nebo Unicode bloku](#CategoryOrBlock).  
  
-   Negativní obecná kategorie nebo pojmenovaný blok sady Unicode. Pro úspěšné vyhledání shody nesmí být znak ve vstupním řetězci členem určité kategorie sady Unicode ani nesmí spadat do souvislého rozsahu znaků sady Unicode. Další informace najdete v tématu [negativní kategorie Unicode nebo blok kódu Unicode](#NegativeCategoryOrBlock).  
  
-   Znak slova. Znak ve vstupním řetězci může patřit do kterékoli kategorie sady Unicode, která je vhodná pro znaky ve slovech. Další informace najdete v tématu [Word znak](#WordCharacter).  
  
-   Mimoslovní znak. Znak ve vstupním řetězci může patřit do jakékoli kategorie sady Unicode, která není znakem slova. Další informace najdete v tématu [znak mimo slovo](#NonWordCharacter).  
  
-   Prázdný znak. Znakem ve vstupním řetězci může být jakýkoli oddělovací znak sady Unicode nebo některý z mnoha řídicích znaků. Další informace najdete v tématu [prázdný znak](#WhitespaceCharacter).  
  
-   Neprázdný znak. Znakem ve vstupním řetězci může být libovolný znak, který není prázdným znakem. Další informace najdete v tématu [znak bez mezer](#NonWhitespaceCharacter).  
  
-   Desítková číslice. Znakem ve vstupním řetězci může být kterýkoli ze znaků, který je klasifikován jako desítková číslice sady Unicode. Další informace najdete v tématu [znaku desítková číslice](#DigitCharacter).  
  
-   Nedesetinné číslo. Znakem ve vstupním řetězci může být jakýkoli jiný znak než desítková číslice sady Unicode. Další informace najdete v tématu [znaku desítková číslice](#NonDigitCharacter).  
  
 Rozhraní .NET podporuje výrazy odčítání třídy znaků, který umožňuje definovat sadu znaků jako výsledek vyloučení jedné třídy znaků z jiné třídě znaků. Další informace najdete v tématu [odčítání tříd znaků](#CharacterClassSubtraction).  
  
> [!NOTE]
>  Znak třídy, které odpovídají znaky podle kategorie, jako například [\w](#WordCharacter) tak, aby odpovídaly znaků slova nebo [{} \p](#CategoryOrBlock) tak, aby odpovídaly kategorie sady Unicode, závisí na <xref:System.Globalization.CharUnicodeInfo> třída k zadání informací o znak kategorie.  Počínaje [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], jsou na základě kategorií znak [ve standardu Unicode, verze 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] prostřednictvím [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], jsou založené na [ve standardu Unicode, verze 6.3.0](http://www.unicode.org/versions/Unicode6.3.0/).  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>Pozitivní skupina znaků: [ ]  
 Skupina pozitivních znaků určuje seznam znaků, které se mohou objevit ve vstupním řetězci, aby nastala shoda. Tento seznam znaků může být zadán jako jednotlivé znaky, jako rozsah nebo obojí.  
  
 Syntaxe pro určení seznamu jednotlivých znaků je následující:  
  
 [*character_group*]  
  
 kde *character_group* je seznam jednotlivé znaky, které se mohou objevit ve vstupním řetězci pro úspěšnou shodu. *character_group* může obsahovat libovolnou kombinaci jeden nebo více znaků, literálu, [řídicí znaky](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), nebo třídy znaků.  
  
 Syntaxe pro zadání rozsahu znaků je následující:  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 kde *firstCharacter* je znak, který začíná rozsah a *lastCharacter* je znak, který končí rozsah. Rozsah znaků je souvislá řada znaků definovaná zadáním prvního znaku v řadě, spojovníku (-) a posledního znaku v řadě. Dva znaky jsou souvislé, pokud mají sousedící kódové body sady Unicode.  
  
 Některé běžné vzory regulárních výrazů, které obsahují pozitivní třídy znaků, jsou uvedeny v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`[aeiou]`|Porovná se všemi samohláskami.|  
|`[\p{P}\d]`|Porovná se všemi interpunkčními znaky a znaky desítkových číslic.|  
|`[\s\p{P}]`|Odpovídat všechny mezera nebo interpunkční znaménka.|  
  
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
  
 V následujícím příkladu jsou vyhledána slova začínající kterýmkoli velkým písmenem. Používá dílčí výraz `[A-Z]` k reprezentaci rozsahu velkých písmen od A do Z.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Regulární výraz `\b[A-Z]\w*\b` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`[A-Z]`|Porovná s libovolným znakem velkého písmene od A až do Z.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Porovná hranici slova.|  
  
 [Zpět na začátek](#Top)  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a>Negativní skupina znaků: [^]  
 Skupina negativních znaků určuje seznam znaků, které se nesmí objevit ve vstupním řetězci, aby došlo ke shodě. Seznam znaků může být zadán jako jednotlivé znaky, jako rozsah nebo obojí.  
  
 Syntaxe pro určení seznamu jednotlivých znaků je následující:  
  
 [*^character_group*]  
  
 kde *character_group* je seznam jednotlivých znaků, které se nesmí nacházet ve vstupním řetězci shody proběhla úspěšně. *character_group* může obsahovat libovolnou kombinaci jeden nebo více znaků, literálu, [řídicí znaky](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), nebo třídy znaků.  
  
 Syntaxe pro zadání rozsahu znaků je následující:  
  
 [^*firstCharacter*-*lastCharacter*]  
  
 kde *firstCharacter* je znak, který začíná rozsahu, a *lastCharacter* je znak, který končí rozsah. Rozsah znaků je souvislá řada znaků definovaná zadáním prvního znaku v řadě, spojovníku (-) a posledního znaku v řadě. Dva znaky jsou souvislé, pokud mají sousedící kódové body sady Unicode.  
  
 Mohou být spojeny dva nebo více rozsahů znaků. Například zadejte rozsah čísel desítkové soustavy "0" až "9", rozsah malých písmen "a" až "f" a rozsah velká písmena "A" až "F", použít `[0-9a-fA-F]`.  
  
 Uvozovací znak (`^`) záporné znakem skupiny je povinná a označuje znak skupina je skupina negativních znaků místo skupiny pozitivních znaků.  
  
> [!IMPORTANT]
>  Skupina negativních znaků ve větším vzoru regulárního výrazu není kontrolní výraz nulové šířky. To znamená, že po vyhodnocení skupiny negativních znaků modul regulárních výrazů postoupí o jeden znak ve vstupním řetězci.  
  
 Některé běžné vzory regulárních výrazů, které obsahují skupiny negativních znaků, jsou uvedeny v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`[^aeiou]`|Porovná se všemi znaky kromě samohlásek.|  
|`[^\p{P}\d]`|Porovná se všemi znaky kromě interpunkčních znaků a znaků desítkových číslic.|  
  
 Následující příklad porovná libovolné slovo, které začíná znaky „th“ a nenásleduje je „o“.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 Regulární výraz `\bth[^o]\w+\b` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne na hranici slova.|  
|`th`|Porovná s literálními znaky „th“.|  
|`[^o]`|Porovná s libovolným znakem, který není „o“.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`\b`|Skončí na hranici slova.|  
  
 [Zpět na začátek](#Top)  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>Libovolný znak: .  
 Tečka (.) odpovídá jakémukoli znaku kromě `\n` (znak nového řádku, \u000A), s následující dvěma předpoklady:  
  
-   Pokud je vzor regulárního výrazu upraveném <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost, nebo pokud část vzoru, který obsahuje `.` je třída znaků upraveném `s` možnost, `.` odpovídá jakémukoliv znaku. Další informace najdete v tématu [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
     Následující příklad ukazuje různé chování `.` znak třídy ve výchozím nastavení a s <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost. Regulární výraz `^.+` spustí na začátku řetězce a odpovídá každý znak. Ve výchozím nastavení shody končí na konci prvního řádku. regulární výraz odpovídá znakem konce řádku, `\r` nebo \u000D, ale neodpovídá `\n`. Protože <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost interpretuje celý vstupní řetězec jako jeden řádek, porovnává každý znak ve vstupním řetězci, včetně `\n`.  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  Protože odpovídá jakémukoli znaku kromě `\n`, `.` třída znaků také odpovídající `\r` (návratový znak, \u000D).  
  
-   Ve skupině pozitivních nebo negativních znaků je tečka považována za literální znak tečky a nikoli za třídu znaků. Další informace najdete v tématu [skupina pozitivních znaků](#PositiveGroup) a [Skupina negativních znaků](#NegativeGroup) výše v tomto tématu. Následující příklad uvádí ukázku definováním regulární výraz, který zahrnuje tečka (`.`) jako třída znaků i jako člen skupiny pozitivních znaků. Regulární výraz `\b.*[.?!;:](\s|\z)` začíná na hranici slova, odpovídá jakémukoliv znaku, dokud zjistí jednu ze čtyř interpunkčních znamének, včetně období a potom porovnává prázdný znak nebo konci řetězce.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  Protože odpovídá libovolný znak, `.` jazyk element se často používá u opožděné kvantifikátoru, pokud vzor regulárního výrazu pokusí porovnat libovolný znak vícekrát. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 [Zpět na začátek](#Top)  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Kategorie nebo blok standardu Unicode: \p {}  
 Standard Unicode přiřadí každému znaku obecnou kategorii. Například určitý znak může být velké písmeno (reprezentována `Lu` kategorie), desítková číslice ( `Nd` kategorie), matematický symbol ( `Sm` kategorie), nebo oddělovač odstavců ( `Zl` kategorie). Určité množiny znaků sady Unicode zabírají také určité oblasti nebo bloky po sobě následujících bodů kódu. Například množina znaků základní Latinky se nalézá od \u0000 až do \u007F, zatímco množina znaků Arabštiny se nalézá od \u0600 až do \u06FF.  
  
 Konstrukce regulárního výrazu  
  
 `\p{` *Jméno* `}`  
  
 odpovídá jakémukoliv znaku, který patří do obecné kategorie Unicode nebo pojmenovaného blok, kde *název* je zkratka pro kategorii nebo název pojmenované bloku. Seznam kategorií zkratky najdete v tématu [podporována obecná Unicode kategorie](#SupportedUnicodeGeneralCategories) později v tomto tématu. Seznam pojmenovaných bloků najdete v tématu [podporované pojmenované bloky](#SupportedNamedBlocks) později v tomto tématu.  
  
 Následující příklad používá `\p{` *název* `}` konstrukce tak, aby odpovídaly obou obecné kategorie sady Unicode (v takovém případě `Pd`, nebo interpunkční znaménka, Dash kategorie) a pojmenované bloku ( `IsGreek` a `IsBasicLatin` s názvem bloky).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 Regulární výraz `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` je definovaný jak je znázorněno v následující tabulce.  
  
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
  
 [Zpět na začátek](#Top)  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a>Negativní kategorie nebo blok standardu Unicode: \P {}  
 Standard Unicode přiřadí každému znaku obecnou kategorii. Například určitý znak může být velké písmeno (reprezentována `Lu` kategorie), desítková číslice ( `Nd` kategorie), matematický symbol ( `Sm` kategorie), nebo oddělovač odstavců ( `Zl` kategorie). Určité množiny znaků sady Unicode zabírají také určité oblasti nebo bloky po sobě následujících bodů kódu. Například množina znaků základní Latinky se nalézá od \u0000 až do \u007F, zatímco množina znaků Arabštiny se nalézá od \u0600 až do \u06FF.  
  
 Konstrukce regulárního výrazu  
  
 `\P{` *Jméno* `}`  
  
 odpovídá jakémukoliv znaku, který nepatří do obecné kategorie Unicode nebo pojmenovaného blok, kde *název* je zkratka pro kategorii nebo název pojmenované bloku. Seznam kategorií zkratky najdete v tématu [podporována obecná Unicode kategorie](#SupportedUnicodeGeneralCategories) později v tomto tématu. Seznam pojmenovaných bloků najdete v tématu [podporované pojmenované bloky](#SupportedNamedBlocks) později v tomto tématu.  
  
 Následující příklad používá `\P{` *název* `}` konstrukce odebrat symboly měny (v takovém případě `Sc`, nebo, kategorie symbolu měny) z číselných řetězců.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Regulární výraz `(\P{Sc})+` odpovídá jeden nebo více znaků, které nejsou symboly měny; efektivně odděluje žádné symbolu měny z výsledný řetězec.  
  
 [Zpět na začátek](#Top)  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>Znak, který může být součástí slova: \w  
 `\w` odpovídá jakémukoliv znaku aplikace word. Znak slova je členem každé kategorie sady Unicode uvedených v následující tabulce.  
  
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
  
 Pokud je zadán chování ECMAScript, `\w` je ekvivalentní `[a-zA-Z_0-9]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Protože odpovídá jakémukoliv znaku, word, `\w` jazyk element se často používá u opožděné kvantifikátoru, pokud vzor regulárního výrazu pokusí porovnat libovolný znak vícekrát, za nímž následuje znak určité slovo. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Následující příklad používá `\w` jazyk elementu duplicitní znaků v textovém. V příkladu definuje vzor regulárního výrazu `(\w)\1`, která jde interpretovat následujícím způsobem.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|(\w)|Porovnává znak slova. Toto je první zachytávající skupina.|  
|\1|Porovnává hodnotu prvního zachycení.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
 [Zpět na začátek](#Top)  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>Znak, který nemůže být součástí slova: \W  
 `\W` odpovídá jakémukoliv znaku aplikace word. Prvek jazyka \W je ekvivalentní s následující třídou znaků:  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 Jinými slovy odpovídá jakémukoliv znaku, s výjimkou těch v kódování Unicode kategorií uvedených v následující tabulce.  
  
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
  
 Pokud je zadán chování ECMAScript, `\W` je ekvivalentní `[^a-zA-Z_0-9]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Protože odpovídá jakémukoliv znaku aplikace word `\W` jazyk element se často používá u opožděné kvantifikátoru, pokud vzor regulárního výrazu pokusí porovnat libovolný znak mimo slovo několikrát následuje znak konkrétní bez slova. Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Následující příklad ukazuje `\W` třídy znaků.  Definuje vzor regulárního výrazu `\b(\w+)(\W){1,2}`, který porovnává slovo následuje jedna nebo dvě-aplikace word znaky jako mezera nebo interpunkční znaménka. Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\b|Začne porovnání na hranici slova.|  
|(\w+)|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|(\W){1,2}|Porovnává s mimoslovním znakem jednou nebo dvakrát. Toto je druhá zachytávající skupina.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 Protože <xref:System.Text.RegularExpressions.Group> objekt pro druhou zachytávající skupinu obsahuje pouze jediný zachycený znak aplikace word, příklad načte všechny zaznamenané-aplikace word znaky z <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je vrácen <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost.  
  
 [Zpět na začátek](#Top)  
  
<a name="WhitespaceCharacter"></a>   
## <a name="white-space-character-s"></a>Prázdný znak: \s  
 `\s` odpovídá jakémukoliv znaku prázdný znak. Je ekvivalentní s uvozovacími sekvencemi a kategoriemi sady Unicode, které jsou uvedeny v následující tabulce.  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|`\f`|Znak nové stránky, \u000C.|  
|`\n`|Znak nového řádku, \u000A.|  
|`\r`|Návratový znak, \u000D.|  
|`\t`|Znak tabulátoru, \u0009.|  
|`\v`|Znak svislého tabulátoru, \u000B.|  
|`\x85`|Znak tři tečky nebo znak NEXT LINE (NEL) (…), \u0085.|  
|`\p{Z}`|Porovnává s jakýmkoli znakem oddělovače.|  
  
 Pokud je zadán chování ECMAScript, `\s` je ekvivalentní `[ \f\n\r\t\v]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje `\s` třídy znaků. Definuje vzor regulárního výrazu `\b\w+(e)?s(\s|$)`, který odpovídá slova končící na "s" nebo "es" následované prázdný znak nebo konci vstupní řetězec. Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\b|Začne porovnání na hranici slova.|  
|\w+|Porovná jeden nebo více znaků slova.|  
|(e)?|Porovnává s „e“ jednou nebo vůbec.|  
|s|Porovnává s „s“.|  
|(\s&#124;$)|Odpovídat prázdný znak nebo konci vstupní řetězec.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
 [Zpět na začátek](#Top)  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-white-space-character-s"></a>Jiný než prázdný znak: \S  
 `\S` odpovídá jakémukoliv znaku prázdný znak. Ta je ekvivalentní `[^\f\n\r\t\v\x85\p{Z}]` regulární výraz nebo je opakem vzor regulárního výrazu, který je ekvivalentní `\s`, který odpovídá prázdné znaky. Další informace najdete v tématu [prázdný znak: \s](#WhitespaceCharacter).  
  
 Pokud je zadán chování ECMAScript, `\S` je ekvivalentní `[^ \f\n\r\t\v]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje `\S` element jazyka. Regulární výraz `\b(\S+)\s?` odpovídá řetězce, které jsou odděleny prázdné znaky. Druhý prvkem v na shodu <xref:System.Text.RegularExpressions.GroupCollection> objektu obsahuje odpovídající řetězec. Vzor regulárního výrazu může být interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\S+)`|Porovnává s jedním nebo více prázdnými znaky. Toto je první zachytávající skupina.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
 [Zpět na začátek](#Top)  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>Znak desítkové číslice: \d  
 `\d` Vyhledá všechny desítková číslice. Ta je ekvivalentní `\p{Nd}` vzor regulárního výrazu, který obsahuje standardní desítková číslice 0 – 9 a desetinných číslic čísla jiné znakové sady.  
  
 Pokud je zadán chování ECMAScript, `\d` je ekvivalentní `[0-9]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje `\d` element jazyka. Ověřuje, zda vstupní řetězec představuje platné telefonní číslo ve Spojených státech a Kanadě. Regulární výraz `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` je definovaný jak je znázorněno v následující tabulce.  
  
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
  
 [Zpět na začátek](#Top)  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a>Jiný znak než číslice: \D  
 `\D` odpovídá jakémukoliv znaku bez číslice. Ta je ekvivalentní `\P{Nd}` regulární výraz.  
  
 Pokud je zadán chování ECMAScript, `\D` je ekvivalentní `[^0-9]`. Informace o ECMAScript regulární výrazy, najdete v části "ECMAScript chování porovnávání" v [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Následující příklad ukazuje prvek jazyka \D. Ověřuje, zda se řetězec jako součást čísla skládá z vhodné kombinace desítkových a nedesítkových znaků. Regulární výraz `^\D\d{1,5}\D*$` je definovaný jak je znázorněno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`\D`|Porovná nečíslicový znak.|  
|`\d{1,5}`|Porovná jednu až pět desítkových číslic.|  
|`\D*`|Odpovídat nula, jednu nebo více znaků desetinné číslo.|  
|`$`|Porovná konec vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
 [Zpět na začátek](#Top)  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>Podporované obecné kategorie sady Unicode  
 Sada Unicode definuje obecné kategorie uvedené v následující tabulce. Další informace najdete v tématu "Formát souboru UCD" a "Hodnoty obecné kategorie" v tématu na [databáze znaků Unicode](http://www.unicode.org/reports/tr44/).  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|`Lu`|písmeno, velké písmeno|  
|`Ll`|písmeno, malé písmeno|  
|`Lt`|písmeno, velké počáteční písmeno|  
|`Lm`|písmeno, modifikátor|  
|`Lo`|písmeno, jiné|  
|`L`|Všechny znaky písmena. To zahrnuje `Lu`, `Ll`, `Lt`, `Lm`, a `Lo` znaků.|  
|`Mn`|značka, bez mezer|  
|`Mc`|značka, kombinování mezer|  
|`Me`|značka, uzavření|  
|`M`|Všechny značky diakritických znamének. To zahrnuje `Mn`, `Mc`, a `Me` kategorií.|  
|`Nd`|číslo, desítková číslice|  
|`Nl`|číslo, písmeno|  
|`No`|číslo, jiné|  
|`N`|Všechna čísla. To zahrnuje `Nd`, `Nl`, a `No` kategorií.|  
|`Pc`|interpunkce, spojka|  
|`Pd`|interpunkce, pomlčka|  
|`Ps`|interpunkce, otevřená|  
|`Pe`|interpunkce, uzavřená|  
|`Pi`|interpunkce, počáteční uvozovka (může se chovat jako Ps nebo Pe v závislosti na použití)|  
|`Pf`|interpunkce, koncová uvozovka (může se chovat jako Ps nebo Pe v závislosti na použití)|  
|`Po`|interpunkce, jiné|  
|`P`|Všechny znaky interpunkce. To zahrnuje `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, a `Po` kategorií.|  
|`Sm`|symbol, matematický|  
|`Sc`|symbol, měna|  
|`Sk`|symbol, modifikátor|  
|`So`|symbol, jiný|  
|`S`|Všechny symboly. To zahrnuje `Sm`, `Sc`, `Sk`, a `So` kategorií.|  
|`Zs`|oddělovač, mezera|  
|`Zl`|oddělovač, řádek|  
|`Zp`|oddělovač, odstavec|  
|`Z`|Všechny znaky oddělovačů. To zahrnuje `Zs`, `Zl`, a `Zp` kategorií.|  
|`Cc`|jiný, ovládací prvek|  
|`Cf`|jiný, formát|  
|`Cs`|jiný, náhradník|  
|`Co`|jiný, soukromé použití|  
|`Cn`|jiný, nepřiřazené (žádné znaky nemají tuto vlastnost)|  
|`C`|Všechny znaky ovládacích prvků. To zahrnuje `Cc`, `Cf`, `Cs`, `Co`, a `Cn` kategorií.|  
  
 Můžete určit kategorii žádné konkrétní znak Unicode předáním tento znak, který má <xref:System.Char.GetUnicodeCategory%2A> metoda. Následující příklad používá <xref:System.Char.GetUnicodeCategory%2A> metoda k určení kategorie každý prvek v pole, které obsahuje vybrané znaky latinky.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
 [Zpět na začátek](#Top)  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>Podporované pojmenované bloky  
 Rozhraní .NET poskytuje pojmenované bloky, které jsou uvedeny v následující tabulce. Množina podporovaných pojmenovaných bloků je založena na sadě Unicode 4.0 a Perl 5.6.  
  
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
  
 [Zpět na začátek](#Top)  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a>Odčítání tříd znaků: [základní_skupina-[vyloučená_skupina]]  
 Třída znaků definuje množinu znaků. Odčítání třídy znaků získává množinu znaků, která je výsledkem vyloučení znaků jedné třídy znaků, které jsou obsaženy v jiné třídě znaků.  
  
 Výraz odčítání třídy znaků má následující tvar:  
  
 `[` *base_group* `-[` *excluded_group* `]]`  
  
 Hranaté závorky (`[]`) a pomlčku (`-`) jsou povinné. *Base_group* je [skupina kladné znaků](#PositiveGroup) nebo [Skupina negativních znaků](#NegativeGroup). *Excluded_group* komponenta se jiná skupina kladné a záporné znaků nebo jiný výraz odčítání třídy znaků (to znamená, že můžete vnořovat výrazy odčítání třídy znaků).  
  
 Předpokládejme například, že máte základní skupinu, která se skládá z rozsahu znaků od „a“ až do „z“. Chcete-li definovat sadu znaků, který se skládá ze základní skupiny s výjimkou znak "m", použijte `[a-z-[m]]`. Chcete-li definovat sadu znaků, který se skládá ze základní skupiny s výjimkou sady znaků "d", "d" a "p", použijte `[a-z-[djp]]`. Chcete-li definovat sadu znaků, který se skládá ze základní skupiny s výjimkou rozsahu znaků od "m" až "p", použijte `[a-z-[m-p]]`.  
  
 Vezměte v úvahu výraz odčítání třídy vnořené znaků, `[a-z-[d-w-[m-o]]]`. Výraz je vyhodnocen od nejvnitřnějšího rozsahu znaků ven. Nejdříve se rozsah znaků od „m“ do „o“ odečte od rozsahu znaků „d“ až „w“, který dává množinu znaků od „d“ až „l“ a „p“ až „w“. Tato sada je poté odečtena od rozsahu znaků od "a" prostřednictvím "z", která dává sadu znaků `[abcmnoxyz]`.  
  
 Při odčítání třídy znaků můžete použít libovolnou třídu znaků. K definování sady znaků, který obsahuje všechny znaky Unicode z \u0000 do \uFFFF s výjimkou prázdných znaků (`\s`), znaky v obecné kategorii interpunkční znaménka (`\p{P}`), znakům `IsGreek` s názvem blok (`\p{IsGreek}`), a použít řídicí znak Unicode další řádek (\x85), `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 Zvolte třídy znaků pro výraz odčítání třídy znaků, které budou poskytovat užitečné výsledky. Vyhněte se výrazu, jehož výsledkem jsou prázdné množiny znaků, které nemohou odpovídat ničemu, nebo výrazu, který odpovídá původní základní skupině. Například prázdná sada je výsledkem výrazu `[\p{IsBasicLatin}-[\x00-\x7F]]`, který odečte všechny znaky v `IsBasicLatin` znak rozsahu od `IsBasicLatin` obecné kategorie. Podobně původní základní skupina je výsledkem výrazu `[a-z-[0-9]]`.  Důvodem je skutečnost, že základní skupina, která je rozsahem znaků písmen od „a“ až do „z“, neobsahuje žádné znaky ve vyloučené skupině, která je rozsahem znaků desítkových číslic od „0“ až po „9“.  
  
 V následujícím příkladu definuje regulární výraz, `^[0-9-[2468]]+$`, který odpovídá nule a liché číslic ve vstupním řetězci.  Regulární výraz je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|^|Začne porovnávání na začátku vstupního řetězce.|  
|`[0-9-[2468]]+`|Porovnává jeden nebo více výskytů libovolného znaku od 0 do 9 s výjimkou 2, 4, 6 a 8. Jinými slovy, porovnává jeden nebo více výskytů nuly nebo liché číslice.|  
|$|Ukončí porovnávání na konci vstupního řetězce.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Char.GetUnicodeCategory%2A>  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md)
