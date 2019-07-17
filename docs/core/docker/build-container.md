---
title: Kontejnerizace aplikace pomocí Docker kurz
description: V tomto kurzu se dozvíte, jak kontejnerizovat aplikace .NET Core s Dockerem.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 8c50fb20a6a2273b17825b83b1a94d9abd2c158a
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235710"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Kurz: Kontejnerizace aplikace .NET Core

V tomto kurzu se naučíte, jak sestavit image Dockeru obsahující aplikaci .NET Core. Na obrázku slouží k vytvoření kontejnerů pro vaše místní vývojové prostředí, privátního cloudu nebo veřejného cloudu.

Naučíte se:

> [!div class="checklist"]
> * Vytvoření a publikování jednoduchou aplikaci .NET Core
> * Vytvoření a konfigurace souboru Dockerfile pro .NET Core
> * Sestavíte image Dockeru
> * Vytvoření a spuštění kontejneru Dockeru

Rozumíte budete Docker, kontejner sestavení a nasazení úlohy pro aplikace .NET Core. *Platforma Docker* používá *modul Docker* k rychlému sestavování a balíčky aplikací jako *imagí Dockeru*. Tyto Image jsou napsané v *soubor Dockerfile* formát nasazení a spuštění v kontejneru vrstvami.

## <a name="prerequisites"></a>Požadavky

Nainstalujte následující požadavky:

* [.NET core 2.2 SDK](https://dotnet.microsoft.com/download)\
Pokud máte nainstalovaný .NET Core, použijte `dotnet --info` příkaz k určení SDK, které používáte.

* [Docker Community Edition](https://www.docker.com/products/docker-desktop)

* Dočasnou pracovní složku pro *soubor Dockerfile* a ukázkovou aplikaci .NET Core. V tomto kurzu se název `docker-working` slouží jako pracovní složku.

### <a name="use-sdk-version-22"></a>Použití sady SDK verze 2.2

Pokud používáte sadu SDK, která je novější, jako je 3.0, ujistěte se, že, že vaše aplikace bude muset používat sady SDK 2.2. Vytvořte soubor s názvem `global.json` v pracovní složce a vložte následující kód json:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Soubor uložte. Vynutí přítomnost souboru .NET Core na použití pro všechny verze 2.2 `dotnet` příkaz volat z této složky a nižší.

## <a name="create-net-core-app"></a>Vytvoření .NET Core aplikace

Je nutné aplikaci .NET Core, který se spustí kontejner Dockeru. Otevřete terminál, vytvořte pracovní složky, pokud jste to ještě neudělali a zadejte ji. V pracovní složce spusťte následující příkaz pro vytvoření nového projektu v podadresáři s názvem aplikace:

```console
dotnet new console -o app -n myapp
```

Strom složek bude vypadat nějak takto:

```console
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

`dotnet new` Příkaz vytvoří novou složku s názvem *aplikace* a vygeneruje aplikace "Hello World". Zadejte *aplikace* složky a spusťte tento příkaz `dotnet run`. Se zobrazí následující výstup:

```console
> dotnet run
Hello World!
```

Výchozí šablona vytvoří aplikaci, která vytiskne do terminálu a pak se ukončí. Pro účely tohoto kurzu budete používat aplikaci, která smyčky po neomezenou dobu. Otevřít **Program.cs** souboru v textovém editoru. By měl nyní vypadat jako následující kód:

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

Soubor nahraďte následující kód, který počítá každou sekundu:

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

Uložte soubor a testovat program znovu s `dotnet run`. Mějte na paměti, že tato aplikace běží po neomezenou dobu. Použití příkazu Storno <kbd>CTRL + C</kbd> zastavte ji. Se zobrazí následující výstup:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Pokud předáte číslo na příkazovém řádku do aplikace, bude se pouze počítat až, který částka a poté ukončete. Vyzkoušejte si to s `dotnet run -- 5` počet na 5.

> [!NOTE]
> Žádné parametry po `--` nejsou předán `dotnet run` příkazů a místo toho jsou předány do vaší aplikace.

## <a name="publish-net-core-app"></a>Publikování .NET Core aplikace

Abyste mohli přidat aplikaci .NET Core do image Dockeru, publikujte ho. Chcete, aby se zajistilo, že se kontejner spustí publikovanou verzi aplikace při spuštění.

Z pracovní složky, zadejte **aplikace** složku s příkladem zdrojového kódu a spusťte následující příkaz:

```console
dotnet publish -c Release
```

Tento příkaz zkompiluje aplikaci tak, aby **publikovat** složky. Cesta k **publikovat** by měla být složka z pracovní složky `.\app\bin\Release\netcoreapp2.2\publish\`

Získat výpis složky publikování a ověřte, zda **myapp.dll** byl vytvořen. Z **aplikace** složky, spusťte následující příkazy:

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

*Soubor Dockerfile* soubor je používán `docker build` příkaz pro vytvoření image kontejneru. Tento soubor je soubor ve formátu prostého textu s názvem *soubor Dockerfile* , který nemá žádné rozšíření.

V terminálu přejděte na adresář pro pracovní složky, kterou jste vytvořili na začátku nahoru. Vytvořte soubor s názvem *soubor Dockerfile* ve své pracovní složce a otevřete ho v textovém editoru. Jako první řádek souboru přidejte následující příkaz:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

`FROM` Příkaz říká Dockeru stáhnout image označit **2.2** z **mcr.microsoft.com/dotnet/core/runtime** úložiště. Ujistěte se, že o přijetí změn na .NET Core runtime, který se shoduje s cílem sady SDK modulu runtime. Například aplikace vytvořené v předchozí části používá .NET Core 2.2 SDK a vytvořili aplikaci, na který .NET Core 2.2. Takže základní image podle *soubor Dockerfile* je označené **2.2**.

Uložit *soubor Dockerfile* souboru. Struktura adresářů pracovní složky by měl vypadat nějak takto. Některé z hlubší úrovně soubory a složky byly snížili pro úsporu místa v následujícím článku:

```console
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

Docker bude zpracovávat každý řádek v *soubor Dockerfile*. `.` v `docker build` příkaz říká Dockeru použití aktuální složku k vyhledání *soubor Dockerfile*. Tento příkaz sestaví image a vytvoří místní úložiště s názvem **myimage** , která odkazuje na této bitové kopie. Po dokončení tohoto příkazu Spustit `docker images` zobrazíte seznam imagí, které jsou nainstalovány:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

Všimněte si, že dvě bitové kopie sdílet stejný **ID bitové kopie** hodnotu. Hodnota je mezi obě bitové kopie, protože jediný příkaz v *soubor Dockerfile* byla na základní novou imagí v existující imagi. Přidejme dva příkazy, které *soubor Dockerfile*. Každý příkaz vytvoří novou image vrstvu s poslední příkaz představující obrázek **myimage** úložiště bude odkazovat na.

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` Příkaz sděluje kopírování zadané složky na vašem počítači do složky v kontejneru Dockeru. V tomto příkladu **publikovat** složky je zkopírován do složky s názvem **aplikace** v kontejneru.

Další příkaz `ENTRYPOINT`, říká Dockeru konfigurace kontejner pro spuštění jako spustitelný soubor. Při spuštění kontejneru, `ENTRYPOINT` příkaz spustí. Až příkaz skončí, automaticky zastaví kontejner.

Z terminálu spusťte `docker build -t myimage -f Dockerfile .` a po dokončení příkazu, který, spusťte `docker images`.

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

Každý příkaz v *soubor Dockerfile* vygenerované vrstvy a vytvoření **ID bitové kopie**. Finální **ID bitové kopie** (bude jiné) je **ddcc6646461b** a dále vytvoříte na základě této image kontejneru.

## <a name="create-a-container"></a>Vytvoření kontejneru

Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner. Kontejner můžete vytvořit dvěma způsoby. Nejprve vytvořte nový kontejner, který je zastavená.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

`docker create` Příkaz výše vytvoří kontejner na základě **myimage** bitové kopie. Výstup tohoto příkazu se dozvíte **ID KONTEJNERU** (bude jiné) vytvořený kontejneru. Pokud chcete zobrazit seznam *všechny* kontejnery, použít `docker ps -a` příkaz:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Správa kontejneru

Každý kontejner je přiřazený náhodný název, který vám pomůže odkazovat na instanci kontejneru. Například kontejner, který byl automaticky vytvořen zvolili název **boring_matsumoto** (bude jiný) a tento název je možné spustit kontejner. Přepsat automatické název s konkrétní skupinu pomocí `docker create --name` parametru.

V následujícím příkladu `docker start` příkazu spusťte kontejner a pak používá `docker ps` příkazu můžete zobrazit pouze kontejnery, na kterých běží:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

Podobně platí `docker stop` příkaz zastaví kontejneru. V následujícím příkladu `docker stop` příkaz k zastavení kontejner a pak používá `docker ps` příkazu můžete zobrazit, zda jsou spuštěny žádné kontejnery.

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Připojte se ke kontejneru

Po spuštění kontejneru můžete připojit k němu chcete zobrazit výstup. Použití `docker start` a `docker attach` příkazů spusťte kontejner a náhled výstupního datového proudu. V tomto příkladu <kbd>CTRL + C</kbd> příkaz slouží k oddělení spuštěný kontejner. Ve skutečnosti to může ukončit proces v kontejneru se kontejner zastaví. `--sig-proxy=false` Parametr zajišťuje, že <kbd>CTRL + C</kbd> nezpůsobí ukončení procesu v kontejneru.

Chcete-li ověřit, že je stále spuštěna a počítání znovu připojte po odpojení z kontejneru.

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

### <a name="delete-a-container"></a>Odstranit kontejner

Pro účely tohoto článku už nechcete, jenom předsazení kolem nicneděláním kontejnery. Odstraňte kontejner, který jste předtím vytvořili. Pokud je kontejner spuštěný, zastavte ho.

```console
> docker stop boring_matsumoto
```

Následující příklad vypíše všechny kontejnery. Poté použije `docker rm` příkaz odstranit kontejner a poté ověří podruhé pro všechny spuštěné kontejnery.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Najednou

Docker nabízí `docker run` příkaz pro vytvoření a spuštění kontejneru jako jeden příkaz. Tento příkaz se eliminuje potřeba spustit `docker create` a potom `docker start`. Můžete také nastavit tento příkaz automaticky odstranit kontejner, když se kontejner zastaví. Například použít `docker run -it --rm` provést dva kroky, nejprve aktuální terminálu automaticky použít pro připojení ke kontejneru a pak ji odebrat po dokončení kontejneru:

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

S `docker run -it`, <kbd>CTRL + C</kbd> příkaz zastaví proces, který je spuštěn v kontejneru, což zase zastaví kontejner. Vzhledem k tomu, `--rm` nebyl zadán parametr, kontejneru se automaticky odstraní, když se zastaví proces. Ověřte, že neexistuje:

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Změnit vstupní bod

`docker run` Příkaz také umožňuje upravovat `ENTRYPOINT` příkaz *soubor Dockerfile* a spusťte něco jiného, ale pouze pro tento kontejner. Například použijte následující příkaz pro spuštění `bash` nebo `cmd.exe`. Podle potřeby upravte příkaz.

#### <a name="windows"></a>Windows
V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`. <kbd>CTRL + C</kbd> stisknutí ukončit proces a zastavení kontejneru.

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

V tomto příkladu `ENTRYPOINT` se změní na `bash`. `quit` Po spuštění příkazu, který ukončí proces a zastavit kontejner.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Základní příkazy

Docker má mnoho různých příkazů, které se týkají, co byste chtěli provést v kontejneru a obrázky. Tyto příkazy Dockeru jsou nezbytné ke správě kontejnerů:

* [sestavení dockeru](https://docs.docker.com/engine/reference/commandline/build/)
* [docker, spusťte](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [rmi dockeru](https://docs.docker.com/engine/reference/commandline/rmi/)
* [image dockeru](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Během tohoto kurzu jste vytvořili kontejnery a obrázky. Pokud chcete, odstraňte tyto prostředky. Pomocí následujících příkazů

01. Vypsat všechny kontejnery

    ```console
    > docker ps -a
    ```

02. Zastavte kontejnerů, které jsou spuštěny. `CONTAINER_NAME` Představuje název automaticky přiřazují do kontejneru.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Odstranění kontejneru

    ```console
    > docker rm CONTAINER_NAME
    ```

V dalším kroku odstraňte všechny Image, které už nechcete na svém počítači. Odstranit image vytvořené vaší *soubor Dockerfile* a potom odstranit image .NET Core *soubor Dockerfile* byl založen na. Můžete použít **ID bitové kopie** nebo **úložiště: značka** řetězec ve formátu.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

Použití `docker images` příkazu zobrazte seznam imagí, které jsou nainstalované.

> [!NOTE]
> Soubory bitových kopií může být velký. Obvykle by odeberte dočasné kontejnery, které jste vytvořili při testování a vývoj vaší aplikace. Obvykle byste mít základní Image s modulem runtime nainstalovat, pokud máte v úmyslu na vytváření další Image podle tohoto modulu runtime.

## <a name="next-steps"></a>Další postup

* [Projděte si kurz ASP.NET Core Mikroslužeb.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Projděte si služby Azure, které podporují kontejnery.](https://azure.microsoft.com/overview/containers/)
* [Přečtěte si informace o příkazů souboru Docker.](https://docs.docker.com/engine/reference/builder/)
* [Prozkoumejte nástroje kontejneru sady Visual Studio](/visualstudio/containers/overview)
