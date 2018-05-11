---
title: Řídicí sekvence znaků v regulárních výrazech
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebdcda655a186d54065e98f8b9c5c7ae2fda4955
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="character-escapes-in-regular-expressions"></a>Řídicí sekvence znaků v regulárních výrazech
Zpětné lomítko (\\) v regulárním výrazu označuje jeden z následujících:  
  
-   Znak, který následuje je speciální znaky, jak je znázorněno v tabulce v následující části. Například `\b` je kotva, která označuje, že shoda s regulárním výrazem by měl začínat na hranici slova `\t` představuje na kartě a `\x020` představuje mezeru.  
  
-   Znak, který by jinak interpretují jako neuvozené jazyk konstrukce by měl být interpretován oznámena. Například složená závorka (`{`) začíná definici kvantifikátoru, ale zpětné lomítko následované složená závorka (`\{`) označuje, že modul regulárních výrazů by měl odpovídat závorek. Podobně jedno zpětné lomítko označuje začátek řídící jazykové konstrukce, ale dvě zpětná lomítka (`\\`) označuje, že modul regulární výraz by měl odpovídat zpětné lomítko.  
  
> [!NOTE]
>  Řídicí sekvence znaků, se rozpoznávají vzorce regulárního výrazu, ale není v vzory pro nahrazování.  
  
## <a name="character-escapes-in-net"></a>Řídicí sekvence znaků v rozhraní .NET  
 Následující tabulka uvádí řídicí sekvence znaků, které jsou podporované regulární výrazy v rozhraní .NET.  
  
|Znak nebo pořadí|Popis|  
|---------------------------|-----------------|  
|Všechny znaky s výjimkou následující:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \|Znaky, které nejsou uvedeny v **znak nebo pořadí** sloupec mít žádný speciální význam v regulárních výrazech; odpovídají sami.<br /><br /> Znaky, které jsou součástí **znak nebo pořadí** sloupce jsou prvky jazyka speciální regulární výraz. Tak, aby odpovídaly je v regulárním výrazu, které musí být uvozené nebo součástí [skupina kladné znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Například regulární výraz `\$\d+` nebo `[$]\d+` odpovídá "$1200".|  
|`\a`|Znak zvonku (alarm), odpovídá `\u0007`.|  
|`\b`|V `[` *character_group* `]` znak třídy, odpovídá a backspace, `\u0008`.  (Viz [znak třídy](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Mimo třídu znaků `\b` kotva, která odpovídá hranici slova. (Viz [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Odpovídá na kartě `\u0009`.|  
|`\r`|Odpovídá návratu, `\u000D`. Všimněte si, že `\r` není ekvivalentní znak nového řádku `\n`.|  
|`\v`|Odpovídá vertikální tabulátor `\u000B`.|  
|`\f`|Odpovídá posunu, `\u000C`.|  
|`\n`|Odpovídá nový řádek, `\u000A`.|  
|`\e`|Odpovídá escape, `\u001B`.|  
|`\` *nnn*|Odpovídá znaku ASCII, kde *nnn* se skládá ze dvou nebo tří číslic, které představují kód osmičková znak. Například `\040` představuje znak mezery. Tento konstruktor je interpretován jako zpětný odkaz, pokud má jenom jednu číslici (například `\2`) nebo pokud ji odpovídá číslu zachytávající skupiny. (Viz [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Odpovídá znaku ASCII, kde *nn* je kód letopočty hexadecimálních znaků.|  
|`\c` *X*|Odpovídá znaku řízení ASCII, kde X je písmeno řídicí znak. Například `\cC` je CTRL-C.|  
|`\u` *nnnn*|Odpovídá jednotce kódu UTF-16, jehož hodnota je *nnnn* hexadecimální. **Poznámka:** Perl 5 řídicí znak, který slouží k určení kódování Unicode nepodporuje rozhraní .NET. Řídicí znak Perl 5 má tvar `\x{` *####* `…}`, kde *####* `…` je řada šestnáctkových číslic. Místo toho použijte `\u` *nnnn*.|  
|`\`|Když následuje znak, který není rozpoznaný jako řídící znak, odpovídá tento znak. Například `\*` odpovídá znak hvězdičky (*) a je stejná jako `\x2A`.|  
  
## <a name="an-example"></a>Příklad  
 Následující příklad ukazuje použití řídicí sekvence znaků v regulárním výrazu. Analyzuje řetězec, který obsahuje názvy města největší na světě a jejich plnění v 2009. Každý název města je oddělená od jeho naplnění na kartě (`\t`) nebo svislá čára (&#124; nebo `\u007c`). Jednotlivá města a jejich plnění jsou od sebe navzájem oddělené návrat na začátek a odřádkování.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Regulární výraz `\G(.+)[\t|\u007c](.+)\r?\n` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začněte shoda, kde poslední porovnávání ukončeno.|  
|`(.+)`|Porovná libovolný znak jeden či více krát. Toto je první zachytávající skupina.|  
|`[\t\u007c]`|Na kartě odpovídat (`\t`) nebo svislá čára (&#124;).|  
|`(.+)`|Porovná libovolný znak jeden či více krát. Toto je druhá zachytávající skupina.|  
|`\r?\n`|Porovná nula nebo jeden výskyt návrat následuje nový řádek.|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
