---
title: 'Sestavení nelze vygenerovat: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968857"
---
# <a name="unable-to-emit-assembly-error-message"></a>Nelze vygenerovat sestavení: \<chybová zpráva >

Kompilátor Visual Basic volá linker sestavení (*Al. exe*, označovaný také jako ALink) pro generování sestavení s manifestem a linker hlásí chybu ve fázi emisí pro vytvoření sestavení.

**ID chyby:** BC30145

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Projděte si chybovou zprávu v uvozovkách a vyhledejte další vysvětlení a Rady v tématu [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) .

2. Zkuste podepsat sestavení ručně pomocí nástroje [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Pokud chyba přetrvává, shromážděte informace o okolnostech a upozorněte služby podpory společnosti Microsoft.

### <a name="to-sign-the-assembly-manually"></a>Postup ručního podepsání sestavení

1. K vytvoření souboru dvojice veřejného a privátního klíče použijte [Nástroj Sn. exe (Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).

   Tento soubor má příponu *. snk* .

2. Odstraňte odkaz modelu COM, který generuje chybu z vašeho projektu.

3. Otevřete [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   Ve Windows 10 zadejte **Developer Command Prompt** do vyhledávacího pole na hlavním panelu. Pak v seznamu výsledků vyberte **Developer Command Prompt pro VS 2017** .

4. Změňte adresář na adresář, do kterého chcete umístit obálku sestavení.

5. Zadejte následující příkaz:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Příklad skutečného příkazu, který byste mohli zadat, je:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Pokud cesta nebo soubor obsahuje mezery, použijte dvojité uvozovky.

6. V aplikaci Visual Studio přidejte odkaz na sestavení .NET do souboru, který jste právě vytvořili.

## <a name="see-also"></a>Viz také:

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](../../../standard/assembly/create-public-private-key-pair.md)
- [Kontaktujte nás](/visualstudio/ide/talk-to-us)
