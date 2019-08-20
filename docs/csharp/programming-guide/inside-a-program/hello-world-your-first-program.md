---
title: Hello World – první programový průvodce C# programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589371"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World – první program (C# Průvodce programováním)

Následující postup vytvoří C# verzi tradičního "Hello World!" editoru. Program zobrazí řetězec`Hello World!`

Další příklady úvodních konceptů naleznete v tématu [Začínáme with C# Visual and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Vytvoření a spuštění konzolové aplikace

1. Spusťte Visual Studio.

2. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

3. Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **C#vizuál**a pak zvolte možnost konzolová **aplikace**.

4. Do pole **název** zadejte název projektu a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

5. Pokud Program.cs není otevřen v **editoru kódu**, otevřete místní nabídku pro **program.cs** v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.

6. Obsah Program.cs nahraďte následujícím kódem.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Kliknutím na klávesu F5 spusťte projekt. Zobrazí se okno příkazového řádku, které obsahuje řádek.`Hello World!`

V dalším kroku se zkontrolují důležité části tohoto programu.

## <a name="comments"></a>Komentáře

První řádek obsahuje komentář. Znaky `//` převedou zbytek čáry na komentář.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Můžete také odkomentovat blok textu uzavřením mezi `/*` znaky a. `*/` To je ukázáno v následujícím příkladu.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>main – metoda

C# Konzolová aplikace musí obsahovat `Main` metodu, ve které ovládací prvek začíná a končí. `Main` Metoda je místo, kde vytvoříte objekty a spustíte jiné metody.

Metoda je statická metoda, která se nachází uvnitř třídy nebo struktury. [](../../language-reference/keywords/static.md) `Main` V předchozím "Hello World!" například se nachází ve třídě s názvem `Hello`. `Main` Metodu lze deklarovat jedním z následujících způsobů:

- Může vracet `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Může také vracet celé číslo.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- U obou návratových typů může vzít v úvahu argumenty.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     -nebo-

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` metody, `args`, je `string` pole, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu. Na rozdíl od C++, pole nezahrnuje název spustitelného souboru (exe).

Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md) a [How to: Vytvořte a použijte sestavení pomocí příkazového řádku](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

Volání <xref:System.Console.ReadKey%2A> na konci `Main` metody zabraňuje oknu v zavření okna konzoly před tím, než budete mít možnost číst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.

## <a name="input-and-output"></a>Vstup a výstup

C#programy obecně používají vstupní a výstupní služby, které poskytuje knihovna run-time .NET Framework. `System.Console.WriteLine("Hello World!");` Příkaz<xref:System.Console.WriteLine%2A> používá metodu. Toto je jedna z výstupních metod <xref:System.Console> třídy v knihovně run-time. Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem. Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace. Pokud zadáte <xref:System>direktivu na začátku programu, můžete přímo použít třídy a metody bez jejich úplného zařazení. `using System;` Například můžete volat `Console.WriteLine` `System.Console.WriteLine`místo:

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Další informace o metodách vstupu a výstupu naleznete v <xref:System.IO>tématu.

## <a name="command-line-compilation-and-execution"></a>Kompilace a provádění příkazového řádku

Můžete zkompilovat "Hello World!" program pomocí příkazového řádku namísto integrovaného vývojového prostředí (IDE) sady Visual Studio.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Kompilace a spuštění z příkazového řádku

1. Vložte kód z předchozího postupu do libovolného textového editoru a pak soubor uložte jako textový soubor. Pojmenujte soubor `Hello.cs`. C#soubory zdrojového kódu používají rozšíření `.cs`.

2. K otevření okna příkazového řádku proveďte jeden z následujících kroků:

    - Ve Windows 10 v nabídce **Start** vyhledejte `Developer Command Prompt`a potom klepněte nebo zvolte **Developer Command Prompt pro vs 2017**.

         Zobrazí se okno Developer Command Prompt.

    - V systému Windows 7 otevřete nabídku **Start** , rozbalte složku pro aktuální verzi sady Visual Studio, otevřete místní nabídku pro **Visual Studio Tools**a zvolte možnost **Developer Command Prompt pro vs 2017**.

         Zobrazí se okno Developer Command Prompt.

    - Povolit buildy z příkazového řádku ze standardního okna příkazového řádku.

         Viz [jak: Nastavení proměnných prostředí pro příkazový řádek](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)sady Visual Studio.

3. V okně příkazového řádku přejděte do složky, která obsahuje váš `Hello.cs` soubor.

4. Zadejte následující příkaz, který se `Hello.cs`má zkompilovat.

     `csc Hello.cs`

     Pokud program neobsahuje žádné chyby kompilace, je vytvořen spustitelný soubor s názvem `Hello.exe` .

5. V okně příkazového řádku zadejte následující příkaz pro spuštění programu:

     `Hello`

 Další informace o C# kompilátoru a jeho možnostech naleznete v tématu [ C# možnosti kompilátoru](../../language-reference/compiler-options/index.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [V programu v jazyce C#](./index.md)
- [Řetězce](../strings/index.md)
- [Ukázky a kurzy](../../../samples-and-tutorials/index.md)
- [C#Odkaz](../../language-reference/index.md)
- [Argumenty Main() a příkazového řádku](../main-and-command-args/index.md)
- [Začínáme s jazykem Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
