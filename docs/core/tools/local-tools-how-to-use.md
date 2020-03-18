---
title: 'Kurz: Instalace a použití místních nástrojů .NET Core'
description: Přečtěte si, jak nainstalovat a používat nástroj .NET jako místní nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156696"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

Tento kurz vás naučí, jak nainstalovat a používat místní nástroj. Nástroj, který vytvoříte v [prvním kurzu této řady](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Požadavky

* Dokončete [první kurz této série](global-tools-how-to-create.md).
* Nainstalujte runtime .NET Core 2.1.

  Pro účely tohoto kurzu nainstalujete a použijete nástroj, který se zaměřuje na rozhraní .NET Core 2.1, takže musíte mít tento runtime nainstalován v počítači. Chcete-li nainstalovat runtime 2.1, přejděte na [stránku pro stažení rozhraní .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) a vyhledejte odkaz na instalaci runtime ve sloupci **Spustit aplikace – runtime.**

## <a name="create-a-manifest-file"></a>Vytvoření souboru manifestu

Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), musí být přidán do souboru manifestu.

Ze složky *microsoft.botsay* přejděte o jednu úroveň nahoru do složky *úložiště:*

```console
cd ..
```

Vytvořte soubor manifestu spuštěním nového příkazu [dotnet:](dotnet-new.md)

```dotnetcli
dotnet new tool-manifest
```

Výstup označuje úspěšné vytvoření souboru.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Soubor *.config/dotnet-tools.json* v něm zatím nemá žádné nástroje:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Nástroje uvedené v souboru manifestu jsou k dispozici pro aktuální adresář a podadresáře. Aktuální adresář je ten, který obsahuje adresář *.config* se souborem manifestu.

Při použití příkazu příkazu příkazu příkazu příkazu, který odkazuje na místní nástroj, sada SDK vyhledá soubor manifestu v aktuálním adresáři a nadřazených adresářích. Pokud najde soubor manifestu, ale soubor neobsahuje odkazovaný nástroj, pokračuje v hledání prostřednictvím nadřazených adresářů. Hledání končí, když vyhledá odkazovaný nástroj nebo najde `isRoot` soubor `true`manifestu s nastavenou na .

## <a name="install-botsay-as-a-local-tool"></a>Nainstalujte botsay jako místní nástroj

Nainstalujte nástroj z balíčku, který jste vytvořili v prvním kurzu:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Tento příkaz přidá nástroj do souboru manifestu, který jste vytvořili v předchozím kroku. Výstup příkazu ukazuje, ve kterém souboru manifestu se nově nainstalovaný nástroj nachází:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Soubor *.config/dotnet-tools.json* má nyní jeden nástroj:

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

Vyvolat nástroj spuštěním `dotnet tool run` příkazu ze složky *úložiště:*

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Obnovení místního nástroje nainstalovaného jinými uživateli

Obvykle nainstalujete místní nástroj do kořenového adresáře úložiště. Po vrácení souboru manifestu se změnami do úložiště mohou ostatní vývojáři získat nejnovější soubor manifestu. Chcete-li nainstalovat všechny nástroje uvedené v souboru `dotnet tool restore` manifestu, mohou spustit jeden příkaz.

1. Otevřete soubor *.config/dotnet-tools.json* a nahraďte obsah následujícím nástrojem JSON:

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

1. Nahraďte `<name>` název, který jste použili k vytvoření projektu.

1. Uložte provedené změny.

   Provedení této změny je stejné jako získání nejnovější verze z úložiště `dotnetsay` poté, co někdo jiný nainstaloval balíček pro adresář projektu.

1. Spusťte příkaz `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   Příkaz vytváří výstup jako v následujícím příkladu:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Ověřte, zda jsou nástroje k dispozici:

   ```dotnetcli
   dotnet tool list
   ```

   Výstup je seznam balíčků a příkazů, podobně jako v následujícím příkladu:

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

Nainstalovaná verze místního nástroje `dotnetsay` je 2.1.3.  Nejnovější verze je 2.1.4. Pomocí příkazu [aktualizace nástroje dotnet](dotnet-tool-update.md) aktualizujte nástroj na nejnovější verzi.

```dotnetcli
dotnet tool update dotnetsay
```

Na výstupu je uvedeno nové číslo verze:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Příkaz update vyhledá první soubor manifestu, který obsahuje ID balíčku, a aktualizuje jej. Pokud není žádné takové ID balíčku v libovolném souboru manifestu, který je v oboru hledání, sada SDK přidá novou položku do nejbližšího souboru manifestu. Obor hledání je až přes nadřazené adresáře, dokud není nalezen soubor manifestu s. `isRoot = true`

## <a name="remove-local-tools"></a>Odebrání místních nástrojů

Odeberte nainstalované nástroje spuštěním příkazu [odinstalace nástroje dotnet:](dotnet-tool-uninstall.md)

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Řešení potíží

Pokud se při sledování kurzu zobrazí chybová zpráva, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Viz také

Další informace naleznete v tématu [.NET Core tools](global-tools.md)
