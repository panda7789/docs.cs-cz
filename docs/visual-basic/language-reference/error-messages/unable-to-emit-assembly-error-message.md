---
title: 'Sestavení nelze vygenerovat: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 012284aa42dfa29ad1a5e4ec4a4df5eaacbd4fb7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642281"
---
# <a name="unable-to-emit-assembly-error-message"></a>Sestavení nelze vygenerovat: \<chybová zpráva >

Kompilátor jazyka Visual Basic volá Assembly Linker (*Al.exe*, označovaný také jako Alink) ke generování manifestu a propojovací program sestavení nahlásí chybu ve fázi emisí vytváření sestavení.

**ID chyby:** BC30145

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte v uvozovkách chybovou zprávu a najdete v tématu [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) pro další vysvětlení a poradenství.

2. Zkuste se sestavení ručně, buď pomocí [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Pokud potíže potrvají, shromážděte informace o okolnostech a upozornit Microsoft Product Support Services.

### <a name="to-sign-the-assembly-manually"></a>K podepsání sestavení ručně

1. Použít [Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)) k vytvoření souboru pár veřejného a privátního klíče.

   Tento soubor má *.snk* rozšíření.

2. Odstraňte odkaz modelu COM, který generuje chybu z projektu.

3. Otevřít [Developer Command Prompt pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   Ve Windows 10, zadejte **příkazový řádek pro vývojáře** do vyhledávacího pole na hlavním panelu. Vyberte **Developer Command Prompt for VS 2017** ze seznamu výsledků.

4. Změňte adresář na adresář, kam chcete umístit vaše sestavení obálky.

5. Zadejte následující příkaz:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Je například skutečný příkaz, který můžete například zadat:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Pokud cestu nebo soubor obsahuje mezery, použijte uvozovky.

6. V sadě Visual Studio přidejte odkaz sestavení .NET do souboru, který jste právě vytvořili.

## <a name="see-also"></a>Viz také:

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Postupy: Vytvoření páru veřejného a privátního klíče](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
