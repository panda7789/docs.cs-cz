---
title: Sestavení příkazového řádku pomocí CSc. exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 54306c79bc2856996925756ee4261fbe67692aea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606974"
---
# <a name="command-line-build-with-cscexe"></a>Sestavení příkazového řádku pomocí CSc. exe
C# Kompilátor můžete vyvolat zadáním názvu spustitelného souboru (*CSc. exe*) na příkazovém řádku.

Použijete-li okno **Developer Command Prompt pro sadu Visual Studio** , jsou pro vás nastaveny všechny potřebné proměnné prostředí. Informace o tom, jak získat přístup k tomuto nástroji, naleznete v tématu [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) . 

Používáte-li standardní okno příkazového řádku, je nutné před spuštěním souboru *CSc. exe* z libovolného podadresáře v počítači upravit cestu. Také je nutné spustit *vsvars32. bat* pro nastavení příslušných proměnných prostředí pro podporu sestavení příkazového řádku. Další informace o *vsvars32. bat*, včetně pokynů pro jeho vyhledání a spuštění, najdete v tématu [How to: Nastavení proměnných prostředí pro příkazový řádek](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)sady Visual Studio.

Pokud pracujete na počítači, který má pouze sadu Windows Software Development Kit (SDK), můžete použít C# kompilátor na **příkazovém řádku sady SDK**, který otevřete z možnosti nabídky **Microsoft .NET Framework SDK** .

Nástroj MSBuild můžete také použít k programovému sestavování C# programů. Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).

Spustitelný soubor *CSc. exe* je obvykle umístěný ve složce Microsoft. NET\Framework\\ *\<verze >* v adresáři *Windows* . Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače. Pokud je v počítači nainstalována více než jedna verze .NET Framework, najdete více verzí tohoto souboru. Další informace o těchto instalacích naleznete v tématu [How to: Určete, které verze .NET Framework jsou nainstalovány](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Při sestavování projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit příkaz **CSC** a jeho přidružené možnosti kompilátoru v okně **výstup** . Chcete-li zobrazit tyto informace, postupujte podle [pokynů v tématu Postupy: Umožňuje zobrazit, Uložit a nakonfigurovat soubory](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) protokolu sestavení pro změnu úrovně podrobností dat protokolu na **normální** nebo **podrobné**. Po opětovném sestavení projektu vyhledejte v okně **výstup** pro **CSC** , abyste našli vyvolání C# kompilátoru.

 **V tomto tématu**

- [Pravidla pro syntaxi příkazového řádku](#rules-for-command-line-syntax-for-the-c-compiler)

- [Ukázkové příkazové řádky](#sample-command-lines-for-the-c-compiler)

- [Rozdíly mezi C# kompilátorem C++ a výstupem kompilátoru](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Pravidla pro syntaxi příkazového řádku pro C# kompilátor

C# Kompilátor při interpretaci argumentů uvedených na příkazovém řádku operačního systému používá následující pravidla:

- Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.

- Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač. Znak je zpracován analyzátorem příkazového řádku v operačním systému předtím, než se předává do `argv` pole v programu.

- Řetězec uzavřený v dvojitých uvozovkách ("String") je interpretován jako jeden argument bez ohledu na prázdné znaky, které jsou obsaženy v. V argumentu může být vložen řetězec v uvozovkách.

- Dvojitá uvozovka začínající zpětným lomítkem (\\") je interpretována jako literální znak dvojité uvozovky (").

- Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.

- Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je vloženo do `argv` pole pro každý pár zpětných lomítek a Dvojitá uvozovka je interpretována jako oddělovač řetězců.

- Je-li lichý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěno v `argv` poli pro každý pár zpětných lomítek a dvojité uvozovky je "Escape" pomocí zbývajícího zpětného lomítka. To způsobí, že se literální dvojité uvozovky (") přidají do `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Ukázkové příkazové řádky pro C# kompilátor

- Zkompiluje *File.cs* vytvářející *soubor. exe*:

```console
csc File.cs 
```

- Zkompiluje *File.cs* produkující *soubor. dll*:

```console
csc -target:library File.cs
```

- Zkompiluje *File.cs* a vytvoří *My. exe*:

```console
csc -out:My.exe File.cs
```

- Zkompiluje všechny C# soubory v aktuálním adresáři s povolenými optimalizacemi a definuje symbol ladění. Výstup je *Soubor2. exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Zkompiluje všechny C# soubory v aktuálním adresáři, ve kterém je vyprodukována ladicí verze souboru *Soubor2. dll*. Nezobrazují se žádné logo a žádná upozornění:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Zkompiluje všechny C# soubory v aktuálním adresáři na *něco. xyz* (knihovna DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Rozdíly mezi C# kompilátorem C++ a výstupem kompilátoru
V důsledku vyvolání C# kompilátoru nejsou vytvořeny žádné soubory objektů ( *. obj*). výstupní soubory jsou vytvářeny přímo. V důsledku toho C# kompilátor nepotřebuje linker.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Možnosti kompilátoru jazyka C# (abecední pořadí)](./listed-alphabetically.md)
- [Možnosti kompilátoru jazyka C# uvedené podle kategorie](./listed-by-category.md)
- [Argumenty Main() a příkazového řádku](../../programming-guide/main-and-command-args/index.md)
- [Argumenty příkazového řádku](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Postupy: Zobrazit argumenty příkazového řádku](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](../../programming-guide/main-and-command-args/main-return-values.md)
