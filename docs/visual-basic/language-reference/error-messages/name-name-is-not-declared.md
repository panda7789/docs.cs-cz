---
title: Název &#39; &lt;název&gt; &#39; není deklarována
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e52b93980cfc2d162d35b86bd93ce9eeb9875c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574817"
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Název &#39; &lt;název&gt; &#39; není deklarována
Příkaz odkazuje na programovací prvek, ale kompilátor nemůže najít element s tímto názvem přesné.  
  
 **ID chyby:** BC30451  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte, zda název v odkazující příkazu. Visual Basic je velká a malá písmena, ale jiné kolísání pravopis se považuje za zcela jiný název. Všimněte si, že podtržítko (`_`) je součástí názvu a proto součástí pravopis.  
  
2. Zkontrolujte, zda je operátor přístupu členů (`.`) mezi objekt a jeho členů. Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1`, pro přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnost byste měli zadat `TextBox1.Text`. Pokud místo toho zadejte `TextBox1Text`, vytvoříte jiný název.  
  
3. Pokud správně a správnost syntaxe jakékoli přístup ke členu objektu, ověřte, že element byl deklarován. Další informace najdete v tématu [deklarované elementy](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Pokud je deklarovaný programovací element, zkontrolujte, že se nachází v oboru. Pokud je mimo oblast deklarace programovací element odkazující příkaz, můžete potřebovat kvalifikovat název elementu. Další informace najdete v tématu [obor v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Pokud nechcete použít plně kvalifikovaný typ nebo název typů a členů (například váš kód odkazuje na vlastnost jako `MethodInfo.Name` místo `System.Reflection.MethodInfo.Name`), přidejte [Imports – příkaz](../statements/imports-statement-net-namespace-and-type.md).

6. Pokud se pokoušíte ke kompilaci projektu aplikace sady SDK – vizuální styl (projekt se \*.vbproj soubor, který začíná na řádku `<Project Sdk="Microsoft.NET.Sdk">`) a chybová zpráva se odkazuje na typ nebo člen v sestavení knihovny Microsoft.VisualBasic.dll, konfigurace aplikace pro Kompilovat s odkazem na knihovnu Runtime jazyka Visual Basic. Ve výchozím nastavení podmnožina knihovny je součástí vašeho sestavení v sadě SDK – vizuální styl projektu.

   Například následující příklad nejde zkompilovat, protože <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> metoda nebyla nalezena. Není součástí dílčí modul Runtime jazyka Visual Basic součástí vaší aplikace.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   Chcete-li vyřešit tuto chybu, přidejte `<VBRuntime>Default</VBRuntime>` elementu k projektům `<PropertyGroup>` části, jak ukazuje následující soubor projektu jazyka Visual Basic.

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Viz také:

- [Souhrn deklarací a konstant](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
