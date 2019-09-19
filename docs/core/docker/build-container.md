---
title: Kontejnerizace aplikace s využitím kurzu Docker
description: V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5e05fd2a38770ce348fbbfcfaa88267217b806bf
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116558"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Kurz: Kontejnerizace aplikace .NET Core

V tomto kurzu se naučíte, jak vytvořit image Docker, která obsahuje vaši aplikaci .NET Core. Image se dá použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.

Naučíte se:

> [!div class="checklist"]
>
> * Vytvoření a publikování jednoduché aplikace .NET Core
> * Vytvoření a konfigurace souboru Dockerfile pro .NET Core
> * Sestavení image Docker
> * Vytvoření a spuštění kontejneru Docker

Porozumíte sestavení kontejneru Docker a nasazování úloh pro aplikaci .NET Core. *Platforma Docker* používá *modul Docker* k rychlému sestavování a zabalení aplikací jako *imagí Docker*. Tyto image jsou napsané ve formátu *souboru Dockerfile* , aby je bylo možné nasadit a spustit v vrstveném kontejneru.

## <a name="prerequisites"></a>Požadavky

Nainstalujte následující požadavky:

* [Sada .NET Core 2,2 SDK](https://dotnet.microsoft.com/download)\
Pokud máte nainstalované rozhraní .NET Core, pomocí `dotnet --info` příkazu určete, kterou sadu SDK používáte.

* [Docker Community Edition](https://www.docker.com/products/docker-desktop)

* Dočasná pracovní složka pro *souboru Dockerfile* a ukázkovou aplikaci .NET Core. V tomto kurzu se název `docker-working` používá jako pracovní složka.

### <a name="use-sdk-version-22"></a>Použít sadu SDK verze 2,2

Pokud používáte sadu SDK, která je novější, třeba 3,0, ujistěte se, že je aplikace nucená používat sadu SDK sady 2,2. Vytvořte v pracovní složce `global.json` soubor s názvem a vložte do něj následující kód JSON:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Soubor uložte. Přítomnost souboru vynutí, aby rozhraní .NET Core používalo verzi 2,2 pro `dotnet` jakýkoli příkaz nazvaný z této složky a níže.

## <a name="create-net-core-app"></a>Vytvoření aplikace .NET Core

Potřebujete aplikaci .NET Core, kterou bude kontejner Docker spustit. Otevřete terminál, vytvořte pracovní složku, pokud jste to ještě neudělali, a zadejte ji. V pracovní složce spusťte následující příkaz, který vytvoří nový projekt v podadresáři s názvem App:

```dotnetcli
dotnet new console -o app -n myapp
```

Váš strom složek bude vypadat následovně:

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

Příkaz vytvoří novou složku s názvem App a vygeneruje aplikaci Hello World. `dotnet new` Zadejte složku *aplikace* a spusťte příkaz `dotnet run`. Zobrazí se následující výstup:

```console
> dotnet run
Hello World!
```

Výchozí šablona vytvoří aplikaci, která se vytiskne do terminálu a pak se ukončí. V tomto kurzu použijete aplikaci, která bude mít neomezenou dobu. V textovém editoru otevřete soubor **program.cs** . V současné době by měl vypadat jako v následujícím kódu:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Nahraďte soubor následujícím kódem, který počítá čísla každou sekundu:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Uložte soubor a otestujte program znovu pomocí `dotnet run`. Mějte na paměti, že tato aplikace bude běžet po neomezenou dobu. K zastavení použijte příkaz zrušit <kbd>CTRL + C</kbd> . Zobrazí se následující výstup:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Pokud předáte číslo do příkazového řádku do aplikace, bude se počítat jenom s touto velikostí a pak se ukončí. Zkuste to s `dotnet run -- 5` počtem až pěti.

> [!NOTE]
> Jakékoli parametry po `--` nejsou předány `dotnet run` do příkazu a místo toho jsou předány do aplikace.

## <a name="publish-net-core-app"></a>Publikování aplikace .NET Core

Před přidáním aplikace .NET Core do image Docker ji publikujte. Chcete se ujistit, že kontejner spouští publikovanou verzi aplikace, když je spuštěný.

Z pracovní složky zadejte složku **aplikace** s příkladem zdrojového kódu a spusťte následující příkaz:

```dotnetcli
dotnet publish -c Release
```

Tento příkaz zkompiluje vaši aplikaci do složky pro **publikování** . Cesta ke složce pro **publikování** z pracovní složky by měla být`.\app\bin\Release\netcoreapp2.2\publish\`

Získejte výpis adresáře složky pro publikování a ověřte, zda byla vytvořena aplikace **MyApp. dll** . Ve složce **aplikace** spusťte jeden z následujících příkazů:

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Vytvoření souboru Dockerfile

Soubor *souboru Dockerfile* používá `docker build` příkaz k vytvoření image kontejneru. Tento soubor je soubor ve formátu prostého textu s názvem *souboru Dockerfile* , který nemá příponu.

V terminálu přejděte v adresáři do pracovní složky, kterou jste vytvořili na začátku. Vytvořte v pracovní složce soubor s názvem *souboru Dockerfile* a otevřete ho v textovém editoru. Jako první řádek souboru přidejte následující příkaz:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

Příkaz instruuje Docker, aby vyčetl obrázek s příznakem **2,2** z úložiště **MCR.Microsoft.com/dotnet/Core/Runtime.** `FROM` Ujistěte se, že vyžádáte modul runtime .NET Core, který odpovídá modulu runtime, který cílí na vaši sadu SDK. Například aplikace vytvořená v předchozí části používala sadu .NET Core 2,2 SDK a vytvořila aplikaci cílenou na rozhraní .NET Core 2,2. Základní bitová kopie, na kterou odkazuje *souboru Dockerfile* , je označená jako **2,2**.

Uložte soubor *souboru Dockerfile* . Adresářová struktura pracovní složky by měla vypadat takto. Některé soubory hlubší úrovně a složky byly vyjmuty, aby se ušetřilo místo v tomto článku:

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

Z terminálu spusťte následující příkaz:

```console
docker build -t myimage -f Dockerfile .
```

Docker zpracuje každý řádek v *souboru Dockerfile*. V příkazu dá Docker pokyn k použití aktuální složky k vyhledání *souboru Dockerfile.* `.` `docker build` Tento příkaz sestaví image a vytvoří místní úložiště s názvem **MyImage** , které odkazuje na tuto image. Po dokončení tohoto příkazu spusťte `docker images` příkaz a zobrazí se seznam nainstalovaných imagí:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

Všimněte si, že tyto dva obrázky sdílejí stejnou hodnotu **ID obrázku** . Tato hodnota je stejná mezi oběma obrazci, protože jediný příkaz v *souboru Dockerfile* byl založen na novém obrázku na stávající imagi. Pojďme do *souboru Dockerfile*přidat dva příkazy. Každý příkaz vytvoří novou vrstvu obrázku s posledním příkazem reprezentujícím obrázek, na který bude **MyImage** úložiště odkazovat.

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` Příkaz vyzve Docker ke zkopírování zadané složky ve vašem počítači do složky v kontejneru. V tomto příkladu je složka pro **publikování** zkopírována do složky s názvem **App** v kontejneru.

Následující příkaz `ENTRYPOINT`instruuje Docker ke konfiguraci kontejneru tak, aby běžel jako spustitelný soubor. Po spuštění `ENTRYPOINT` kontejneru se příkaz spustí. Po ukončení tohoto příkazu se kontejner automaticky zastaví.

V terminálu spusťte `docker build -t myimage -f Dockerfile .` příkaz a po jeho dokončení spusťte `docker images`příkaz.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořila **ID obrázku**. Konečné **ID image** (bude se lišit) bude **ddcc6646461b** a dál vytvoříte kontejner na základě tohoto obrázku.

## <a name="create-a-container"></a>Vytvoření kontejneru

Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner. Kontejner můžete vytvořit dvěma způsoby. Nejdřív vytvořte nový kontejner, který se zastaví.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

Výše uvedený příkaz vytvoří kontejner založený na imagi **MyImage.** `docker create` Výstup tohoto příkazu ukazuje **ID kontejneru** (bude se lišit) vytvořeného kontejneru. Chcete-li zobrazit seznam *všech* kontejnerů, použijte `docker ps -a` příkaz:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Správa kontejneru

Každému kontejneru je přiřazen náhodný název, který můžete použít k odkazování na tuto instanci kontejneru. Například kontejner, který byl vytvořen automaticky, zvolil název **boring_matsumoto** (bude jiný a tento název lze použít ke spuštění kontejneru). Automatický název přepíšete pomocí konkrétního `docker create --name` parametru.

Následující příklad používá `docker start` příkaz ke spuštění kontejneru a poté `docker ps` používá příkaz k zobrazení pouze kontejnerů, které jsou spuštěny:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

`docker stop` Podobně příkaz zastaví kontejner. Následující příklad používá `docker stop` příkaz k zastavení kontejneru a poté `docker ps` používá příkaz k zobrazení, že žádné kontejnery neběží.

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Připojit ke kontejneru

Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup. Použijte příkazy `docker attach` a ke spuštění kontejneru a k prohlížení výstupního datového proudu. `docker start` V tomto příkladu se k odpojení od běžícího kontejneru používá příkaz <kbd>CTRL + C</kbd> . To může ve skutečnosti ukončit proces v kontejneru, který zastaví kontejner. Parametr zajistí, že <kbd>CTRL + C</kbd> nezastaví proces v kontejneru. `--sig-proxy=false`

Po odpojení od kontejneru znovu připojte, abyste ověřili, že pořád běží a počítá se.

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Odstranění kontejneru

Pro účely tohoto článku nechcete, aby kontejnery právě neprováděly žádné akce. Odstraňte kontejner, který jste dříve vytvořili. Pokud je kontejner spuštěný, zastavte ho.

```console
> docker stop boring_matsumoto
```

Následující příklad zobrazí seznam všech kontejnerů. Pak pomocí příkazu tento `docker rm` kontejner odstraní a pak u všech spuštěných kontejnerů zkontroluje druhou dobu.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Jeden běh

Docker poskytuje `docker run` příkaz pro vytvoření a spuštění kontejneru jako jediného příkazu. Tento příkaz eliminuje nutnost spuštění `docker create` a pak. `docker start` Tento příkaz lze také nastavit tak, aby při zastavení kontejneru automaticky odstranil kontejner. Například použijte `docker run -it --rm` k provedení dvou věcí, nejdřív, automatické použití aktuálního terminálu k připojení ke kontejneru a po dokončení kontejneru ho odeberte:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

V `docker run -it`systému, příkaz <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, který zase zastaví kontejner. Vzhledem k `--rm` tomu, že byl zadán parametr, kontejner je automaticky odstraněn při zastavení procesu. Ověřte, že neexistuje:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Změnit vstupní bod

Příkaz také umožňuje `ENTRYPOINT` upravit příkaz z souboru Dockerfile a spustit něco jiného, ale pouze pro tento kontejner. `docker run` Například použijte následující příkaz ke spuštění `bash` nebo. `cmd.exe` V případě potřeby upravte příkaz.

#### <a name="windows"></a>Windows
V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`. Stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončíte proces a zastavíte kontejner.

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>Linux

V tomto příkladu `ENTRYPOINT` se změní na `bash`. `quit` Příkaz se spustí, který ukončí proces a zastaví kontejner.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Důležité příkazy

Docker má mnoho různých příkazů, které pokrývají, co chcete s kontejnerem a obrázky udělat. Tyto příkazy Docker jsou zásadní pro správu vašich kontejnerů:

* [sestavení Docker](https://docs.docker.com/engine/reference/commandline/build/)
* [spuštění Docker](https://docs.docker.com/engine/reference/commandline/run/)
* [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/)
* [zastavení Docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
* [Docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Obrázek Docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Vyčištění prostředků

V tomto kurzu jste vytvořili kontejnery a image. Pokud chcete, tyto prostředky odstraňte. Následující příkazy použijte k

01. Vypsat všechny kontejnery

    ```console
    > docker ps -a
    ```

02. Zastavte kontejnery, které jsou spuštěny. `CONTAINER_NAME` Představuje název automaticky přiřazený kontejneru.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Odstranění kontejneru

    ```console
    > docker rm CONTAINER_NAME
    ```

Pak na počítači odstraňte všechny image, které už nechcete. Odstraňte image vytvořenou *souboru Dockerfile* a pak odstraňte image .NET Core, na které byl *souboru Dockerfile* založen. Můžete použít **ID obrázku** nebo **úložiště:** řetězec ve formátu značek.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

`docker images` Pomocí příkazu zobrazte seznam nainstalovaných imagí.

> [!NOTE]
> Soubory obrázků můžou být velké. Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji vaší aplikace. Při plánování vytváření dalších imagí na základě tohoto modulu runtime obvykle zachováte základní image s nainstalovaným modulem runtime.

## <a name="next-steps"></a>Další kroky

* [Vyzkoušejte si kurz ASP.NET Core mikroslužeb.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Projděte si služby Azure, které podporují kontejnery.](https://azure.microsoft.com/overview/containers/)
* [Přečtěte si o příkazech souboru Dockerfile.](https://docs.docker.com/engine/reference/builder/)
* [Prozkoumejte nástroje kontejnerů pro Visual Studio](/visualstudio/containers/overview)
