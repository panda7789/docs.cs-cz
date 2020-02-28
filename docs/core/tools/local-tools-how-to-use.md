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
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="f348d-103">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f348d-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="f348d-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="f348d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="f348d-105">V tomto kurzu se naučíte, jak nainstalovat a používat místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="f348d-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="f348d-106">Použijete nástroj, který vytvoříte v [prvním kurzu této série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="f348d-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f348d-107">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="f348d-107">Prerequisites</span></span>

* <span data-ttu-id="f348d-108">Dokončete [první kurz této série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="f348d-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="f348d-109">Nainstalujte modul runtime .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f348d-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="f348d-110">V tomto kurzu nainstalujete a použijete nástroj, který cílí na .NET Core 2,1, takže musíte mít v počítači nainstalovaný tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f348d-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="f348d-111">Pokud chcete nainstalovat modul runtime 2,1, navštivte [stránku ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) a vyhledejte odkaz instalace modulu runtime ve sloupci **Spustit aplikace – modul runtime** .</span><span class="sxs-lookup"><span data-stu-id="f348d-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="f348d-112">Vytvořit soubor manifestu</span><span class="sxs-lookup"><span data-stu-id="f348d-112">Create a manifest file</span></span>

<span data-ttu-id="f348d-113">Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), je nutné jej přidat do souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f348d-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="f348d-114">Ve složce *Microsoft. botsay* přejděte o jednu úroveň výš do složky *úložiště* :</span><span class="sxs-lookup"><span data-stu-id="f348d-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="f348d-115">Vytvořte soubor manifestu spuštěním příkazu [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="f348d-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="f348d-116">Výstup indikuje úspěšné vytvoření souboru.</span><span class="sxs-lookup"><span data-stu-id="f348d-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="f348d-117">Soubor *. config/dotnet-Tools. JSON* zatím neobsahuje žádné nástroje:</span><span class="sxs-lookup"><span data-stu-id="f348d-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="f348d-118">Nástroje uvedené v souboru manifestu jsou k dispozici pro aktuální adresář a podadresáře.</span><span class="sxs-lookup"><span data-stu-id="f348d-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="f348d-119">Aktuální adresář je ten, který obsahuje adresář *. config* se souborem manifestu.</span><span class="sxs-lookup"><span data-stu-id="f348d-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="f348d-120">Když použijete příkaz CLI, který odkazuje na místní nástroj, sada SDK vyhledá soubor manifestu v aktuálním adresáři a v nadřazených adresářích.</span><span class="sxs-lookup"><span data-stu-id="f348d-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="f348d-121">Pokud najde soubor manifestu, ale soubor neobsahuje odkazovaný nástroj, pokračuje v hledání prostřednictvím nadřazených adresářů.</span><span class="sxs-lookup"><span data-stu-id="f348d-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="f348d-122">Hledání skončí, když nalezne odkazovaný nástroj, nebo najde soubor manifestu s `isRoot` nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="f348d-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="f348d-123">Nainstalovat botsay jako místní nástroj</span><span class="sxs-lookup"><span data-stu-id="f348d-123">Install botsay as a local tool</span></span>

<span data-ttu-id="f348d-124">Nainstalujte nástroj z balíčku, který jste vytvořili v prvním kurzu:</span><span class="sxs-lookup"><span data-stu-id="f348d-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="f348d-125">Tento příkaz přidá nástroj do souboru manifestu, který jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="f348d-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="f348d-126">Výstup příkazu zobrazuje, ve kterém souboru manifestu je nově nainstalovaný nástroj:</span><span class="sxs-lookup"><span data-stu-id="f348d-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="f348d-127">Soubor *. config/dotnet-Tools. JSON* teď obsahuje jeden nástroj:</span><span class="sxs-lookup"><span data-stu-id="f348d-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

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

## <a name="use-the-tool"></a><span data-ttu-id="f348d-128">Použití nástroje</span><span class="sxs-lookup"><span data-stu-id="f348d-128">Use the tool</span></span>

<span data-ttu-id="f348d-129">Vyvolejte nástroj spuštěním příkazu `dotnet tool run` ze složky *úložiště* :</span><span class="sxs-lookup"><span data-stu-id="f348d-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="f348d-130">Obnovení místního nástroje nainstalovaného jinými uživateli</span><span class="sxs-lookup"><span data-stu-id="f348d-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="f348d-131">V kořenovém adresáři úložiště obvykle nainstalujete místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="f348d-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="f348d-132">Po vrácení souboru manifestu do úložiště mohou jiní vývojáři získat nejnovější soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="f348d-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="f348d-133">Chcete-li nainstalovat všechny nástroje, které jsou uvedeny v souboru manifestu, mohou spustit jeden `dotnet tool restore` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f348d-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="f348d-134">Otevřete soubor *. config/dotnet-Tools. JSON* a nahraďte obsah následujícím kódem JSON:</span><span class="sxs-lookup"><span data-stu-id="f348d-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

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

1. <span data-ttu-id="f348d-135">Nahraďte `<name>` názvem, který jste použili k vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="f348d-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="f348d-136">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="f348d-136">Save your changes.</span></span>

   <span data-ttu-id="f348d-137">Tato změna je stejná jako získání nejnovější verze z úložiště poté, co někdo jiný nainstaloval balíček `dotnetsay` pro adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="f348d-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="f348d-138">Spusťte příkaz `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="f348d-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="f348d-139">Příkaz vytvoří výstup podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="f348d-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="f348d-140">Ověřte, že jsou dostupné tyto nástroje:</span><span class="sxs-lookup"><span data-stu-id="f348d-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="f348d-141">Výstupem je seznam balíčků a příkazů, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f348d-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="f348d-142">Otestujte nástroje:</span><span class="sxs-lookup"><span data-stu-id="f348d-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="f348d-143">Aktualizace místního nástroje</span><span class="sxs-lookup"><span data-stu-id="f348d-143">Update a local tool</span></span>

<span data-ttu-id="f348d-144">Nainstalovaná verze místního nástroje `dotnetsay` je 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="f348d-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="f348d-145">Nejnovější verze je 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="f348d-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="f348d-146">K aktualizaci nástroje na nejnovější verzi použijte příkaz [dotnet Tool Update](dotnet-tool-update.md) .</span><span class="sxs-lookup"><span data-stu-id="f348d-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="f348d-147">Výstup označuje nové číslo verze:</span><span class="sxs-lookup"><span data-stu-id="f348d-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="f348d-148">Příkaz Update vyhledá první soubor manifestu, který obsahuje ID balíčku, a aktualizuje ho.</span><span class="sxs-lookup"><span data-stu-id="f348d-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="f348d-149">Pokud žádné takové ID balíčku není v žádném souboru manifestu, který je v oboru hledání, sada SDK přidá novou položku do nejbližšího souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f348d-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="f348d-150">Rozsah hledání je až do nadřazených adresářů, dokud se nenajde soubor manifestu s `isRoot = true`.</span><span class="sxs-lookup"><span data-stu-id="f348d-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="f348d-151">Odebrat místní nástroje</span><span class="sxs-lookup"><span data-stu-id="f348d-151">Remove local tools</span></span>

<span data-ttu-id="f348d-152">Nainstalované nástroje odeberte spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="f348d-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="f348d-153">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="f348d-153">Troubleshoot</span></span>

<span data-ttu-id="f348d-154">Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="f348d-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f348d-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="f348d-155">See also</span></span>

<span data-ttu-id="f348d-156">Další informace najdete v tématu [nástroje .NET Core](global-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="f348d-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
