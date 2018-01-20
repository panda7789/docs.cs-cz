---
title: "Sestavení příkazového řádku pomocí csc.exe"
ms.date: 04/19/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5fe7b735977b0cde0bed266815987b773be6bdbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="command-line-build-with-cscexe"></a>Sestavení příkazového řádku pomocí csc.exe
Kompilátor jazyka C# můžete vyvolat zadáním názvu jeho spustitelného souboru (*csc.exe*) na příkazovém řádku.

Pokud použijete **příkazový řádek vývojáře pro sadu Visual Studio** okně všechny nezbytné proměnné prostředí jsou nastavené pro vás. Informace o tom, jak získat přístup k tento nástroj najdete v tématu [příkazový řádek vývojáře pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tématu. 

Pokud chcete použít standardní okno příkazového řádku, je nutné upravit cestu k, než můžete vyvolat *csc.exe* z libovolného adresáře v počítači. Také musíte spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku. Další informace o *vsvars32.bat*, včetně pokyny, jak najít a spustit ji, najdete v článku [postupy: nastavení proměnných prostředí pro Visual Studio v příkazovém řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Pokud pracujete na počítač, který je k dispozici pouze [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], můžete kompilátor jazyka C# na **SDK – příkazový řádek**, které otevřete z **Microsoft .NET Framework SDK** možnost nabídky.

MSBuild můžete také použít k sestavení C# programy prostřednictvím kódu programu. Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).

*Csc.exe* spustitelný soubor je obvykle uložen ve Microsoft.NET\Framework\\*\<verze >* ve složce *Windows* adresář. Umístění, kde se můžou lišit v závislosti na přesnou konfiguraci určitého počítače. Pokud ve vašem počítači je nainstalovaná více než jedna verze rozhraní .NET Framework, zjistíte více verzí tohoto souboru. Další informace o těchto instalacích najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit **csc** příkaz a její přidružené kompilátoru možnosti v **výstup** okno. Chcete-li zobrazit tyto informace, postupujte podle pokynů v [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) chcete změnit úroveň podrobností dat protokolu **normální** nebo **podrobné**. Po opětovném sestavení projektu, vyhledávání **výstup** okna pro **csc** najít volání do kompilátoru jazyka C#.

 **V tomto tématu**

- [Pravidla pro syntaxe příkazového řádku](#-rules-for-command-line-syntax-for-the-c-compiler)

- [Příkazové řádky ukázkové](#sample-command-lines-for-the-c-compiler)

- [Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Pravidla pro syntaxe příkazového řádku pro kompilátor jazyka C#

Kompilátor jazyka C# používá následující pravidla při interpretaci argumentů zadána na příkazovém řádku operačního systému:

- Argumenty jsou odděleny prázdný znak, který je mezeru nebo na kartě.

- Znak pomocí kurzoru (^) není rozpoznán jako řídicí znak nebo oddělovač. Znak je zpracován analyzátorem příkazového řádku v operačním systému, než je předán do `argv` pole v programu.

- Řetězec v uvozovkách ("řetězec") interpretována jako jeden argument, bez ohledu na to prázdný znak, který je součástí. Řetězec v uvozovkách, lze jej vkládat v argumentu.

- Uvozovky uvedené zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").

- Zpětná lomítka se interpretují oznámena, pokud se okamžitě předcházet uvozovky.

- Pokud sudý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko uveden `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se interpretuje jako oddělovač řetězec.

- Pokud lichý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko uveden `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se "escape" ve zbývajících zpětné lomítko. To způsobí, že literálu uvozovky (") k přidání do `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Příkazové řádky ukázkové pro kompilátor jazyka C#

- Zkompiluje *File.cs* generovala *File.exe*:

```console
csc File.cs 
```

- Zkompiluje *File.cs* generovala *souboru File.dll*:

```console
csc -target:library File.cs
```

- Zkompiluje *File.cs* a vytvoří *My.exe*:

```console
csc -out:My.exe File.cs
```

- Kompiluje všechny C# soubory v aktuálním adresáři s povolenými optimalizacemi a definuje symboly pro ladění. Výstupem je *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Kompiluje všechny C# soubory v aktuálním adresáři ladicí verze *File2.dll pro ladění*. Zobrazí se žádná upozornění ani logo:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Kompiluje všechny C# soubory v aktuálním adresáři na *Something.xyz* (DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++
Neexistují žádné objektu (*.obj*) v důsledku volání do kompilátoru jazyka C# vytvoří soubory; výstupní soubory vytvářené přímo. V důsledku toho nemusí kompilátor jazyka C# linkeru.

## <a name="see-also"></a>Viz také
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Možnosti kompilátoru jazyka C# uvedené podle kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
