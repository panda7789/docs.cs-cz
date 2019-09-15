---
title: Vícesouborové sestavení
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4c288a54194e89eb90b6ac512cf45184376e952
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971866"
---
# <a name="multifile-assemblies"></a>Vícesouborové sestavení

Můžete vytvořit vícesouborové sestavení, která cílí na .NET Framework pomocí kompilátorů příkazového řádku nebo sady Visual Studio s C++Visual. Jeden soubor v sestavení musí obsahovat manifest sestavení. Sestavení, které spustí aplikaci, musí také obsahovat vstupní bod, například `Main` metodu nebo. `WinMain`

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

## <a name="see-also"></a>Viz také:

- [Postupy: Sestavení vícesouborového sestavení](build-multifile-assembly.md)
- [Program se sestaveními](../../standard/assembly/program.md)
