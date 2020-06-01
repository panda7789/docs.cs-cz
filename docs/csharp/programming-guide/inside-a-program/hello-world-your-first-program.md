---
title: Hello World – první program využívající Visual Studio ve Windows nebo v prostředí Mac – Průvodce programováním v C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 6d78ec83fec72b30f5cee398af1816d0cac35886
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241861"
---
# <a name="hello-world----your-first-program"></a>Hello World – první program

V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!" editoru. Visual Studio je profesionální integrované vývojové prostředí (IDE) s řadou funkcí navržených pro vývoj pro .NET. K vytvoření tohoto programu použijete pouze několik funkcí v aplikaci Visual Studio. Další informace o aplikaci Visual Studio naleznete v tématu [Začínáme v jazyce Visual C#](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Vytvoření nové aplikace

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Spusťte Visual Studio. Ve Windows se zobrazí následující obrázek:

![Úvodní obrazovka sady Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Vyberte **vytvořit nový projekt** v pravém dolním rohu obrázku. Visual Studio zobrazí dialogové okno **Nový projekt** :

![Obrazovka nového projektu v aplikaci Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Pokud jste spustili aplikaci Visual Studio poprvé, seznam **naposledy použitých šablon projektů** je prázdný.

V dialogovém okně Nový projekt zvolte možnost Konzolová aplikace (.NET Core) a potom stiskněte tlačítko **Další**. Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.

Visual Studio otevře projekt. Už je základní "Hello World!". případě. Stisknutím klávesy `Ctrl`  +  `F5` spusťte projekt. Visual Studio sestaví projekt a převede zdrojový kód na spustitelný soubor. Potom spustí příkazové okno, které spustí vaši novou aplikaci. V okně byste měli vidět následující text:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Stisknutím klávesy zavřete okno.

# <a name="macos"></a>[macOS](#tab/macos)

Spusťte Visual Studio pro Mac. Na Macu se zobrazí následující obrázek:

![Úvodní obrazovka sady Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Pokud Visual Studio pro Macte poprvé, seznam **posledních projektů** je prázdný.

V pravém horním rohu obrázku vyberte **Nový** . Visual Studio pro Mac zobrazí dialog **Nový projekt** :

![Obrazovka nového projektu v aplikaci Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

V dialogovém okně Nový projekt vyberte .NET Core a Konzolová aplikace a pak klikněte na **Další**. Bude nutné vybrat cílovou architekturu. Ve výchozím nastavení je to v pořádku, takže stiskněte tlačítko Další. Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**. Můžete použít výchozí umístění projektu. Nepřidávat tento projekt do správy zdrojových kódů.

Visual Studio pro Mac otevře projekt. Už je základní "Hello World!". případě. Stisknutím klávesy `Ctrl`  +  `Fn`  +  `F5` spusťte projekt. Visual Studio pro Mac sestavit projekt a převod zdrojového kódu na spustitelný soubor. Potom spustí příkazové okno, které spustí vaši novou aplikaci. V okně byste měli vidět následující text:

```console
Hello World!

Press any key to close this window . . .
```

Ukončete relaci stisknutím klávesy.

---

## <a name="elements-of-a-c-program"></a>Prvky programu v jazyce C#

Pojďme se podívat na důležité části tohoto programu. První řádek obsahuje komentář. Znaky `//` převedou zbytek čáry na komentář.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Můžete také odkomentovat blok textu uzavřením mezi `/*` `*/` znaky a. To je ukázáno v následujícím příkladu.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Konzolová aplikace v jazyce C# musí obsahovat `Main` metodu, ve které ovládací prvek začíná a končí. `Main`Metoda je místo, kde vytvoříte objekty a spustíte jiné metody.

`Main`Metoda je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury. V předchozím "Hello World!" například se nachází ve třídě s názvem `Hello` . Metodu lze deklarovat `Main` jedním z následujících způsobů:

- Může vracet `void` . To znamená, že váš program nevrací hodnotu.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Může také vracet celé číslo. Celé číslo je **ukončovací kód** vaší aplikace.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- U obou návratových typů může vzít v úvahu argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-nebo-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` metody, `args` , je `string` pole, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu.

Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Vstup a výstup

Programy v jazyce C# obecně používají vstupní a výstupní služby, které poskytuje běhová knihovna rozhraní .NET. Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metodu. Toto je jedna z výstupních metod <xref:System.Console> třídy v knihovně run-time. Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem. Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace. Pokud zadáte `using System;` direktivu na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich úplného zařazení. Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine` :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Další informace o metodách vstupu a výstupu naleznete v tématu <xref:System.IO> .

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Ukázky a kurzy](../../../samples-and-tutorials/index.md)
- [Argumenty Main () a příkazového řádku](../main-and-command-args/index.md)
- [Začínáme s Visual C #](/visualstudio/ide/quickstart-csharp-console)
