---
title: Direktivy kompilátoru (F#)
description: Další informace o F# jazyka direktivy preprocesoru, direktivy podmíněné kompilace, direktivy line a direktivy kompilátoru.
ms.date: 05/16/2016
ms.openlocfilehash: 5ac375ac5acd0609a6556f9e0481d169df827c98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50181365"
---
# <a name="compiler-directives"></a>Direktivy kompilátoru

Toto téma popisuje procesor směrnic a direktivy kompilátoru.

## <a name="preprocessor-directives"></a>Preprocesor – direktivy

Direktivy preprocesoru je symbolů # předponu a zobrazí se v řádku samostatně. Je interpretován pomocí preprocesoru, který se spouští před kompilátor sám.

Následující tabulka uvádí direktivy preprocesoru, které jsou k dispozici v jazyce F#.

|– Direktiva|Popis|
|---------|-----------|
|`#if` *Symbol*|Podporuje podmíněné kompilace. Kód v části po `#if` je zahrnuta, pokud *symbol* je definována.|
|`#else`|Podporuje podmíněné kompilace. Označí části kódu, které chcete zahrnout, pokud symbol použili s předchozí `#if` není definován.|
|`#endif`|Podporuje podmíněné kompilace. Označuje konec podmíněné části kódu.|
|`#`[řádku] *int*,<br/>`#`[řádku] *int* *řetězec*,<br/>`#`[řádku] *int* *doslovný řetězec*|Určuje původní zdrojový kód řádku a název souboru, pro ladění. Tato funkce je k dispozici pro nástroje, které generují zdrojovém kódu F#.|
|`#nowarn` *warningcode*|Zakáže upozornění kompilátoru nebo upozornění. Zakázat upozornění, vyhledejte příslušného čísla z výstupu kompilátoru a uzavřete do uvozovek. Vynechte předpony "FS". Zakázat více čísel upozornění na stejném řádku, zahrnout každého čísla v uvozovkách a oddělte každý řetězec oddělte mezerou. Příklad:

`#nowarn "9" "40"`

Výsledek vypnutí upozornění se vztahuje na celý soubor, včetně části souboru, které předcházet direktiva. |

## <a name="conditional-compilation-directives"></a>Direktivy podmíněné kompilace

Kód, který je deaktivováno pomocí jedné z těchto směrnic zobrazeno šedě v editoru kódu sady Visual Studio.

>[!NOTE]
Chování direktivy podmíněné kompilace není stejný jako v jiných jazycích. Například nelze použít logické výrazy zahrnující symbolů, a `true` a `false` nemají zvláštní význam. Symboly, které můžete použít `if` – direktiva musí být definován pomocí příkazového řádku nebo v nastavení projektu, neexistuje žádný `define` direktiva preprocesoru.

Následující kód ukazuje použití `#if`, `#else`, a `#endif` direktivy. V tomto příkladu kód obsahuje dvě verze definice `function1`. Při `VERSION1` se definuje pomocí [-define – možnost kompilátoru](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kód mezi `#if` – direktiva a `#else` – direktiva je aktivován. V opačném případě kód mezi `#else` a `#endif` aktivován.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Neexistuje žádná `#define` preprocesoru – direktiva v jazyce F#. Nastavení kompilátoru možnost nebo projektu musíte použít k definování symboly používají `#if` směrnice.

Mohou být vnořené direktivy podmíněné kompilace. Odsazení není významné pro preprocesor – direktivy.

## <a name="line-directives"></a>Direktivy Line

Při sestavování, kompilátor hlásí chyby v kódu F# pomocí odkazu na čísla řádků, na kterém dojde k každé chybě. Tato čísla řádku začínají znakem 1 pro první řádek v souboru. Ale pokud zdrojový kód F# se generuje z jiného nástroje, čísla řádků ve vygenerovaném kódu nejsou obecně zájmu, protože chyby ve vygenerovaném F# kódu pravděpodobně vznikají z jiného zdroje. `#line` – Direktiva poskytuje způsob pro autory nástrojů, které generování zdrojového kódu jazyka F# k předávání informací o původní řádek čísla a zdrojové soubory do generovaného kódu F#.

Při použití `#line` direktiv, názvy souborů musí být uzavřen v uvozovkách. Pokud verbatim token (`@`) se zobrazí před řetězec pomocí dvou znaků zpětného lomítka místo aby bylo možné používat v cestě musí řídicí znaky zpětného lomítka. Toto jsou tokeny platné řádku. V těchto příkladech se předpokládá, že původní soubor `Script1` výsledky v automaticky generovaného souboru kódu F# při spuštění pomocí některého nástroje, a vygenerovanou z některých tokenů na řádku 25 v souboru kódu na místě těchto směrnic `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tyto tokeny znamenat, že kód F# vygenerovaný na tomto místě je odvozen z některé konstrukce nebo blízko řádku `25` v `Script1`.

## <a name="compiler-directives"></a>Direktivy kompilátoru

Direktivy kompilátoru vypadat podobně jako direktivy preprocesoru, protože mají předponu znaménko #, ale nebude interpretován pomocí preprocesoru, jsou ponechána pro kompilátor interpretovat a zpracovat.

Následující tabulka uvádí direktivy kompilátoru, která je k dispozici v jazyce F#.

|– Direktiva|Popis|
|---------|-----------|
|`#light` ["na"&#124;"off"]|Povolí nebo zakáže jednoduché syntaxe, pro kompatibilitu s jinými verzemi ML. Prostá syntaxe je ve výchozím nastavení povolené. Podrobná syntaxe je vždy povolena. Proto můžete použít nenáročném syntaxi a podrobná syntaxe. Direktiva `#light` sám o sobě je ekvivalentní `#light "on"`. Pokud zadáte `#light "off"`, je nutné použít podrobné syntaxi pro všechny jazykové konstrukce. Syntaxe v dokumentaci pro F# se zobrazí za předpokladu, že používáte nenáročném syntaxi. Další informace najdete v tématu [podrobná syntaxe](verbose-syntax.md).|
Direktivy interpretu (fsi.exe), najdete v části [interaktivní programování s F#](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Možnosti kompilátoru](compiler-options.md)
