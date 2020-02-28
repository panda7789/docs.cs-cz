---
title: 'Kurz: instalace a používání místních nástrojů .NET Core'
description: Naučte se instalovat a používat nástroj .NET jako místní nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156696"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

V tomto kurzu se naučíte, jak nainstalovat a používat místní nástroj. Použijete nástroj, který vytvoříte v [prvním kurzu této série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Předpoklady

* Dokončete [první kurz této série](global-tools-how-to-create.md).
* Nainstalujte modul runtime .NET Core 2,1.

  V tomto kurzu nainstalujete a použijete nástroj, který cílí na .NET Core 2,1, takže musíte mít v počítači nainstalovaný tento modul runtime. Pokud chcete nainstalovat modul runtime 2,1, navštivte [stránku ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) a vyhledejte odkaz instalace modulu runtime ve sloupci **Spustit aplikace – modul runtime** .

## <a name="create-a-manifest-file"></a>Vytvořit soubor manifestu

Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), je nutné jej přidat do souboru manifestu.

Ve složce *Microsoft. botsay* přejděte o jednu úroveň výš do složky *úložiště* :

```console
cd ..
```

Vytvořte soubor manifestu spuštěním příkazu [dotnet New](dotnet-new.md) :

```dotnetcli
dotnet new tool-manifest
```

Výstup indikuje úspěšné vytvoření souboru.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Soubor *. config/dotnet-Tools. JSON* zatím neobsahuje žádné nástroje:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Nástroje uvedené v souboru manifestu jsou k dispozici pro aktuální adresář a podadresáře. Aktuální adresář je ten, který obsahuje adresář *. config* se souborem manifestu.

Když použijete příkaz CLI, který odkazuje na místní nástroj, sada SDK vyhledá soubor manifestu v aktuálním adresáři a v nadřazených adresářích. Pokud najde soubor manifestu, ale soubor neobsahuje odkazovaný nástroj, pokračuje v hledání prostřednictvím nadřazených adresářů. Hledání skončí, když nalezne odkazovaný nástroj, nebo najde soubor manifestu s `isRoot` nastavenou na `true`.

## <a name="install-botsay-as-a-local-tool"></a>Nainstalovat botsay jako místní nástroj

Nainstalujte nástroj z balíčku, který jste vytvořili v prvním kurzu:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Tento příkaz přidá nástroj do souboru manifestu, který jste vytvořili v předchozím kroku. Výstup příkazu zobrazuje, ve kterém souboru manifestu je nově nainstalovaný nástroj:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Soubor *. config/dotnet-Tools. JSON* teď obsahuje jeden nástroj:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>Použití nástroje

Vyvolejte nástroj spuštěním příkazu `dotnet tool run` ze složky *úložiště* :

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Obnovení místního nástroje nainstalovaného jinými uživateli

V kořenovém adresáři úložiště obvykle nainstalujete místní nástroj. Po vrácení souboru manifestu do úložiště mohou jiní vývojáři získat nejnovější soubor manifestu. Chcete-li nainstalovat všechny nástroje, které jsou uvedeny v souboru manifestu, mohou spustit jeden `dotnet tool restore` příkaz.

1. Otevřete soubor *. config/dotnet-Tools. JSON* a nahraďte obsah následujícím kódem JSON:

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. Nahraďte `<name>` názvem, který jste použili k vytvoření projektu.

1. Uložte provedené změny.

   Tato změna je stejná jako získání nejnovější verze z úložiště poté, co někdo jiný nainstaloval balíček `dotnetsay` pro adresář projektu.

1. Spusťte příkaz `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   Příkaz vytvoří výstup podobný následujícímu příkladu:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Ověřte, že jsou dostupné tyto nástroje:

   ```dotnetcli
   dotnet tool list
   ```

   Výstupem je seznam balíčků a příkazů, podobně jako v následujícím příkladu:

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Otestujte nástroje:

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Aktualizace místního nástroje

Nainstalovaná verze místního nástroje `dotnetsay` je 2.1.3.  Nejnovější verze je 2.1.4. K aktualizaci nástroje na nejnovější verzi použijte příkaz [dotnet Tool Update](dotnet-tool-update.md) .

```dotnetcli
dotnet tool update dotnetsay
```

Výstup označuje nové číslo verze:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Příkaz Update vyhledá první soubor manifestu, který obsahuje ID balíčku, a aktualizuje ho. Pokud žádné takové ID balíčku není v žádném souboru manifestu, který je v oboru hledání, sada SDK přidá novou položku do nejbližšího souboru manifestu. Rozsah hledání je až do nadřazených adresářů, dokud se nenajde soubor manifestu s `isRoot = true`.

## <a name="remove-local-tools"></a>Odebrat místní nástroje

Nainstalované nástroje odeberte spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Řešení potíží

Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Viz také

Další informace najdete v tématu [nástroje .NET Core](global-tools.md) .
