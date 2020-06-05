---
title: Název '<name>' není deklarován.
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 6fa4639b97e4314d8752ae520e94a58a189b7cbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397165"
---
# <a name="name-name-is-not-declared"></a>Název '\<name>' není deklarován.
Příkaz odkazuje na programovací prvek, ale kompilátor nemůže najít element s tímto přesným názvem.  
  
 **ID chyby:** BC30451  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte pravopis názvu v odkazujícím příkazu. Visual Basic rozlišuje velká a malá písmena, ale jakékoli jiné variace v pravopisu se považují za úplně jiný název. Všimněte si, že podtržítko ( `_` ) je součástí názvu a je proto součástí pravopisu.  
  
2. Ověřte, zda máte operátor přístupu členů ( `.` ) mezi objektem a jeho členem. Například pokud máte <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1` , pro přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnosti byste měli zadat `TextBox1.Text` . Pokud místo toho zadáte `TextBox1Text` , vytvořili jste jiný název.  
  
3. Pokud je pravopis správné a syntaxe jakéhokoli přístupu ke členu objektu je správná, ověřte, zda byl prvek deklarován. Další informace naleznete v tématu [deklarované elementy](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Pokud byl deklarován element, ověřte, zda je v oboru. Pokud je odkazující příkaz mimo oblast, která deklaruje prvek programování, může být nutné kvalifikovat název elementu. Další informace najdete v tématu věnovaném [oboru v Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Pokud nepoužíváte plně kvalifikovaný typ nebo typ a název členu (například váš kód odkazuje na vlastnost `MethodInfo.Name` namísto `System.Reflection.MethodInfo.Name` ), přidejte [příkaz Imports](../statements/imports-statement-net-namespace-and-type.md).

6. Pokud se pokoušíte zkompilovat projekt ve stylu sady SDK (projekt se \* souborem. vbproj, který začíná na řádku `<Project Sdk="Microsoft.NET.Sdk">` ), a chybová zpráva odkazuje na typ nebo člen v sestavení Microsoft. VisualBasic. dll, nakonfigurujte svou aplikaci tak, aby byla zkompilována s odkazem na knihovnu modulu runtime Visual Basic. Ve výchozím nastavení je podmnožina knihovny vložena do sestavení v projektu ve stylu sady SDK.

   Například následující příklad se nepodaří zkompilovat, protože <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> nelze nalézt metodu. Není vložen do podmnožiny modulu runtime Visual Basic, který je součástí vaší aplikace.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Chcete-li tuto chybu vyřešit, přidejte `<VBRuntime>Default</VBRuntime>` prvek do `<PropertyGroup>` části projekty, jak ukazuje následující soubor Visual Basic projektu.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Viz také

- [Souhrn deklarací a konstant](../keywords/declarations-and-constants-summary.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
- [Deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
