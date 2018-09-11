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
ms.openlocfilehash: 9b390b1d3d935ad045d59dd6b3d2e42cdbe82dd7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262250"
---
# <a name="character-escapes-in-regular-expressions"></a>Řídicí sekvence znaků v regulárních výrazech
Zpětné lomítko (\\) v regulárním výrazu označuje jeden z následujících akcí:  
  
-   Že následující znak je speciální znaky, jak je znázorněno v tabulce v části. Například `\b` kotva, která označuje, že shoda s regulárním výrazem by měla začínat na hranici slova `\t` představuje kartu, a `\x020` představuje mezeru.  
  
-   Znak, který by jinak interpretován jako znak bez řídícího jazykové konstrukce by měl být interpretován literálně. Například složenou závorku (`{`) začíná definici kvantifikátor, ale zpětné lomítko následované složená závorka (`\{`) označuje, že modul regulárních výrazů by měl odpovídat složenou závorkou. Obdobně jedno zpětné lomítko označuje začátek toho uvozený uvozovacím znakem jazykové konstrukce, ale dvě zpětná lomítka (`\\`) označuje, že modul regulárních výrazů by měl odpovídat zpětné lomítko.  
  
> [!NOTE]
>  Řídicí sekvence znaků, jsou rozpoznány ve vzorech regulárního výrazu, ale ne ve vzorech pro nahrazení.  
  
## <a name="character-escapes-in-net"></a>Řídicí sekvence znaků v rozhraní .NET  
 V následující tabulce jsou uvedeny řídicí sekvence znaků, které jsou podporované regulárními výrazy v rozhraní .NET.  
  
|Znak nebo posloupnost|Popis|  
|---------------------------|-----------------|  
|Všechny znaky s výjimkou následujících:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Jiné znaky než hodnotami uvedenými v **znak nebo posloupnost** sloupce nemají zvláštní význam v regulární výrazy, aby odpovídaly sami.<br /><br /> Znaky součástí **znak nebo posloupnost** sloupce jsou prvky jazyka regulárních výrazů speciální. Tak, aby odpovídaly je v regulárním výrazu, musí být uvozeny řídicími znaky nebo součástí [pozitivní skupina znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Například regulární výraz `\$\d+` nebo `[$]\d+` odpovídá "$1200".|  
|`\a`|Odpovídá znaku Zvonek (alarm) `\u0007`.|  
|`\b`|V `[` *character_group* `]` třídy, odpovídá znaku backspace znak `\u0008`.  (Viz [znaku třídy](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Mimo třídu znaků `\b` kotva, která odpovídá hranici slova. (Viz [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Odpovídá znaku tabulátoru `\u0009`.|  
|`\r`|Odpovídá návratu `\u000D`. Všimněte si, že `\r` není ekvivalentní znaku nového řádku `\n`.|  
|`\v`|Odpovídá znaku svislého tabulátoru `\u000B`.|  
|`\f`|Odpovídá form feed, `\u000C`.|  
|`\n`|Odpovídá znaku nového řádku, `\u000A`.|  
|`\e`|Odpovídá `\u001B`.|  
|`\` *nnn*|Odpovídá znaku ASCII, kde *nnn* se skládá ze dvou nebo tří číslic, které představují osmičkový kód znaku. Například `\040` představuje znak mezery. Tento konstruktor je interpretováno jako zpětný odkaz, pokud má pouze jednu číslici (například `\2`) nebo pokud to odpovídá číslu zachycující skupiny. (Viz [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Odpovídá znaku ASCII, kde *nn* je dvouciferný šestnáctkový kód znaku.|  
|`\c` *X*|Odpovídá znaku ASCII ovládací prvek, kde X je písmeno kontrolního znaku. Například `\cC` je CTRL-C.|  
|`\u` *nnnn*|Odpovídá jednotku kódu UTF-16, jehož hodnota je *nnnn* šestnáctkové. **Poznámka:** znak escape jazyka Perl 5, který se používá k určení kódování Unicode nepodporuje rozhraní .NET. Znak escape jazyka Perl 5 má formát `\x{` *####* `…}`, kde *####* `…` je řada šestnáctkových číslic. Místo toho použijte `\u` *nnnn*.|  
|`\`|Pokud následuje znak, který nebyl rozpoznán jako řídicí znak, odpovídá danému znaku. Například `\*` odpovídá hvězdičku (*) a je stejný jako `\x2A`.|  
  
## <a name="an-example"></a>Příklad  
 Následující příklad ukazuje použití řídicí sekvence znaků v regulárních výrazů. Analyzuje řetězec, který obsahuje názvy měst největší na světě a jejich plnění v roce 2009. Každý název města je oddělen od jeho naplnění kartu (`\t`) nebo svislá čára (&#124; nebo `\u007c`). Jednotlivá města a jejich plnění jsou od sebe navzájem oddělené zalomení řádku a odřádkování.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Regulární výraz `\G(.+)[\t|\u007c](.+)\r?\n` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Začnete porovnáváním tam, kde poslední shody ukončeno.|  
|`(.+)`|Odpovídá jakémukoli znaku jednou nebo vícekrát. Toto je první zachytávající skupina.|  
|`[\t\u007c]`|Odpovídá na kartě (`\t`) nebo svislá čára (&#124;).|  
|`(.+)`|Odpovídá jakémukoli znaku jednou nebo vícekrát. Toto je druhá zachytávající skupina.|  
|`\r?\n`|Porovná žádný nebo jeden výskyt zalomení řádku a nový řádek.|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
