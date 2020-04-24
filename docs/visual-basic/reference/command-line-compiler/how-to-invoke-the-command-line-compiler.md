---
title: 'Postupy: Volání kompilátoru příkazového řádku'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344263"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Postupy: Volání kompilátoru příkazového řádku (Visual Basic)

Kompilátor příkazového řádku můžete vyvolat zadáním názvu spustitelného souboru do příkazového řádku, který se označuje také jako příkazový řádek MS-DOS. Pokud kompilujete z výchozího příkazového řádku systému Windows, je nutné zadat plně kvalifikovanou cestu ke spustitelnému souboru. Chcete-li přepsat toto výchozí chování, můžete buď použít Developer Command Prompt pro Visual Studio, nebo upravit proměnnou prostředí PATH. Obě umožňují kompilovat z libovolného adresáře pouhým zadáním názvu kompilátoru.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Volání kompilátoru pomocí Developer Command Prompt pro Visual Studio

1. Otevřete složku Visual Studio Tools program ve skupině Microsoft Visual Studio programu.

2. Pokud je nainstalována aplikace Visual Studio, můžete použít Developer Command Prompt pro Visual Studio k přístupu k kompilátoru z libovolného adresáře na vašem počítači.

3. Vyvolejte Developer Command Prompt pro Visual Studio.

4. Do příkazového řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.

    Pokud jste například uložili zdrojový kód do adresáře s názvem `SourceFiles`, otevřete příkazový řádek a zadejte `cd SourceFiles` příkaz pro změnu do tohoto adresáře. Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, můžete ho zkompilovat zadáním. `vbc.exe Source.vb`

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Nastavení proměnné prostředí PATH na kompilátor příkazového řádku systému Windows

1. K vyhledání Vbc. exe na místním disku použijte funkci Windows Search.

    Přesný název adresáře, ve kterém je kompilátor umístěný, závisí na umístění adresáře systému Windows a ve verzi nainstalovaného ".NET Framework". Pokud máte nainstalovanou více než jednu verzi .NET Framework, musíte určit, která verze se má použít (obvykle nejnovější verze).

2. V nabídce **Start** klikněte pravým tlačítkem myši na položku **Tento počítač**a potom v místní nabídce klikněte na příkaz **vlastnosti** .

3. Klikněte na kartu **Upřesnit** a pak klikněte na **proměnné prostředí**.

4. V podokně **systémové** proměnné vyberte v seznamu možnost **cesta** a klikněte na **Upravit**.

5. V dialogovém okně **upravit systémovou** proměnnou přesuňte kurzor na konec řetězce v poli **hodnota proměnné** a zadejte středník (;) Následuje úplný název adresáře, který byl nalezen v kroku 1.

6. Kliknutím na tlačítko **OK** potvrďte provedené úpravy a zavřete dialogová okna.

     Po změně proměnné prostředí PATH můžete spustit kompilátor Visual Basic v příkazovém řádku systému Windows z libovolného adresáře v počítači.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Vyvolání kompilátoru pomocí příkazového řádku systému Windows

1. V nabídce **Start** klikněte na složku **příslušenství** a pak otevřete **příkazový řádek systému Windows**.

2. Do příkazového řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.

     Pokud jste například uložili zdrojový kód do adresáře s názvem `SourceFiles`, otevřete příkazový řádek a zadejte `cd SourceFiles` příkaz pro změnu do tohoto adresáře. Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, můžete ho zkompilovat zadáním. `vbc.exe Source.vb`

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
