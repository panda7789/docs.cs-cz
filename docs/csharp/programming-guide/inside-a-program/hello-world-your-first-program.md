---
title: Hello World! -- váš první program (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 90f0ec6b88a2822cb3429948681c76c70f3d3f18
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339393"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World! -- váš první program (Průvodce programováním v C#)
Následující postup vytvoří verzi C# tradiční "Hello World!" program. Program zobrazí řetězec `Hello World!`  
  
 Další příklady úvodních konceptů viz [Začínáme s Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>Vytvoření a spuštění konzolové aplikace  
  
1.  Spusťte sadu Visual Studio.  
  
2.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  Rozbalte **nainstalováno**, rozbalte **šablony**, rozbalte **Visual C#** a klikněte na tlačítko **konzolovou aplikaci**.  
  
4.  V **název** pole, zadejte název pro váš projekt a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
5.  Pokud Program.cs není otevřen v **Editor kódu**, otevřete místní nabídku pro **Program.cs** v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.  
  
6.  Nahraďte obsah Program.cs následujícím kódem.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Stiskněte klávesu F5 ke spuštění projektu. Zobrazí se okno příkazového řádku, která obsahuje řádek `Hello World!`  
  
 Dále jsou zkoumány důležité části tohoto programu.  
  
## <a name="comments"></a>Komentáře  
 První řádek obsahuje komentář. Znaky `//` převést zbytek řádku na poznámku.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Můžete také můžete Zakomentovat blok textu jeho uzavřením mezi `/*` a `*/` znaků. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Main – metoda  
 Musí obsahovat konzolovou aplikaci C# `Main` metody, ve kterém ovládací prvek začíná a končí. `Main` Je metoda, ve kterém se vytváří objekty a spouštějí jiné metody.  
  
 `Main` Je metoda [statické](../../../csharp/language-reference/keywords/static.md) metodu, která se nachází uvnitř třídy nebo struktury. V předchozí "Hello World!" například se nachází ve třídě s názvem `Hello`. Lze deklarovat `Main` metody v jednom z následujících způsobů:  
  
-   Může vrátit `void`.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Také může vrátit celé číslo.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Pomocí některé z návratových typů můžete převzít argumenty.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     -nebo-  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Parametr `Main` metody `args`, je `string` pole obsahující argumenty příkazového řádku používané k vyvolání programu. Na rozdíl od v jazyce C++ pole neobsahuje název souboru spustitelný soubor (exe).  
  
 Další informace o tom, jak používat argumenty příkazového řádku, podívejte se na příklady v [Main() a argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md) a [postupy: vytvoření a použití sestavení pomocí řádek příkazu](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
 Volání <xref:System.Console.ReadKey%2A> na konci `Main` metody zabrání v okně konzoly se ukončit dříve, než máte možnost si přečíst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.  
  
## <a name="input-and-output"></a>Vstup a výstup  
 C# obvykle používají vstupní a výstupní služby poskytované knihovny run-time rozhraní .NET Framework. Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metody. Toto je jedna z metod výstupu <xref:System.Console> třídy do knihovny run-time. Zobrazuje svůj parametr řetězce v datovém proudu standardního výstupu následovaný novým řádkem. Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace. Pokud zahrnete `using System;` direktiv na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich plné kvalifikace. Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine`:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Další informace o vstupních/výstupních metodách naleznete v tématu <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Kompilace a provádění na příkazovém řádku  
 Můžete kompilovat "Hello World!" program pomocí příkazového řádku namísto Visual Studio integrované vývojové prostředí (IDE).  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>Kompilace a spuštění z příkazového řádku  
  
1.  Vložte kód z předchozího postupu do libovolného textového editoru a uložte soubor jako textový soubor. Název souboru `Hello.cs`. Soubory zdrojového kódu jazyka C# používají příponu `.cs`.  
  
2.  Proveďte jeden z následujících kroků a otevřete okno příkazového řádku:  
  
    -   Ve Windows 10 na **Start** nabídky, vyhledejte `Developer Command Prompt`a potom klepněte nebo vyberte možnost **Developer Command Prompt for VS 2017**.  
  
         Zobrazí se okno příkazového řádku pro vývojáře.  
  
    -   Ve Windows 7, otevřete **Start** nabídka, rozbalte složku pro aktuální verzi sady Visual Studio, otevřete místní nabídku pro **Visual Studio Tools**a klikněte na tlačítko **Developer Command Prompt pro sady VS 2017**.  
  
         Zobrazí se okno příkazového řádku pro vývojáře.  
  
    -   Povolte sestavení příkazového řádku ze standardního okna příkazového řádku.  
  
         Zobrazit [postupy: nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  V okně příkazového řádku přejděte do složky, která obsahuje vaše `Hello.cs` souboru.  
  
4.  Zadejte následující příkaz pro kompilaci `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Pokud program neobsahuje žádné chyby během kompilace, spustitelný soubor, který je pojmenován `Hello.exe` se vytvoří.  
  
5.  V okně příkazového řádku zadejte následující příkaz pro spuštění programu:  
  
     `Hello`  
  
 Další informace o kompilátoru C# a jeho možnostech naleznete v tématu [možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [V programu v jazyce C#](../../../csharp/programming-guide/inside-a-program/index.md)  
- [Řetězce](../../../csharp/programming-guide/strings/index.md)  
- [\<paveover > ukázkové aplikace C#](https://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Začínáme s jazykem Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
