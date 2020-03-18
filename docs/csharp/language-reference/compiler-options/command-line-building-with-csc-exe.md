---
title: Sestavení příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789862"
---
# <a name="command-line-build-with-cscexe"></a>Sestavení příkazového řádku s csc.exe

Kompilátor jazyka C# můžete vyvolat zadáním názvu jeho spustitelného souboru (*csc.exe*) na příkazovém řádku.

Pokud použijete **okno Příkazový řádek pro vývojáře pro sadu Visual Studio,** budou nastaveny všechny proměnné prostředí. Informace o tom, jak získat přístup k tomuto nástroji, naleznete v [tématu Vývojářský příkaz ový řádek pro sadu Visual Studio.](../../../framework/tools/developer-command-prompt-for-vs.md)

Pokud používáte standardní okno příkazového řádku, je nutné upravit cestu před vyvoláním *souboru csc.exe* z libovolného podadresáře v počítači. Musíte také spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku. Další informace o *vsvars32.bat*, včetně pokynů k vyhledání a spuštění, naleznete v tématu [Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Pokud pracujete na počítači, který obsahuje pouze sadu Windows Software Development Kit (SDK), můžete použít kompilátor jazyka C# na **příkazovém řádku sady SDK**, který otevřete z nabídky sady **Microsoft .NET Framework SDK.**

MSBuild můžete také použít k vytvoření programů Jazyka C# programově. Další informace naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild).

Spustitelný soubor *csc.exe* je obvykle umístěn ve\\složce Microsoft.NET\Framework*\<Version>* v adresáři *systému Windows.* Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače. Pokud je v počítači nainstalována více než jedna verze rozhraní .NET Framework, najdete více verzí tohoto souboru. Další informace o těchto instalacích naleznete v [tématu How to: determine which version of the .NET Framework .](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)

> [!TIP]
> Při vytváření projektu pomocí ide sady Visual Studio můžete zobrazit příkaz **csc** a jeho přidružené možnosti kompilátoru v okně **Výstup.** Chcete-li tyto informace zobrazit, postupujte podle pokynů v [části Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) změňte úroveň podrobností dat protokolu na **normální** nebo **podrobnou**. Po sestavení projektu vyhledejte vyvolání kompilátoru jazyka C#, vyhledejte v okně **Výstup** **csc** vyvolání kompilátoru jazyka C#.

 **V tomto tématu**

- [Pravidla pro syntaxi příkazového řádku](#rules-for-command-line-syntax-for-the-c-compiler)

- [Ukázkové příkazové řádky](#sample-command-lines-for-the-c-compiler)

- [Rozdíly mezi kompilátorem jazyka C# a výstupem kompilátoru jazyka C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#

Kompilátor Jazyka C# používá následující pravidla, pokud interpretuje argumenty uvedené na příkazovém řádku operačního systému:

- Argumenty jsou odděleny prázdné místo, což je mezera nebo karta.

- Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač. Znak je zpracován analyzátorem příkazového řádku v operačním systému před `argv` jeho předáním poli v programu.

- Řetězec uzavřený v uvozovkách ("řetězec") je interpretován jako jeden argument, bez ohledu na prázdné místo, které je obsaženo uvnitř. Řetězec v uvozovkách může být vložen do argumentu.

- Dvojité uvozovky, před nimiž\\je zpětné lomítko ( ") interpretováno jako znak doslovné uvozovky ().

- Zpětná lomítka jsou interpretována doslovně, pokud bezprostředně nepředcházejí před uvozovkou.

- Pokud sudý počet zpětných lomítk následuje dvojité uvozovky, `argv` jedno zpětné lomítko je vložen do pole pro každý pár zpětných lomítka a dvojité uvozovky je interpretován jako řetězec oddělovač.

- Pokud lichý počet zpětných lomítk následuje dvojité uvozovky, `argv` jedno zpětné lomítko je vložen do pole pro každý pár zpětných lomítka a dvojité uvozovky je "uvozena" zbývající zpětné lomítko. To způsobí, že literál dvojité uvozovky (") které mají být přidány v `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Ukázkové příkazové řádky pro kompilátor jazyka C#

- Zkompiluje *File.cs* produkující *soubor File.exe*:

  ```console
  csc File.cs
  ```

- Zkompiluje *File.cs* produkci *souboru File.dll*:

  ```console
  csc -target:library File.cs
  ```

- Zkompiluje *File.cs* a vytvoří *my.exe*:

  ```console
  csc -out:My.exe File.cs
  ```

- Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři s povolenými optimalizacemi a definuje symbol LADĚNÍ. Výstupem je *Soubor2.exe*:

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři, který vytváří ladicí verzi *souboru File2.dll*. Nezobrazuje se žádné logo ani varování:

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři do *souboru Something.xyz* (dll):

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Rozdíly mezi kompilátorem jazyka C# a výstupem kompilátoru jazyka C++

Neexistují žádné soubory objektu (*obj*) vytvořené v důsledku vyvolání kompilátoru Jazyka C#; výstupní soubory jsou vytvářeny přímo. V důsledku toho kompilátor jazyka C# nepotřebuje propojovací ho.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Možnosti kompilátoru C# (abecední pořadí)](./listed-alphabetically.md)
- [Možnosti kompilátoru C# uvedené podle kategorie](./listed-by-category.md)
- [Argumenty Main() a příkazového řádku](../../programming-guide/main-and-command-args/index.md)
- [Argumenty příkazového řádku](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Jak zobrazit argumenty příkazového řádku](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](../../programming-guide/main-and-command-args/main-return-values.md)
