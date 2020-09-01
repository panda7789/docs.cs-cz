---
description: Sestavení příkazového řádku s csc.exe
title: Sestavení příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125927"
---
# <a name="command-line-build-with-cscexe"></a>Sestavení příkazového řádku s csc.exe

Kompilátor jazyka C# lze vyvolat zadáním názvu spustitelného souboru (*csc.exe*) na příkazovém řádku.

Použijete-li okno **Developer Command Prompt pro sadu Visual Studio** , jsou pro vás nastaveny všechny potřebné proměnné prostředí. Informace o tom, jak získat přístup k tomuto nástroji, naleznete v tématu [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) .

Pokud používáte standardní okno příkazového řádku, musíte upravit cestu, abyste mohli *csc.exe* vyvolat z libovolného podadresáře v počítači. Je také nutné spustit *VsDevCmd.bat* pro nastavení příslušných proměnných prostředí pro podporu sestavení příkazového řádku. Další informace o *VsDevCmd.bat*, včetně pokynů pro vyhledání a spuštění, naleznete v tématu [jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Pokud pracujete na počítači, který má pouze sadu Windows Software Development Kit (SDK), můžete použít kompilátor jazyka C# na příkazovém **řádku sady SDK**, který otevřete z možnosti nabídky **Microsoft .NET Framework SDK** .

Nástroj MSBuild můžete také použít k programovému sestavení programů v jazyce C#. Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).

Spustitelný soubor *csc.exe* obvykle je umístěný ve složce Microsoft. NET\Framework \\ *\<Version>* v adresáři *Windows* . Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače. Pokud je v počítači nainstalována více než jedna verze .NET Framework, najdete více verzí tohoto souboru. Další informace o těchto instalacích naleznete v tématu [How to: Určete, které verze .NET Framework jsou nainstalovány](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
> Při sestavování projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit příkaz **CSC** a jeho přidružené možnosti kompilátoru v okně **výstup** . Chcete-li zobrazit tyto informace, postupujte podle pokynů v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) pro změnu úrovně podrobností dat protokolu na **normální** nebo **podrobné**. Po opětovném sestavení projektu vyhledejte v okně **výstup** pro **CSC** , aby bylo nalezeno vyvolání kompilátoru jazyka C#.

 **V tomto tématu**

- [Pravidla pro syntaxi příkazového řádku](#rules-for-command-line-syntax-for-the-c-compiler)

- [Ukázkové příkazové řádky](#sample-command-lines-for-the-c-compiler)

- [Rozdíly mezi kompilátorem C# a výstupem kompilátoru C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#

Kompilátor jazyka C# při interpretaci argumentů uvedených na příkazovém řádku operačního systému používá následující pravidla:

- Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.

- Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač. Znak je zpracován analyzátorem příkazového řádku v operačním systému předtím, než se předává do `argv` pole v programu.

- Řetězec uzavřený v dvojitých uvozovkách ("String") je interpretován jako jeden argument bez ohledu na prázdné znaky, které jsou obsaženy v. V argumentu může být vložen řetězec v uvozovkách.

- Dvojitá uvozovka začínající zpětným lomítkem ( \\ ") je interpretována jako literální znak dvojité uvozovky (").

- Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.

- Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je vloženo do `argv` pole pro každý pár zpětných lomítek a Dvojitá uvozovka je interpretována jako oddělovač řetězců.

- Je-li lichý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěno v `argv` poli pro každý pár zpětných lomítek a dvojité uvozovky je "Escape" pomocí zbývajícího zpětného lomítka. To způsobí, že se literální dvojité uvozovky (") přidají do `argv` .

## <a name="sample-command-lines-for-the-c-compiler"></a>Ukázkové příkazové řádky pro kompilátor jazyka C#

- Zkompiluje *File.cs* produkující *File.exe*:

  ```console
  csc File.cs
  ```

- Zkompiluje *File.cs* produkující *File.dll*:

  ```console
  csc -target:library File.cs
  ```

- Zkompiluje *File.cs* a vytvoří *My.exe*:

  ```console
  csc -out:My.exe File.cs
  ```

- Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři s povolenými optimalizacemi a definuje symbol ladění. Výstup je *File2.exe*:

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři, ve kterém je vyprodukována ladicí verze *File2.dll*. Nezobrazují se žádné logo a žádná upozornění:

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři do souboru *. xyz* (knihovna DLL):

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Rozdíly mezi kompilátorem C# a výstupem kompilátoru C++

Neexistují žádné soubory objektů (*. obj*) vytvořené v důsledku vyvolání kompilátoru jazyka C#; výstupní soubory jsou vytvářeny přímo. V důsledku toho kompilátor C# nepotřebuje linker.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Možnosti kompilátoru C# (abecední pořadí)](./listed-alphabetically.md)
- [Možnosti kompilátoru C# uvedené podle kategorie](./listed-by-category.md)
- [Argumenty Main () a příkazového řádku](../../programming-guide/main-and-command-args/index.md)
- [Argumenty příkazového řádku](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Jak zobrazit argumenty příkazového řádku](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](../../programming-guide/main-and-command-args/main-return-values.md)
