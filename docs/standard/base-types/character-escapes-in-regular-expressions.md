---
title: Řídicí sekvence znaků v regulárních výrazech .NET
description: Přečtěte si o speciálních znacích a řídicích znacích v regulárních výrazech .NET.
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
ms.custom: seodec18
ms.openlocfilehash: 248d434f7aad56d84d952fa27cf49f3d370f4a1c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934833"
---
# <a name="character-escapes-in-regular-expressions"></a>Řídicí sekvence znaků v regulárních výrazech
Zpětné lomítko (\\) v regulárním výrazu označuje jednu z následujících možností:  
  
- Znak, který následuje, je speciální znak, jak je znázorněno v tabulce v následující části. Například `\b` je kotva, která označuje, že by se měla shoda regulárního výrazu začínat na hranici `\t` slova, představuje kartu a `\x020` představuje mezeru.  
  
- Znak, který by byl jinak interpretován jako neřídicí konstrukce jazyka, by měl být interpretován doslova. Například složené závorky (`{`) zahájí definici kvantifikátoru, ale zpětné lomítko následované složenou závorkou (`\{`) označuje, že se modul regulárních výrazů musí shodovat s závorkou. Podobně jedno zpětné lomítko označuje začátek řídicí konstrukce jazyka, ale dvě zpětná lomítka (`\\`) označují, že se modul regulárních výrazů musí shodovat s zpětným lomítkem.  
  
> [!NOTE]
> Řídicí znaky se rozpoznávají v vzorcích regulárních výrazů, ale ne v vzorech pro nahrazení.  
  
## <a name="character-escapes-in-net"></a>Řídicí sekvence znaků v .NET  
 V následující tabulce jsou uvedeny znaková řídicí sekvence podporovaná regulárními výrazy v rozhraní .NET.  
  
|Znak nebo sekvence|Popis|  
|---------------------------|-----------------|  
|Všechny znaky kromě následujících:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Jiné znaky než ty, které jsou uvedeny ve sloupci **Character nebo Sequence** , nemají v regulárních výrazech žádný zvláštní význam; samy se shodují.<br /><br /> Znaky zahrnuté ve sloupci **Character nebo Sequence** jsou speciální prvky jazyka regulárních výrazů. Aby se shodovaly s regulárním výrazem, musí být uvozeny řídicími znaky nebo zahrnuty do [skupiny pozitivních znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Například regulární výraz `\$\d+` nebo `[$]\d+` odpovídá "$1200".|  
|`\a`|Odpovídá znaku zvonku (alarm), `\u0007`.|  
|`\b`|Ve třídě znaků *character_group* `]` odpovídá znaku Backspace, `\u0008`. `[`  (Viz [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Mimo třídu `\b` znaků je kotva, která odpovídá hranici slova. (Viz [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Odpovídá kartě, `\u0009`.|  
|`\r`|Odpovídá znaku návratu `\u000D`na začátek řádku. Všimněte si `\r` , že se nerovná znaku nového řádku `\n`,.|  
|`\v`|Odpovídá svislé kartě `\u000B`.|  
|`\f`|Odpovídá posunu `\u000C`formuláře.|  
|`\n`|Odpovídá novému řádku `\u000A`.|  
|`\e`|Odpovídá řídicímu znaku `\u001B`,.|  
|`\`*NNN*&#124; Odpovídá znaku ASCII, kde *NNN* sestává ze dvou nebo tří číslic, které reprezentují osmičkový kód znaku. Například `\040` představuje znak mezery. Tato konstrukce je interpretována jako zpětný odkaz, pokud má pouze jednu číslici (například `\2`) nebo, pokud odpovídá číslu zachytávající skupiny. (Viz [konstrukce zpětných odkazů](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Odpovídá znaku ASCII, kde *NN* je dvouciferné hexadecimální kód znaku.|  
|`\c` *X*|Odpovídá řídicímu znaku ASCII, kde X je písmeno řídicího znaku. Například `\cC` je CTRL-C.|  
|`\u` *nnnn*|Odpovídá jednotce kódu UTF-16, jejíž hodnota je *nnnn* hexadecimální. **Poznámka:**  Rozhraní .NET nepodporuje řídicí znak "Perl 5", který se používá k zadání kódování Unicode. Řídicí znak jazyka Perl 5 `\x{`má formulář *####* `…}`, kde *####* `…` je řada hexadecimálních číslic. Místo toho použijte `\u` *nnnn*.|  
|`\`&#124; Pokud následuje znak, který není rozpoznán jako řídicí znak, odpovídá tomuto znaku. Například `\*` odpovídá znaku hvězdička (*) a je stejný jako `\x2A`.|  
  
## <a name="an-example"></a>Příklad  
 Následující příklad ukazuje použití znakových řídicích znaků v regulárním výrazu. Analyzuje řetězec, který obsahuje názvy největších měst a jejich populace na světě v 2009. Název každého města je oddělený od jeho populace tabulátorem (`\t`) nebo svislým pruhem&#124; ( `\u007c`nebo). Jednotlivá města a jejich populace jsou vzájemně oddělené návratem na začátek řádku a řádkovým kanálem.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Regulární výraz `\G(.+)[\t|\u007c](.+)\r?\n` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\G`|Zahajte shodu s koncem poslední shody.|  
|`(.+)`|Porovnává libovolný znak jednou nebo vícekrát. Toto je první zachytávající skupina.|  
|`[\t\u007c]`|Porovnává s tabulátorem (`\t`) nebo svislým pruhem (&#124;).|  
|`(.+)`|Porovnává libovolný znak jednou nebo vícekrát. Toto je druhá zachytávající skupina.|  
|`\r?\n`|Porovná žádný nebo jeden výskyt návratového znaku následovaný novým řádkem.|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
