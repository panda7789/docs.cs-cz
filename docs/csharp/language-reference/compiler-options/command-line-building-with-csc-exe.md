---
title: Sestavení z příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 68f0c12d173587e8efc0fe283617b5805c6f7eae
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877028"
---
# <a name="command-line-build-with-cscexe"></a>Sestavení z příkazového řádku s csc.exe
Kompilátor jazyka C# můžete vyvolat zadáním názvu její spustitelný soubor (*csc.exe*) z příkazového řádku.

Pokud používáte **Developer Command Prompt pro sadu Visual Studio** okna, všechny nezbytné proměnné prostředí jsou nastaveny za vás. Informace o tom, jak tento nástroj používat, najdete v článku [Developer Command Prompt pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tématu. 

Pokud používáte standardního okna příkazového řádku, je nutné upravit cestu k, abyste mohli vyvolat *csc.exe* z libovolného adresáře v počítači. Je také nutné spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku. Další informace o *vsvars32.bat*, včetně pokynů pro vyhledání a spusťte ho, naleznete v tématu [jak: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Pokud pracujete na počítači, který má pouze [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], můžete použít kompilátor jazyka C# na **příkazový řádek sady SDK**, které můžete otevřít z **Microsoft .NET Framework SDK** nabídky.

Pomocí nástroje MSBuild můžete také programově vytvářet programy jazyka C#. Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).

*Csc.exe* spustitelný soubor je obvykle umístěn ve Microsoft.NET\Framework\\*\<verze >* ve složce *Windows* adresář. Umístění, kde se může lišit v závislosti na přesnou konfiguraci určitého počítače. Pokud více než jednu verzi rozhraní .NET Framework je nainstalována v počítači, zjistíte více verzí tohoto souboru. Další informace o těchto zařízení najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Při vytváření projektu pomocí rozhraní IDE sady Visual Studio můžete zobrazit **csc** příkazu a jeho kompilátoru přidružené možností v **výstup** okna. Chcete-li zobrazit tyto informace, postupujte podle pokynů v [jak: Zobrazení, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) změnit úroveň podrobností dat protokolu do **normální** nebo **podrobné**. Po opětovném sestavení projektu, hledání **výstup** okně **csc** najít vyvolání kompilátor jazyka C#.

 **V tomto tématu**

- [Pravidla pro syntaxi příkazového řádku](#rules-for-command-line-syntax-for-the-c-compiler)

- [Ukázkové příkazové řádky](#sample-command-lines-for-the-c-compiler)

- [Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#

Kompilátor jazyka C# používá při interpretaci argumentů příkazového řádku operačního systému následující pravidla:

- Argumenty jsou odděleny prázdným znakem, který je mezera nebo tabulátor.

- Znak stříšky (^) nebyl rozpoznán jako řídicí znak ani oddělovač. Znak, který zařizuje služba analyzátor příkazového řádku v operačním systému předtím, než je předána `argv` pole v programu.

- Řetězec uzavřen do dvojitých uvozovek ("string") je interpretován jako jeden argument, bez ohledu na prázdný znak, který je součástí. Řetězec v uvozovkách, může být vložen do argumentu.

- Znak dvojitých uvozovek předcházený zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").

- Zpětná lomítka jsou interpretovány literálně, pokud jsou bezprostředně předcházet dvojité uvozovky.

- Pokud sudý počet zpětných lomítek následován znakem dvojitých uvozovek, je jedno zpětné lomítko ukládat `argv` pole pro každý pár zpětných lomítek a dvojitých uvozovek, je interpretován jako oddělovač řetězců.

- Pokud lichý počet zpětných lomítek následován znakem dvojitých uvozovek, je jedno zpětné lomítko ukládat `argv` pole pro každý pár zpětných lomítek a dvojitá uvozovka není "uvozeno uvozovacím znakem" ve zbývajících zpětné lomítko. To způsobí, že literálu uvozovky (") mají být přidány v `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Příkazové řádky ukázkové pro kompilátor jazyka C#

- Zkompiluje *File.cs* vytváření *File.exe*:

```console
csc File.cs 
```

- Zkompiluje *File.cs* vytváření *soubor.dll*:

```console
csc -target:library File.cs
```

- Zkompiluje *File.cs* a vytvoří *My.exe*:

```console
csc -out:My.exe File.cs
```

- Kompiluje všechny jazyka C# soubory v aktuálním adresáři s povolenou optimalizací a definuje DEBUG symbol. Výstup je *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Kompiluje všechny jazyka C# soubory v aktuálním adresáři ladicí verzi *File2.dll pro ladění*. Žádná upozornění ani logo se zobrazí:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Kompiluje všechny jazyka C# soubory v aktuálním adresáři *Something.xyz* (DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++
Neexistují žádné objektu (*.obj*) soubory vytvořené v důsledku volání kompilátor jazyka C#; výstupní soubory jsou vytvořeny přímo. V důsledku toho nemusí kompilátor jazyka C# propojovacího programu.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
- [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
- [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)
- [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
