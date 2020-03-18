---
title: Znak escapes v regulárních výrazech rozhraní .NET
description: Informace o speciálních a uvozevých znacích v regulárních výrazech rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
ms.openlocfilehash: 82e60b3cb5eb777d48219209550367642f78d8c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711425"
---
# <a name="character-escapes-in-regular-expressions"></a>Řídicí sekvence znaků v regulárních výrazech
Zpětné lomítko (\\) v regulárním výrazu označuje jednu z následujících položek:  
  
- Znak, který následuje, je speciální znak, jak je znázorněno v tabulce v následující části. Například `\b` je kotva, která označuje, že shoda regulárních výrazů by měla začínat na hranici slova, `\t` představuje kartu a `\x020` představuje mezeru.  
  
- Znak, který by jinak být interpretován jako unescaped jazyk konstrukce by měla být interpretována doslovně. Například složená`{`závorka ( ) začíná definici kvantifikátoru, ale zpětné lomítko následované závorkou (`\{`) označuje, že modul regulárních výrazů by měl odpovídat závorce. Podobně jedno zpětné lomítko označuje začátek konstrukce uvozeného jazyka, ale dvě zpětná lomítka (`\\`) označují, že modul regulárních výrazů by měl odpovídat zpětnému lomítku.  
  
> [!NOTE]
> Úniky znaků jsou rozpoznány ve vzorcích regulárních výrazů, ale ne v náhradních vzorcích.  
  
## <a name="character-escapes-in-net"></a>Znak unikne v rozhraní .NET  
 V následující tabulce jsou uvedeny řídicí znaky podporované regulárními výrazy v rozhraní .NET.  
  
|Znak nebo sekvence|Popis|  
|---------------------------|-----------------|  
|Všechny znaky kromě následujících znaků:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Jiné znaky než ty, které jsou uvedeny ve sloupci **Znak nebo sekvenční,** nemají v regulárních výrazech žádný zvláštní význam; shodují se sami.<br /><br /> Znaky obsažené ve sloupci **Znak nebo sekvenční** jsou speciální prvky jazyka regulárních výrazů. Aby byly spárovány v regulárním výrazu, musí být řídicí nebo zahrnuty do [skupiny pozitivních znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Například regulární `\$\d+` `[$]\d+` výraz nebo odpovídá "$1200".|  
|`\a`|Odpovídá znaku zvonku `\u0007`(alarmu), .|  
|`\b`|Ve *třídě znaků character_group* `]` odpovídá backspace . `\u0008`. `[`  (Viz [Třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Mimo třídu `\b` znaků je kotva, která odpovídá hranici slova. (Viz [Kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Odpovídá kartě `\u0009`.|  
|`\r`|Odpovídá návratu vozíku, `\u000D`. Všimněte `\r` si, že není ekvivalentní `\n`znak u nového řádku .|  
|`\v`|Odpovídá svislé kartě . `\u000B`|  
|`\f`|Odpovídá informačnímu `\u000C`kanálu formuláře .|  
|`\n`|Odpovídá novému `\u000A`řádku .|  
|`\e`|Odpovídá útěku, `\u001B`.|  
|`\`*nnn*|Odpovídá znaku ASCII, kde *se nnn* skládá ze dvou nebo tří číslic, které představují osmičkový znakový kód. Například `\040` představuje znak mezery. Tato konstrukce je interpretována jako zpětný odkaz, `\2`pokud má pouze jednu číslici (například) nebo pokud odpovídá počtu zachytávající skupiny. (Viz [Konstrukce zpětného odkazu](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x`*nn*|Odpovídá znaku ASCII, kde *nn* je dvoumístný hexadecimální znakový kód.|  
|`\c` *×*|Odpovídá řídicímu znaku ASCII, kde X je písmeno řídicího znaku. Například `\cC` je CTRL-C.|  
|`\u`*nnnn*|Odpovídá znakové jednotce UTF-16, jejíž hodnota je *nnnn* hexadecimal. **Poznámka:**  Rozhraní 5 znaků perlu, které se používá k určení unicode, není rozhraním .NET podporováno. Perl 5 znak escape `\x{` *####* `…}`má *####* `…` tvar , kde je řada šestnáctkových číslic. Místo toho `\u`použijte *nnnn*.|  
|`\`|Následuje znak, který není rozpoznán jako řídicí znak, odpovídá tomuto znaku. Například `\*` odpovídá hvězdičkě (*) a je `\x2A`stejný jako .|  
  
## <a name="an-example"></a>Příklad  
 Následující příklad ilustruje použití znaku unikne v regulárním výrazu. Analyzuje řetězec, který obsahuje jména největších světových měst a jejich populace v roce 2009. Každý název města je oddělen od`\t`svého počtu obyvatel záložkou `\u007c`( ) nebo svislým pruhem (&#124; nebo ). Jednotlivá města a jejich populace jsou od sebe odděleny návratem vozíku a přísežným kanálem.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Regulární `\G(.+)[\t|\u007c](.+)\r?\n` výraz je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začněte zápas, kde skončila poslední shoda.|  
|`(.+)`|Porovná libovolný znak jednou nebo vícekrát. Toto je první zachytávající skupina.|  
|`[\t\u007c]`|Porovná kartu`\t`( ) nebo svislý pruh (&#124;).|  
|`(.+)`|Porovná libovolný znak jednou nebo vícekrát. Toto je druhá zachytávající skupina.|  
|`\r?\n`|Shoda nula nebo jeden výskyt konce řádku následuje nový řádek.|  
  
## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
