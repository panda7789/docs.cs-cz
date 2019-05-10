---
title: Vícesouborová sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e00ec239fbe5d5963edd3a7656961556792c6324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593546"
---
# <a name="multifile-assemblies"></a>Vícesouborová sestavení

Můžete vytvořit vícesouborové sestavení pomocí kompilátoru příkazového řádku nebo Visual Studio s jazykem Visual C++. Jeden soubor v sestavení musí obsahovat manifest sestavení. Vstupní bod, například pro metodu Main nebo WinMain musí obsahovat také sestavení, které spustí aplikaci.

Předpokládejme například, že máte aplikaci, která obsahuje dva moduly kódu, Client.cs a Stringer.cs. Vytvoří Stringer.cs `myStringer` obor názvů, který se odkazuje pomocí kódu v Client.cs. Obsahuje Client.cs `Main` metodu, která je vstupní bod aplikace. V tomto příkladu kompilaci dva moduly kódu a pak vytvořte třetí soubor, který obsahuje manifest sestavení, který spouští aplikaci. Manifest sestavení odkazuje na i `Client` a `Stringer` moduly.

> [!NOTE]
> Vícesouborová sestavení může mít pouze jeden vstupní bod, i v případě, že sestavení má více modulů kódu.

Existuje několik důvodů, proč že můžete chtít vytvořit vícesouborové sestavení:

- Kombinování modulů napsaných v různých jazycích. Toto je nejběžnějším důvodem pro vytvoření vícesouborového sestavení.

- K optimalizaci stahování aplikace tak, že vložíte zřídka používané typy modulu, který se stáhne jenom v případě potřeby.

    > [!NOTE]
    > Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značku Microsoft Internet Explorer, je důležité vytvořit vícesouborové sestavení. V tomto scénáři vytvoříte soubor odděleně od moduly kódu, které obsahuje manifest sestavení. Aplikace Internet Explorer nejprve stáhne manifest sestavení a pak vytvoří pracovních vláken pro stahování jakékoli další moduly nebo požadovaná sestavení. Při stažení souboru, který obsahuje manifest sestavení aplikace Internet Explorer bude reagovat na vstup uživatele. Čím menší soubor obsahující manifest sestavení, tím méně času aplikace Internet Explorer nebude reagovat.

- Kombinovat kód modulů napsaných několik vývojáři. I když každý vývojář může každý modul kódu zkompilovat do sestavení, tato vynutí některé typy veřejně zpřístupní, které nejsou vystaveny, pokud všechny moduly jsou vloženy do vícesouborové sestavení.

Po vytvoření sestavení lze podepsat soubor obsahující manifest sestavení (a tedy sestavení), nebo můžete poskytnout silného názvu souboru (a sestavení) a vložit ho do globální mezipaměti sestavení.

## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)