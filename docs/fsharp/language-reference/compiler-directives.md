---
title: Direktivy kompilátoru
description: Přečtěte F# si o direktivách preprocesoru jazyka, direktivách podmíněné kompilace, direktivách řádků a direktivách kompilátoru.
ms.date: 12/10/2018
ms.openlocfilehash: 16db2efb2fee2c2c5e94aa98eb0a13183a4e0e0b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630412"
---
# <a name="compiler-directives"></a>Direktivy kompilátoru

Toto téma popisuje direktivy procesoru a direktivy kompilátoru.

## <a name="preprocessor-directives"></a>Preprocesor – direktivy

Direktiva preprocesoru je předponou # a na řádku se zobrazuje samostatně. Je interpretována preprocesorem, který se spouští před samotným kompilátorem.

V následující tabulce jsou uvedeny direktivy preprocesoru, které jsou k F#dispozici v.

|– Direktiva|Popis|
|---------|-----------|
|`#if` *symbol*|Podporuje podmíněnou kompilaci. Kód v sekci po `#if` je zahrnut, pokud je *symbol* definován. Symbol může být také negace s `!`.|
|`#else`|Podporuje podmíněnou kompilaci. Označí oddíl kódu, který se má zahrnout, pokud není definovaný symbol použitý `#if` s předchozí.|
|`#endif`|Podporuje podmíněnou kompilaci. Označuje konec podmíněné části kódu.|
|`#`Link *int*,<br/>`#`Link *int* *řetězec*,<br/>`#`Link *int* *doslovné znění – řetězec*|Označuje původní řádek zdrojového kódu a název souboru pro ladění. Tato funkce je k dispozici pro nástroje F# , které generují zdrojový kód.|
|`#nowarn`*warningcode*|Zakáže upozornění kompilátoru nebo upozornění. Chcete-li zakázat upozornění, vyhledejte jeho číslo z výstupu kompilátoru a vložte ho do uvozovek. Vynechejte předponu FS. Chcete-li zakázat více čísel upozornění na jednom řádku, zahrňte každé číslo do uvozovek a jednotlivé řetězce oddělte mezerou. Příklad:

`#nowarn "9" "40"`

Účinek vypnutí upozornění se vztahuje na celý soubor, včetně částí souboru, které předcházejí této direktivě. |

## <a name="conditional-compilation-directives"></a>Direktivy podmíněné kompilace

Kód, který je dezaktivován jednou z těchto direktiv, se v editoru Visual Studio Code jeví šedě.

> [!NOTE]
> Chování direktiv podmíněné kompilace není stejné jako v jiných jazycích. Například nemůžete použít logické výrazy, `true` `false` které obsahují symboly a nemají žádný zvláštní význam. Symboly, které použijete v `if` direktivě, musí být definovány pomocí příkazového řádku nebo v nastavení projektu. neexistuje žádná `define` direktiva preprocesoru.

Následující kód ilustruje použití `#if` `#endif` direktiv, `#else`a. V tomto příkladu kód obsahuje dvě verze definice `function1`. Při `VERSION1` definování pomocí [Možnosti kompilátoru-define](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)je kód mezi `#if` direktivou a `#else` direktivou aktivovaný. V opačném případě je `#else` kód `#endif` mezi a aktivovaný.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

V F#neexistuje žádná `#define` direktiva preprocesoru. Chcete-li definovat symboly používané `#if` direktivou, je nutné použít možnost kompilátoru nebo nastavení projektu.

Direktivy podmíněné kompilace můžou být vnořené. Odsazení není pro direktivy preprocesoru významné.

Můžete také negaci symbolu pomocí `!`. V tomto příkladu je hodnota řetězce něco _pouze při ladění_ :

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Line – direktivy

Při sestavování ohlásí kompilátor chyby v F# kódu odkazem na čísla řádků, u kterých dojde k chybě. Tato čísla řádků začínají 1 pro první řádek v souboru. Nicméně pokud generujete F# zdrojový kód z jiného nástroje, čísla řádků ve vygenerovaném kódu jsou obecně nezajímavá, protože chyby v generovaném F# kódu budou pravděpodobně způsobeny jiným zdrojem. Tato `#line` direktiva poskytuje autorům nástrojů, které generují F# zdrojový kód k předávání informací o původních číslech řádků a zdrojových souborech do generovaného F# kódu.

Když použijete `#line` direktivu, názvy souborů musí být uzavřeny v uvozovkách. Pokud se před řetězcem`@`objeví doslovné token (), je nutné, aby se znaky zpětného lomítka použily pomocí dvou zpětného lomítka místo jednoho, aby je bylo možné použít v cestě. Níže jsou uvedeny platné tokeny řádků. V těchto příkladech předpokládáme, že původní `Script1` soubor má za následek automaticky F# generovaný soubor kódu, když je spuštěn prostřednictvím nástroje a že kód na umístění těchto direktiv je vygenerován z některých tokenů na řádku 25 v souboru `Script1`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tyto tokeny označují, F# že kód vygenerovaný v tomto umístění je odvozen z některých konstrukcí na nebo blízko `25` řádku `Script1`v.

## <a name="compiler-directives"></a>Direktivy kompilátoru

Direktivy kompilátoru připomínají direktivy preprocesoru, protože jsou opatřeny předponou #, ale namísto interpretace preprocesoru, jsou ponechány pro interpretaci a fungování.

V následující tabulce jsou uvedeny direktivy kompilátoru, které jsou F#k dispozici v.

|– Direktiva|Popis|
|---------|-----------|
|`#light`["on"&#124;"off"]|Povolí nebo zakáže zjednodušenou syntaxi pro kompatibilitu s jinými verzemi ML. Ve výchozím nastavení je zjednodušená syntaxe povolena. Podrobná syntaxe je vždy povolena. Proto můžete použít jak zjednodušenou syntaxi, tak podrobnou syntaxi. Direktiva `#light` sama o sobě `#light "on"`odpovídá. Pokud zadáte `#light "off"`, je nutné použít podrobnou syntaxi pro všechny jazykové konstrukce. Syntaxe v dokumentaci pro F# se zobrazí s předpokladem, že používáte zjednodušenou syntaxi. Další informace naleznete v tématu [verbose syntaxe](verbose-syntax.md).|

Direktivy překladače (fsi. exe) naleznete v tématu [interaktivní programování F#s ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Možnosti kompilátoru](compiler-options.md)
