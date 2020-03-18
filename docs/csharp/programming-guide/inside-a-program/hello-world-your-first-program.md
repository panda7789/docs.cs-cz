---
title: Hello World – Váš první program používající Visual Studio ve Windows nebo Macu – Průvodce programováním v Jazyce C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712140"
---
# <a name="hello-world----your-first-program"></a>Hello World - Váš první program

V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!" Program. Visual Studio je profesionální integrované vývojové prostředí (IDE) s mnoha funkcemi určenými pro vývoj rozhraní .NET. K vytvoření tohoto programu použijete pouze několik funkcí sady Visual Studio. Další informace o sadě Visual Studio najdete [v tématu Začínáme s visual c#](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Vytvoření nové aplikace

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Spusťte Visual Studio. Ve Windows se zobrazí následující obrázek:

![Úvodní obrazovka Visual Studia ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Vyberte **Vytvořit nový projekt** v pravém dolním rohu obrazu. Visual Studio zobrazí dialogové okno **Nový projekt:**

![Obrazovka nového projektu Visual Studia ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Pokud je to poprvé, co jste spustili Visual Studio, seznam **šablony posledních projektů** je prázdný.

V novém dialogovém okně projektu zvolte "Console App (.NET Core)" a stiskněte **tlačítko Další**. Pojmenujte projekt, například "HelloWorld", a stiskněte **klávesu Create**.

Visual Studio otevře projekt. Je to již základní "Hello World!" Příklad. `Ctrl`  +  Stisknutím `F5` spusťte projekt. Visual Studio vytvoří váš projekt a převede zdrojový kód na spustitelný soubor. Potom spustí příkazové okno, ve které je spuštěna nová aplikace. V okně by se měl zobrazit následující text:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Zavřete okno stisknutím klávesy.

# <a name="macos"></a>[Macos](#tab/macos)

Spusťte Visual Studio pro Mac. Na Macu se zobrazí následující obrázek:

![Úvodní obrazovka Visual Studia na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Pokud je to poprvé, co jste spustili Visual Studio pro Mac, seznam **Nedávné projekty** je prázdný.

V pravém horním rohu obrazu vyberte **Nový.** Visual Studio pro Mac zobrazí dialogové okno **Nový projekt:**

![Visual Studio nový projekt obrazovky na Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

V novém dialogovém okně projektu zvolte ".NET Core" a "Console App" a stiskněte **tlačítko Další**. Budete muset vybrat cílovou architekturu. Výchozí nastavení je v pořádku, takže stiskněte další. Pojmenujte projekt, například "HelloWorld", a stiskněte **klávesu Create**. Můžete použít výchozí umístění projektu. Nepřidávejte tento projekt do správy zdrojového kódu.

Visual Studio pro Mac otevře váš projekt. Je to již základní "Hello World!" Příklad. `Ctrl`  +  Stisknutím `Fn`  +  spusťte `F5` projekt. Visual Studio pro Mac vytvoří váš projekt a převede zdrojový kód na spustitelný soubor. Potom spustí příkazové okno, ve které je spuštěna nová aplikace. V okně by se měl zobrazit následující text:

```console
Hello World!

Press any key to close this window . . .
```

Stisknutím klávesy ukončíte relaci.

---

## <a name="elements-of-a-c-program"></a>Prvky programu Jazyka C#

Podívejme se na důležité části tohoto programu. První řádek obsahuje komentář. Znaky `//` převedou zbytek řádku na komentář.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Můžete také zakomentovat blok textu tím, `/*` že `*/` jej uzavřete mezi znaky a. To je ukázáno v následujícím příkladu.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Aplikace konzoly Jazyka C# musí obsahovat metodu, `Main` ve které ovládací prvek začíná a končí. Metoda `Main` je místo, kde můžete vytvořit objekty a spustit jiné metody.

Metoda `Main` je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury. V předchozím "Hello World!" například je umístěn ve `Hello`třídě s názvem . Metodu můžete `Main` deklarovat jedním z následujících způsobů:

- Může se `void`vrátit . To znamená, že váš program nevrátí hodnotu.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Může také vrátit celé číslo. Celé číslo je **ukončovací kód** pro vaši aplikaci.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- S jedním z návratových typů může trvat argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-nebo-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` metody , `args`je `string` pole, které obsahuje argumenty příkazového řádku použité k vyvolání programu.

Další informace o použití argumentů příkazového řádku naleznete v příkladech v [části Main() a Argumenty příkazového řádku](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Vstup a výstup

Programy jazyka C# obecně používají vstupní a výstupní služby poskytované knihovnou run-time rozhraní .NET Framework. Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metodu. Toto je jedna z <xref:System.Console> výstupních metod třídy v knihovně za běhu. Zobrazí svůj parametr řetězce ve standardním výstupním datovém proudu následovaném novým řádkem. Jiné <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace. Pokud zahrnete `using System;` směrnice na začátku programu, <xref:System> můžete přímo použít třídy a metody bez jejich plné kvalifikace. Můžete například volat `Console.WriteLine` místo `System.Console.WriteLine`:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Další informace o metodách vstupu <xref:System.IO>a výstupu naleznete v tématu .

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Ukázky a výukové programy](../../../samples-and-tutorials/index.md)
- [Argumenty Main() a příkazového řádku](../main-and-command-args/index.md)
- [Začínáme s visual c #](/visualstudio/ide/quickstart-csharp-console)
