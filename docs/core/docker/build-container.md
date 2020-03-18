---
title: Kontejnerize aplikace s kurzem Dockeru
description: V tomto kurzu se dozvíte, jak kontejnerizovat aplikaci .NET Core s Dockerem.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157827"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Kurz: Kontejnerize aplikace .NET Core

Tento kurz vás naučí, jak vytvořit bitovou kopii Dockeru, která obsahuje vaši aplikaci .NET Core. Image lze použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.

Naučíte se:

> [!div class="checklist"]
>
> - Vytvoření a publikování jednoduché aplikace .NET Core
> - Vytvoření a konfigurace souboru Dockerfile pro jádro rozhraní .NET
> - Sestavení image Dockeru
> - Vytvoření a spuštění kontejneru Dockeru

Porozumíte sestavení a nasazení úloh kontejneru Dockeru pro aplikaci .NET Core. *Platforma Dockeru* používá *modul Dockeru* k rychlému vytváření a balení aplikací jako *imitace Dockeru*. Tyto image jsou zapsány ve formátu *Dockerfile* k nasazení a spuštění ve vrstvené kontejneru.

> [!TIP]
> Pokud pracujete s existující aplikací ASP.NET Core, přečtěte si informace o tom, [jak kontejnerizovat ASP.NET základní aplikace.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

## <a name="prerequisites"></a>Požadavky

Nainstalujte následující požadavky:

- [Sada SDK jádra .NET 3.1](https://dotnet.microsoft.com/download)\
Pokud máte nainstalovanou službu `dotnet --info` .NET Core, použijte příkaz k určení, kterou sadu SDK používáte.

- [Komunitní edice Dockeru](https://www.docker.com/products/docker-desktop)

- Dočasná pracovní složka pro *aplikaci Dockerfile* a .NET Core example. V tomto kurzu název *docker-working* se používá jako pracovní složka.

## <a name="create-net-core-app"></a>Vytvoření aplikace v .NET Core

Potřebujete aplikaci .NET Core, kterou spustí kontejner Dockeru. Otevřete terminál, vytvořte pracovní složku, pokud jste tak dosud neučinili, a zadejte ji. V pracovní složce spusťte následující příkaz a vytvořte nový projekt v podadresáři s názvem *app*:

```dotnetcli
dotnet new console -o app -n myapp
```

Strom složek bude vypadat takto:

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

Příkaz `dotnet new` vytvoří novou složku s názvem *aplikace* a generuje aplikaci "Hello World". Zadejte složku *aplikace* a `dotnet run`spusťte příkaz . Zobrazí se následující výstup:

```console
> dotnet run
Hello World!
```

Výchozí šablona vytvoří aplikaci, která se vytiskne na terminál a poté ji ukončí. Pro účely tohoto kurzu budete používat aplikaci, která smyčky neomezeně dlouho. Otevřete *soubor Program.cs* v textovém editoru. V současné době by měl vypadat jako následující kód:

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
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Uložte soubor a otestujte program znovu pomocí aplikace `dotnet run`. Nezapomeňte, že tato aplikace běží neomezeně dlouho. Chcete-li příkaz cancel <kbd>CTRL</kbd>+<kbd>C,</kbd> zastavte jej. Zobrazí se následující výstup:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Pokud aplikaci předáte číslo na příkazovém řádku, bude se počítat pouze do této částky a pak ji ukončíte. Zkus to `dotnet run -- 5` s počítat do pěti.

> [!NOTE]
> Všechny parametry `--` po nejsou `dotnet run` předány příkazu a místo toho jsou předány do aplikace.

## <a name="publish-net-core-app"></a>Publikování aplikace .NET Core

Než přidáte aplikaci .NET Core do bitové kopie Dockeru, publikujte ji. Chcete se ujistit, že kontejner spustí publikovanou verzi aplikace při spuštění.

Z pracovní složky zadejte složku *aplikace* s ukázkovým zdrojovým kódem a spusťte následující příkaz:

```dotnetcli
dotnet publish -c Release
```

Tento příkaz zkompiluje aplikaci do složky *publikování.* Cesta ke složce *publikování* z pracovní složky by měla být`.\app\bin\Release\netcoreapp3.1\publish\`

Ze složky *aplikace* získáte seznam adresářů složky publikování, abyste ověřili, že byl vytvořen soubor *myapp.dll.*

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

Pokud používáte Linux nebo macOS, `ls` pomocí příkazu získejte výpis adresáře a ověřte, zda byl vytvořen soubor *myapp.dll.*

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Vytvoření souboru Dockerfile

Soubor *Dockerfile* se používá `docker build` příkazem k vytvoření image kontejneru. Tento soubor je textový soubor s názvem *Dockerfile,* který nemá příponu.

V terminálu přejděte do adresáře do pracovní složky, kterou jste vytvořili na začátku. Vytvořte soubor s názvem *Dockerfile* v pracovní složce a otevřete jej v textovém editoru. V závislosti na typu aplikace, kterou chcete kontejnerizovat, zvolíte buď ASP.NET core runtime nebo .NET Core runtime. Pokud jste na pochybách, zvolte ASP.NET core runtime, který zahrnuje .NET Core runtime. Tento kurz bude používat ASP.NET image core runtime, ale aplikace vytvořená v předchozích částech je aplikace .NET Core.

- ASP.NET core runtime

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- Doba běhu jádra .NET

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

Příkaz `FROM` říká Dockeru, aby stáhl obrázek označený **3.1** ze zadaného úložiště. Ujistěte se, že vytáhnete runtime verzi, která odpovídá runtime cílené sdk. Například aplikace vytvořená v předchozí části používala sdk rozhraní .NET Core 3.1 a základní bitovou kopii uvedenou v *souboru Dockerfile* je označena **hodnotou 3.1**.

Uložte soubor *Dockerfile.* Adresářová struktura pracovní složky by měla vypadat takto. Některé soubory a složky na hlubší úrovni byly v článku vyříznuty, aby se ušetřilo místo:

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
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

Docker zpracuje každý řádek v *Dockerfile*. Příkaz `.` v `docker build` příkazu říká Dockeru, aby použil aktuální složku k nalezení *souboru Dockerfile*. Tento příkaz vytvoří image a vytvoří místní úložiště s názvem **myimage,** který odkazuje na tuto bitovou kopii. Po dokončení tohoto příkazu se spusťte `docker images` a zobrazte seznam nainstalovaných bitových kopií:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Všimněte si, že dva obrazy sdílejí stejnou hodnotu **ID image.** Hodnota je stejná mezi oběma bitovými kopiemi, protože jediným příkazem v *souboru Dockerfile* bylo založit novou bitovou kopii na existující bitové kopii. Přidáme dva příkazy do *Dockerfile*. Každý příkaz vytvoří novou vrstvu obrazu s konečným příkazem představujícím obraz, na který položka úložiště **myimage** odkazuje.

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Příkaz `COPY` říká Dockeru, aby zkopíroval zadanou složku v počítači do složky v kontejneru. V tomto příkladu se složka *publikování* zkopíruje do složky s názvem *aplikace* v kontejneru.

Další příkaz `ENTRYPOINT`, říká Docker nakonfigurovat kontejner spustit jako spustitelný soubor. Při spuštění kontejneru `ENTRYPOINT` se spustí příkaz. Když tento příkaz skončí, kontejner se automaticky zastaví.

Z terminálu, `docker build -t myimage -f Dockerfile .` spustit a po dokončení `docker images`tohoto příkazu, spustit .

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořil **ID IMAGE**. Konečné **ID image** (vaše bude jiné) je **ddcc6646461b** a dále vytvoříte kontejner založený na tomto obrázku.

## <a name="create-a-container"></a>Vytvoření kontejneru

Teď, když máte obrázek, který obsahuje vaši aplikaci, můžete vytvořit kontejner. Kontejner můžete vytvořit dvěma způsoby. Nejprve vytvořte nový kontejner, který je zastaven.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

Příkaz `docker create` shora vytvoří kontejner založený na image **myimage.** Výstup tohoto příkazu zobrazí **ID kontejneru** (vaše se bude lišit) vytvořeného kontejneru. Chcete-li zobrazit seznam *všech* `docker ps -a` kontejnerů, použijte příkaz:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Správa kontejneru

Každému kontejneru je přiřazen náhodný název, který můžete použít k odkazování na tuto instanci kontejneru. Například kontejner, který byl vytvořen automaticky vybral název **gallant_lehmann** (vaše se bude lišit) a tento název lze použít ke spuštění kontejneru. Automatický název přepíšete určitým názvem pomocí `docker create --name` parametru.

Následující příklad používá `docker start` příkaz ke spuštění kontejneru `docker ps` a potom používá příkaz zobrazit pouze kontejnery, které jsou spuštěny:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Podobně `docker stop` příkaz zastaví kontejner. Následující příklad používá `docker stop` příkaz k zastavení kontejneru `docker ps` a potom pomocí příkazu zobrazí, že jsou spuštěny žádné kontejnery:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Připojení ke kontejneru

Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup. Pomocí `docker start` příkazů `docker attach` a spusťte kontejner a prohlédněte si výstupní datový proud. V tomto příkladu <kbd>klávesy CTRL + C</kbd> se používá k odpojení od spuštěného kontejneru. Tento úhoz může ve skutečnosti ukončit proces v kontejneru, který zastaví kontejneru. Parametr `--sig-proxy=false` zajišťuje, že <kbd>CTRL + C</kbd> nezastaví proces v kontejneru.

Po odpojení od kontejneru znovu připojte a ověřte, zda je stále spuštěna a počítá.

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Odstranění kontejneru

Pro účely tohoto článku nechcete, aby kontejnery jen poflakovat nic nedělá. Odstraňte kontejner, který jste dříve vytvořili. Pokud je kontejner spuštěn, zastavte jej.

```console
> docker stop gallant_lehmann
```

V následujícím příkladu jsou uvedeny všechny kontejnery. Potom pomocí `docker rm` příkazu odstranit kontejner a potom zkontroluje podruhé pro všechny spuštěné kontejnery.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Jeden běh

Docker poskytuje `docker run` příkaz k vytvoření a spuštění kontejneru jako jeden příkaz. Tento příkaz eliminuje potřebu `docker create` spuštění `docker start`a potom . Tento příkaz můžete také nastavit tak, aby automaticky odstranil kontejner, když se kontejner zastaví. Například použijte `docker run -it --rm` k provedení dvou věcí, nejprve automaticky použijte aktuální terminál pro připojení ke kontejneru a po dokončení kontejneru jej odeberte:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Pomocí `docker run -it`příkazu <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, což zase zastaví kontejner. Vzhledem `--rm` k tomu, že parametr byl poskytnut, kontejner je automaticky odstraněn při zastavení procesu. Ověřte, zda neexistuje:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Změna vstupního bodu

Příkaz `docker run` také umožňuje upravit `ENTRYPOINT` příkaz z *Dockerfile* a spustit něco jiného, ale pouze pro tento kontejner. Pomocí následujícího příkazu můžete `bash` `cmd.exe`například spustit nebo . Podle potřeby upravte příkaz.

#### <a name="windows"></a>Windows

V tomto `ENTRYPOINT` příkladu `cmd.exe`se změní na . <kbd>Ctrl</kbd>+<kbd>C</kbd> je stisknuto ukončit proces a zastavit kontejner.

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

V tomto `ENTRYPOINT` příkladu `bash`se změní na . Příkaz `quit` je spuštěn, který ukončí proces a zastaví kontejner.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Základní příkazy

Docker má mnoho různých příkazů, které pokrývají, co chcete dělat s kontejnerem a image. Tyto příkazy Dockeru jsou nezbytné pro správu kontejnerů:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker spustit](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [obrázek dockeru](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Během tohoto kurzu jste vytvořili kontejnery a obrázky. Pokud chcete, odstraňte tyto prostředky. Pomocí následujících příkazů

01. Vypsat všechny kontejnery

    ```console
    > docker ps -a
    ```

02. Zastavit kontejnery, které jsou spuštěny. Představuje `CONTAINER_NAME` název automaticky přiřazený kontejneru.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Odstranění kontejneru

    ```console
    > docker rm CONTAINER_NAME
    ```

Dále odstraňte všechny obrázky, které již v počítači nechcete. Odstraňte bitovou kopii vytvořenou *souborem Dockerfile* a potom odstraňte bitovou kopii .NET Core, na které byl soubor *Dockerfile* založen. Můžete použít **ID OBRAZU** nebo řetězec ve formátu **REPOSITORY:TAG.**

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Pomocí `docker images` příkazu zobrazíte seznam nainstalovaných bitových kopií.

> [!NOTE]
> Obrazové soubory mohou být velké. Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji aplikace. Obvykle uchováváte základní bitové kopie s nainstalovaným runtime, pokud plánujete vytvářet další bitové kopie na základě tohoto běhu.

## <a name="next-steps"></a>Další kroky

- [Přečtěte si, jak kontejnerizovat aplikaci ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Vyzkoušejte kurz ASP.NET Core Microservice.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Zkontrolujte služby Azure, které podporují kontejnery.](https://azure.microsoft.com/overview/containers/)
- [Přečtěte si o příkazech Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Prozkoumejte nástroje kontejneru pro Visual Studio](/visualstudio/containers/overview)
