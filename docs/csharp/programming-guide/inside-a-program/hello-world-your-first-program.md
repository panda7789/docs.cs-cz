---
title: "Hello World! -- váš první program (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1b6511394e69edd344c4f4a1bbc9da549a1a2a17
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World! -- váš první program (Průvodce programováním v C#)
Následující postup vytvoří C# verze tradiční "Hello, World!" program. Program zobrazí řetězec`Hello World!`  
  
 Další příklady úvodní koncepty, najdete v části [Začínáme s Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>Vytvoření a spuštění konzolové aplikace  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  Rozbalte položku **nainstalovaná**, rozbalte položku **šablony**, rozbalte položku **Visual C#**a potom zvolte **konzolové aplikace**.  
  
4.  V **název** pole, zadejte název pro svůj projekt a potom zvolte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5.  Pokud není otevřen v souboru Program.cs **Editor kódu**, otevřete místní nabídku pro **Program.cs** v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.  
  
6.  Nahraďte obsah souboru Program.cs následujícím kódem.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Zvolte klávesu F5 a spusťte projekt. Zobrazí se okno příkazového řádku, která obsahuje řádek`Hello World!`  
  
 V dalším kroku se zkontrolují důležité části tohoto programu.  
  
## <a name="comments"></a>Komentáře  
 První řádek obsahuje komentář. Znaky `//` převést zbytek řádku na komentář.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Můžete také Zakomentovat blok textu uveden mezi `/*` a `*/` znaků. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Main – metoda  
 Musí obsahovat konzolovou aplikaci C# `Main` metoda, ve kterém řízení spuštění a ukončení. `Main` Je metoda, kde vytvářet objekty a provést další metody.  
  
 `Main` Je metoda [statické](../../../csharp/language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury. V předchozích "Hello World!" například se nachází v třídy s názvem `Hello`. Je možné deklarovat `Main` metoda v jednom z následujících způsobů:  
  
-   Může vrátit `void`.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Také se může vrátit celé číslo.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Některým z návratové typy může trvat argumenty.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     -nebo-  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Parametr `Main` metody `args`, je `string` pole, které obsahuje argumenty příkazového řádku, použije k vyvolání programu. Na rozdíl od v jazyce C++ pole neobsahuje název souboru spustitelný soubor (exe).  
  
 Další informace o tom, jak používat argumenty příkazového řádku, podívejte se na příklady v [Main() a příkazového řádku argumenty](../../../csharp/programming-guide/main-and-command-args/index.md) a [postupy: vytvoření a použití sestavení pomocí příkazu řádek](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
 Volání <xref:System.Console.ReadKey%2A> na konci `Main` metoda zabraňuje v okně konzoly zavřením předtím, než budete mít možnost číst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.  
  
## <a name="input-and-output"></a>Vstup a výstup  
 Programy C# obecně používat vstupu a výstupu služeb poskytovaných běhové knihovny rozhraní .NET Framework. Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metoda. Toto je jedna z metod výstup <xref:System.Console> třídy v běhové knihovny. Zobrazí jeho parametr řetězce na standardní výstupní datový proud, za nímž následuje nový řádek. Další <xref:System.Console> metody jsou k dispozici pro jinou vstupní a výstupní operace. Pokud zahrnete `using System;` direktivy na začátku tohoto programu, můžete přímo použít <xref:System> třídy a metody bez plně kvalifikovaného je. Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine`:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Další informace o metodách vstupu a výstupu, najdete v části <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Kompilace a provádění na příkazovém řádku  
 Zkompilujete "Hello World!" program pomocí příkazového řádku místo prostředí Visual Studio integrované vývoj prostředí (IDE).  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>Kompilace a spuštění z příkazového řádku  
  
1.  Vložit do libovolného textového editoru kódu v předchozím postupu a pak soubor uložte jako textový soubor. Název souboru `Hello.cs`. Soubory zdrojového kódu C# pomocí rozšíření `.cs`.  
  
2.  Proveďte jeden z následujících kroků otevřete okno příkazového řádku:  
  
    -   Ve Windows 10 na **spustit** nabídky, vyhledejte `Developer Command Prompt`a potom klepněte na nebo zvolte **příkazový řádek vývojáře pro VS 2017**.  
  
         Zobrazí se okno příkazového řádku vývojáře.  
  
    -   V systému Windows 7, otevřete **spustit** nabídky, rozbalte složku s aktuální verzí sady Visual Studio, otevřete místní nabídku pro **nástroje sady Visual Studio**a potom zvolte **příkazový řádek vývojáře pro VS 2017**.  
  
         Zobrazí se okno příkazového řádku vývojáře.  
  
    -   Povolte sestavení příkazového řádku z standardní okno příkazového řádku.  
  
         V tématu [postupy: nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  V okně příkazového řádku přejděte do složky, která obsahuje vaše `Hello.cs` souboru.  
  
4.  Zadejte následující příkaz pro kompilaci `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Pokud váš program nejsou žádné chyby kompilace, spustitelný soubor, který je pojmenován `Hello.exe` je vytvořena.  
  
5.  V okně příkazového řádku zadejte následující příkaz pro spuštění programu:  
  
     `Hello`  
  
 Další informace o kompilátor jazyka C# a její možnosti najdete v tématu [možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [V programu v jazyce C#](../../../csharp/programming-guide/inside-a-program/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)  
 [\<paveover > C# ukázkové aplikace](http://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Začínáme s jazykem Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
