---
title: Direktivy kompilátoru
description: 'Přečtěte si o direktivách preprocesoru jazyka F #, direktivách podmíněné kompilace, direktivách řádků a direktivách kompilátoru.'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: aee307eb7bccc8d91b5162f3f43db3b806b761d0
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855371"
---
# <a name="compiler-directives"></a>Direktivy kompilátoru

Toto téma popisuje direktivy procesoru a direktivy kompilátoru.

## <a name="preprocessor-directives"></a>Preprocesor – direktivy

Direktiva preprocesoru je předponou # a na řádku se zobrazuje samostatně. Je interpretována preprocesorem, který se spouští před samotným kompilátorem.

V následující tabulce jsou uvedeny direktivy preprocesoru, které jsou k dispozici v F #.

|Směrnici|Popis|
|---------|-----------|
|`#if` * – symbol*|Podporuje podmíněnou kompilaci. Kód v sekci po `#if` je zahrnut, pokud je *symbol* definován. Symbol může být také negace s `!` .|
|`#else`|Podporuje podmíněnou kompilaci. Označí oddíl kódu, který se má zahrnout, pokud není definovaný symbol použitý s předchozí `#if` .|
|`#endif`|Podporuje podmíněnou kompilaci. Označuje konec podmíněné části kódu.|
|`#`Link *int*,<br/>`#`Link *int* – *řetězec*,<br/>`#`Link *int* *doslovné – řetězec*|Označuje původní řádek zdrojového kódu a název souboru pro ladění. Tato funkce je k dispozici pro nástroje, které generují zdrojový kód F #.|
|`#nowarn`*warningcode*|Zakáže upozornění kompilátoru nebo upozornění. Chcete-li zakázat upozornění, vyhledejte jeho číslo z výstupu kompilátoru a vložte ho do uvozovek. Vynechejte předponu FS. Chcete-li zakázat více čísel upozornění na jednom řádku, zahrňte každé číslo do uvozovek a jednotlivé řetězce oddělte mezerou. Příklad:

`#nowarn "9" "40"`

Účinek vypnutí upozornění se vztahuje na celý soubor, včetně částí souboru, které předcházejí této direktivě. |

## <a name="conditional-compilation-directives"></a>Direktivy podmíněné kompilace

Kód, který je dezaktivován jednou z těchto direktiv, se v editoru Visual Studio Code jeví šedě.

> [!NOTE]
> Chování direktiv podmíněné kompilace není stejné jako v jiných jazycích. Například nemůžete použít logické výrazy, které obsahují symboly a `true` `false` nemají žádný zvláštní význam. Symboly, které použijete v `if` direktivě, musí být definovány pomocí příkazového řádku nebo v nastavení projektu. neexistuje žádná `define` direktiva preprocesoru.

Následující kód ilustruje použití `#if` direktiv, a `#else` `#endif` . V tomto příkladu kód obsahuje dvě verze definice `function1` . Při `VERSION1` Definování pomocí [Možnosti kompilátoru-define](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)je kód mezi `#if` direktivou a `#else` direktivou aktivovaný. V opačném případě je kód mezi `#else` a `#endif` aktivovaný.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

`#define`V jazyce F # neexistuje žádná direktiva preprocesoru. Chcete-li definovat symboly používané direktivou, je nutné použít možnost kompilátoru nebo nastavení projektu `#if` .

Direktivy podmíněné kompilace můžou být vnořené. Odsazení není pro direktivy preprocesoru významné.

Můžete také negaci symbolu pomocí `!` . V tomto příkladu je hodnota řetězce něco _pouze při ladění_ :

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Line – direktivy

Při sestavování ohlásí kompilátor chyby v kódu F # odkazem na čísla řádků, u kterých dojde k chybě. Tato čísla řádků začínají 1 pro první řádek v souboru. Nicméně pokud generujete zdrojový kód F # z jiného nástroje, čísla řádků ve vygenerovaném kódu jsou obecně nezajímavá, protože chyby v kódu jazyka F # nejpravděpodobněji nastanou z jiného zdroje. `#line`Direktiva poskytuje autorům nástrojů, které generují zdrojový kód f # pro předávání informací o původních číslech řádků a zdrojových souborech do vygenerovaného kódu F #.

Když použijete `#line` direktivu, názvy souborů musí být uzavřeny v uvozovkách. Pokud se `@` před řetězcem objeví doslovné token (), je nutné, aby se znaky zpětného lomítka použily pomocí dvou zpětného lomítka místo jednoho, aby je bylo možné použít v cestě. Níže jsou uvedeny platné tokeny řádků. V těchto příkladech předpokládáme, že původní soubor má `Script1` za následek automaticky generovaný soubor kódu F # při spuštění prostřednictvím nástroje a že kód na umístění těchto direktiv je vygenerován z některých tokenů na řádku 25 v souboru `Script1` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tyto tokeny označují, že kód jazyka F # vygenerovaný v tomto umístění je odvozen z některých konstrukcí na nebo blízko řádku `25` v `Script1` .

## <a name="compiler-directives"></a>Direktivy kompilátoru

Direktivy kompilátoru připomínají direktivy preprocesoru, protože jsou opatřeny předponou #, ale namísto interpretace preprocesoru, jsou ponechány pro interpretaci a fungování.

V následující tabulce jsou uvedeny direktivy kompilátoru, které jsou k dispozici v F #.

|Směrnici|Popis|
|---------|-----------|
|`#light`["on" &#124; "off"]|Povolí nebo zakáže zjednodušenou syntaxi pro kompatibilitu s jinými verzemi ML. Ve výchozím nastavení je zjednodušená syntaxe povolena. Podrobná syntaxe je vždy povolena. Proto můžete použít jak zjednodušenou syntaxi, tak podrobnou syntaxi. Direktiva `#light` sama o sobě odpovídá `#light "on"` . Pokud zadáte `#light "off"` , je nutné použít podrobnou syntaxi pro všechny jazykové konstrukce. Syntaxe v dokumentaci F # je prezentována s předpokladem, že používáte zjednodušenou syntaxi. Další informace naleznete v tématu [verbose syntaxe](verbose-syntax.md).|

Direktivy překladače (fsi.exe) naleznete v tématu [interaktivní programování s F #](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Možnosti kompilátoru](compiler-options.md)
