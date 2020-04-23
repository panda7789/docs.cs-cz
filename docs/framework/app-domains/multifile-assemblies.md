---
title: Vícesouborová sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 2a70e45d50763cf99c55cf08600c3c816b4043b7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644207"
---
# <a name="multifile-assemblies"></a>Vícesouborová sestavení

Můžete vytvořit vícesouborové sestavení, která cílí na .NET Framework pomocí kompilátorů příkazového řádku nebo sady Visual Studio s Visual C++. Jeden soubor v sestavení musí obsahovat manifest sestavení. Sestavení, které spustí aplikaci, musí také obsahovat vstupní bod, například metodu `Main` nebo. `WinMain`

Předpokládejme například, že máte aplikaci, která obsahuje dva kódové moduly, *Client.cs* a *Stringer.cs*. *Stringer.cs* vytvoří `myStringer` obor názvů, na který se odkazuje v kódu v *Client.cs*. *Client.cs* obsahuje `Main` metodu, která je vstupním bodem aplikace. V tomto příkladu kompilujete dva kódové moduly a pak vytvoříte třetí soubor, který obsahuje manifest sestavení, který spouští aplikaci. Manifest sestavení odkazuje jak na moduly *klienta* , tak pro *Stringer* .

> [!NOTE]
> Vícesouborové sestavení může mít pouze jeden vstupní bod, a to i v případě, že sestavení má více kódových modulů.

Existuje několik důvodů, proč je vhodné vytvořit vícesouborové sestavení:

- Pro kombinování modulů napsaných v různých jazycích. Toto je nejběžnější důvod pro vytvoření vícesouborového sestavení.

- Chcete-li optimalizovat stahování aplikace v modulu, který je stažen pouze v případě potřeby, a to pomocí zřídka používaných typů.

    > [!NOTE]
    > Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značky v aplikaci Microsoft Internet Explorer, je důležité vytvořit vícesouborové sestavení. V tomto scénáři vytvoříte soubor oddělený od modulů kódu, který obsahuje pouze manifest sestavení. Internet Explorer nejprve stáhne manifest sestavení a poté vytvoří pracovní vlákna ke stažení jakýchkoli dalších modulů nebo sestavení potřebných pro. Při stahování souboru obsahujícího manifest sestavení přestane Internet Explorer reagovat na vstup uživatele. Menší soubor, který obsahuje manifest sestavení, méně času přestane Internet Explorer reagovat.

- Pro kombinování kódových modulů napsaných několika vývojáři. I když každý z vývojářů může kompilovat modul kódu do sestavení, může to vynutit, aby některé typy byly veřejně vystaveny, které nejsou vystaveny, pokud jsou všechny moduly vloženy do vícesouborového sestavení.

Po vytvoření sestavení můžete podepsat soubor, který obsahuje manifest sestavení, a sestavení, nebo můžete soubor a sestavení přidělit silný název a vložit je do globální mezipaměti sestavení (GAC).

## <a name="see-also"></a>Viz také

- [Postupy: sestavení vícesouborového sestavení](build-multifile-assembly.md)
- [Programování se sestaveními](../../standard/assembly/index.md)
