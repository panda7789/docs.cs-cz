---
title: Podpisy (F#)
description: "Naučte se používat soubor podpisu F # uchovávání informací o veřejné podpisy sadu elementů F # program, jako jsou moduly, typy a obory názvů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 76c84a62-b2f6-44ec-8238-e687e2f7d18e
ms.openlocfilehash: d0f71c6472852268303a2d3af2e4b0a3c256704e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="signatures"></a>Podpisy

Soubor podpis obsahuje informace o veřejné podpisy sadu F # program prvky, jako jsou například moduly, obory názvů a typy. Slouží k určení usnadnění z těchto elementů programu.


## <a name="remarks"></a>Poznámky
Pro každý F # soubor kód, abyste měli *soubor podpisu*, což je soubor, který má stejný název jako soubor kódu, ale .fsi rozšíření místo .fs. Podpis souborů lze také přidat do příkazového řádku, pokud jsou přímo pomocí příkazového řádku kompilace. K rozlišení mezi soubory kódu a podpis soubory, soubory kódu se někdy označují jako *implementace soubory*. V projektu by měl předcházet soubor podpisu souboru přidružený kód.

Soubor podpisu popisuje obory názvů, moduly, typy a členy v příslušném souboru implementace. Informace v souboru se používá k určení, jaké části kódu odpovídající implementace souboru je přístupná z kódu mimo soubor implementace a které části jsou interní soubor implementace. Obory názvů, moduly a typy, které jsou obsaženy v souboru podpis musí být podmnožinou obory názvů, moduly a typy, které jsou obsaženy v souboru implementace. Na několik výjimek uvedené dále v tomto tématu jsou považovány za soukromé k souboru implementace těchto prvků jazyka, které nejsou uvedené v souboru podpis. Pokud žádný soubor podpisu je najde v projektu nebo příkazového řádku, použije se výchozí usnadnění.

Další informace o usnadnění výchozí najdete v tématu [řízení přístupu](access-control.md).

V souboru není opakujte implementace každé metody nebo funkce a definice typů. Místo toho použijte podpis pro každou metodu a funkce, která funguje jako specifikaci dokončení funkcí, které je implementované fragment modul, nebo obor názvů. Syntaxe pro typ podpisu je stejný jako příkaz, který se používá v deklaracích abstraktní metodu v abstraktní třídy a rozhraní a také zobrazen IntelliSense a fsi.exe překladač F # při zobrazení správně kompilované vstup.

Pokud není k dispozici dostatek informací v podpis typu indikující, zda je zapečetěná a typ, nebo zda je typ rozhraní, musíte přidat atribut určující povaha typ kompilátoru. Atributy, které používáte pro tento účel jsou popsané v následující tabulce.



|Atribut|Popis|
|---------|-----------|
|`[<Sealed>]`|Pro typ, který nemá žádné členy abstraktní, nebo by neměla být rozšířena.|
|`[<Interface>]`|Pro typ, který je rozhraní.|
Kompilátor vytváří chybu, pokud nejsou konzistentní mezi podpisu a deklarace v souboru implementace atributy.

Použití klíčového slova `val` k vytvoření podpisu pro hodnotu nebo hodnotu, funkce. Klíčové slovo `type` představuje typ podpisu.

Soubor podpisu můžete vygenerovat pomocí `--sig` – možnost kompilátoru. Obecně platí můžete Nezapisovat .fsi soubory ručně. Místo toho generovat .fsi soubory pomocí kompilátor, přidejte do projektu, pokud máte jeden a upravit jejich odebráním metody a funkce, které nechcete, aby byl přístupný.

Existuje několik pravidel pro podpisy typu:


- Zkratky typů v souboru implementace nesmí odpovídat typu bez zkratkou v souboru.


- Záznamy a rozlišovaná sjednocení musí vystavit všech nebo žádných z jejich pole a konstruktory a pořadí, v podpis musí odpovídat pořadí v souboru implementace. Třídy může odhalit některé, všech nebo žádných z jejich pole a metody v podpis.


- Třídy a struktury, které mají konstruktory musí vystavit deklarace jejich základní třídy ( `inherits` deklarace). Navíc třídy a struktury, které mají konstruktory musí vystavit všechny jejich abstraktní metody a deklarace rozhraní.


- Typy rozhraní musí odhalit jejich metody a rozhraní.


Pravidla pro podpisy hodnoty jsou následující:


- Modifikátory pro usnadnění (`public`, `internal`a tak dále) a `inline` a `mutable` modifikátory v podpisu musí odpovídat názvům implementace.


- Počet parametrů obecného typu (buď implicitně odvodit nebo explicitně deklarovat) musí odpovídat, a typy a typ omezení parametry obecného typu se musí shodovat.


- Pokud `Literal` atribut se používá, musí být uvedena v podpisu a implementaci a stejnou hodnotu literálu musí použít pro obě.


- Vzor parametry (také označované jako *Arita*) podpisů a implementace musí být konzistentní.


Následující příklad kódu ukazuje příklad podpis souboru, který má obor názvů, modulu, hodnota funkce a typ podpisy společně s příslušné atributy. Také ukazuje odpovídající soubor implementace.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Následující kód ukazuje implementaci soubor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)

[Řízení přístupu](access-control.md)

[Možnosti kompilátoru](compiler-options.md)
