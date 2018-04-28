---
title: Direktivy kompilátoru (F#)
description: 'Další informace o F # jazyka direktivy preprocesoru, podmíněná kompilace direktivy, direktivy řádku a direktivy kompilátoru.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 03fe3598f04025cf6dfaf2424b9fcb33ed4b3859
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="compiler-directives"></a>Direktivy kompilátoru

Toto téma popisuje direktivy procesoru a direktivy kompilátoru.


## <a name="preprocessor-directives"></a>Preprocesor – direktivy
Direktivy preprocesoru je předponou symbolem # a zobrazí se na řádek samostatně. Interpretovat preprocesor, který se spouští před kompilátoru sám sebe.

Následující tabulka uvádí direktivy preprocesoru, které jsou k dispozici v jazyce F #.


|– Direktiva|Popis|
|---------|-----------|
|`#if` *Symbol*|Podporuje Podmíněná kompilace. Kód v části po `#if` je zahrnuta, pokud *symbol* je definována.|
|`#else`|Podporuje Podmíněná kompilace. Označí části kódu, které chcete zahrnout, pokud je symbol použít s předchozí `#if` není definován.|
|`#endif`|Podporuje Podmíněná kompilace. Označuje konec podmínkového oddílu kódu.|
|`#`[řádku] *int*,<br/>`#`[řádku] *int* *řetězec*,<br/>`#`[řádku] *int* *typu verbatim řetězec*|Určuje původní zdrojový kód řádku a název souboru, pro ladění. Tato funkce je k dispozici pro nástroje, které generují F # zdrojového kódu.|
|`#nowarn` *warningcode*|Zakáže upozornění kompilátoru nebo upozornění. Zakázat upozornění, najděte jeho číslo z výstupu kompilátoru a její zahrnutí do uvozovek. Vynechte předponu "FS". Zakázat více čísel upozornění na stejném řádku, zahrnout všechna čísla v uvozovkách a oddělit každou řetězec mezerou. Příklad:

`#nowarn "9" "40"`


Výsledek vypnutí upozornění se vztahuje na celý soubor, včetně části souboru, které předcházet direktivu. |

## <a name="conditional-compilation-directives"></a>Direktivy Podmíněná kompilace
Kód, který je deaktivována pomocí jedné z těchto direktivy zobrazeno šedě v editoru Visual StudioCode.


>[!NOTE] 
Chování direktivy Podmíněná kompilace není stejný jako v jiných jazycích. Logické výrazy zahrnující symboly, například nelze použít a `true` a `false` mít žádný speciální význam. Symboly, které používáte ve `if` – direktiva musí být definován pomocí příkazového řádku nebo v nastavení projektu; neexistuje žádné `define` direktivy preprocesoru.


Následující kód ukazuje použití `#if`, `#else`, a `#endif` direktivy. V tomto příkladu kód obsahuje dvě verze definice `function1`. Při `VERSION1` se definuje pomocí [-define – možnost kompilátoru](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kód mezi `#if` – direktiva a `#else` – direktiva je aktivována. V opačném kód mezi `#else` a `#endif` se aktivuje.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Neexistuje žádné `#define` preprocesoru – direktiva v jazyce F #. Kompilátor – nastavení možnost nebo produktu project musíte použít k definování symboly používané `#if` – direktiva.

Podmíněná kompilace direktivy mohou být použity. Odsazení není důležité pro preprocesor – direktivy.


## <a name="line-directives"></a>Direktivy řádku
Při vytváření, kompilátor hlásí chyby v F # – kód pod položkou čísla řádků, kdy dojde k jednotlivým chybám došlo. Tato čísla řádku začínají znakem 1 pro první řádek v souboru. Ale pokud jsou generování F # zdrojového kódu z jiného nástroje, čísla řádků v generovaný kód nejsou obvykle zájmu, protože chyby v generovaný F # kód nejpravděpodobnější vyplývat z jiného zdroje. `#line` – Direktiva poskytuje způsob pro autory nástrojů, které generují F # zdrojového kódu předávat informace o řádku původní čísla a zdrojových souborech pro generovaný kód F #.

Při použití `#line` direktivy, názvy souborů musí být uzavřena v uvozovkách. Pokud je token typu verbatim (`@`) se zobrazí před řetězec, musí řídicí znaky zpětné lomítko pomocí dva znaky zpětné lomítko místo jeden, aby bylo možné používat v cestě. Níže jsou uvedeny platný řádek tokeny. V těchto příkladech předpokládáme, že původní soubor `Script1` výsledky v automaticky generované souboru kódu F # při spuštění pomocí některého nástroje, a generovaný kód na umístění těchto direktivy z některé tokenů na řádku v souboru 25 `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tato klíčová slova ukazují, že F # kód, který vygenerovala v tomto umístění je odvozený od některých konstrukce nebo blízko řádku `25` v `Script1`.


## <a name="compiler-directives"></a>Direktivy kompilátoru
Direktivy kompilátoru vypadat podobně jako preprocesor – direktivy, protože mají předponu znak #, ale nebude interpretován podle preprocesor, jsou ponechána pro kompilátor jak interpretovat a fungují v.

Následující tabulka uvádí direktiva kompilátoru, která je k dispozici v F #.


|– Direktiva|Popis|
|---------|-----------|
|`#light` ["na"&#124;"vypnuto"]|Povolí nebo zakáže prostá syntaxe pro kompatibilitu s jinými verzemi ML. Prostá syntaxe je ve výchozím nastavení povolené. Podrobná syntaxe je vždy povolena. Proto můžete prostá syntaxe a podrobná syntaxe. Direktiva `#light` sám o sobě je ekvivalentní `#light "on"`. Pokud zadáte `#light "off"`, je třeba použít podrobná syntaxe pro všechny jazykové konstrukty. Syntaxe v dokumentaci pro F # se zobrazí za předpokladu, že používáte prostá syntaxe. Další informace najdete v tématu [podrobná syntaxe](verbose-syntax.md).|
Direktivy překladač (fsi.exe), najdete v části [interaktivní programování s F #](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Možnosti kompilátoru](compiler-options.md)

