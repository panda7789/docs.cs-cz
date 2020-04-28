---
title: Kontejnerizace aplikace s využitím kurzu Docker
description: V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200025"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Kurz: kontejnerizace aplikace .NET Core

V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker. Kontejnery mají mnoho funkcí a výhod, jako je například neproměnlivá infrastruktura, poskytuje přenosnou architekturu a povoluje škálovatelnost. Image se dá použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.

V tomto kurzu jste:

> [!div class="checklist"]
>
> - Vytvoření a publikování jednoduché aplikace .NET Core
> - Vytvoření a konfigurace souboru Dockerfile pro .NET Core
> - Sestavení image Dockeru
> - Vytvoření a spuštění kontejneru Docker

Porozumíte sestavení kontejneru Docker a nasazování úloh pro aplikaci .NET Core. *Platforma Docker* používá *modul Docker* k rychlému sestavování a zabalení aplikací jako *imagí Docker*. Tyto image jsou napsané ve formátu *souboru Dockerfile* , aby je bylo možné nasadit a spustit v vrstveném kontejneru.

> [!NOTE]
> Tento kurz **není** pro aplikace ASP.NET Core. Pokud používáte ASP.NET Core, přečtěte si kurz týkající se [kontejnerizace ASP.NET Core aplikace](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>Požadavky

Nainstalujte následující požadavky:

- [Sada .NET Core 3,1 SDK](https://dotnet.microsoft.com/download)\
Pokud máte nainstalované rozhraní .NET Core, pomocí `dotnet --info` příkazu určete, kterou sadu SDK používáte.
- [Docker Community Edition](https://www.docker.com/products/docker-desktop)
- Dočasná pracovní složka pro *souboru Dockerfile* a ukázkovou aplikaci .NET Core. V tomto kurzu použijete jako pracovní složku název *Docker – Work* .

## <a name="create-net-core-app"></a>Vytvoření aplikace v .NET Core

Potřebujete aplikaci .NET Core, kterou bude kontejner Docker spustit. Otevřete terminál, vytvořte pracovní složku, pokud jste to ještě neudělali, a zadejte ji. V pracovní složce spusťte následující příkaz, který vytvoří nový projekt v podadresáři s názvem *App*:

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

Váš strom složek bude vypadat následovně:

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

`dotnet new` Příkaz vytvoří novou složku s názvem *App* a vygeneruje konzolovou aplikaci "Hello World". Změňte adresáře a přejděte do složky *aplikace* z relace terminálu. Aplikaci spustíte `dotnet run` pomocí příkazu. Aplikace se spustí a vytiskne `Hello World!` se pod příkazem:

```dotnetcli
dotnet run
Hello World!
```

Výchozí šablona vytvoří aplikaci, která se tiskne do terminálu a následně se okamžitě ukončí. V tomto kurzu použijete aplikaci, která bude mít neomezenou dobu. V textovém editoru otevřete soubor *program.cs* .

> [!TIP]
> Pokud používáte Visual Studio Code, v předchozí relaci terminálu zadejte následující příkaz:
>
> ```
> code .
> ```
>
> Tím se otevře složka *aplikace* , která obsahuje projekt v Visual Studio Code.

*Program.cs* by měl vypadat jako následující kód jazyka C#:

```csharp
using System;

namespace NetCore.Docker
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
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

Uložte soubor a otestujte program znovu pomocí `dotnet run`. Mějte na paměti, že tato aplikace bude běžet po neomezenou dobu. K zastavení použijte příkaz zrušit <kbd>CTRL + C</kbd> . Následuje příklad výstupu:

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Pokud předáte číslo do příkazového řádku do aplikace, bude se počítat jenom s touto velikostí a pak se ukončí. Zkuste to s `dotnet run -- 5` počtem až pěti.

> [!IMPORTANT]
> Jakékoli parametry po `--` nejsou předány do `dotnet run` příkazu a místo toho jsou předány do aplikace.

## <a name="publish-net-core-app"></a>Publikování aplikace .NET Core

Před přidáním aplikace .NET Core do image Docker je třeba nejdřív publikovat. Nejlepší je nechat kontejner spustit publikovanou verzi aplikace. Pokud chcete aplikaci publikovat, spusťte následující příkaz:

```dotnetcli
dotnet publish -c Release
```

Tento příkaz zkompiluje vaši aplikaci do složky pro *publikování* . Cesta ke složce pro *publikování* z pracovní složky by měla být`.\App\bin\Release\netcoreapp3.1\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

Ve složce *aplikace* Získejte výpis adresáře složky pro publikování, abyste ověřili, že byl vytvořen soubor *Netcore. Docker. dll* .

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

Pomocí `ls` příkazu Získejte výpis adresáře a ověřte, zda byl vytvořen soubor *Netcore. Docker. dll* .

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>Vytvoření souboru Dockerfile

Soubor *souboru Dockerfile* používá `docker build` příkaz k vytvoření image kontejneru. Tento soubor je textový soubor s názvem *souboru Dockerfile* , který nemá příponu.

Vytvořte soubor s názvem *souboru Dockerfile* v adresáři obsahujícím *. csproj* a otevřete ho v textovém editoru. Tento kurz použije bitovou kopii ASP.NET Core Runtime (která obsahuje bitovou kopii .NET Core Runtime) a odpovídá konzolové aplikaci .NET Core.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> Bitová kopie ASP.NET Core Runtime se tady používá záměrně, i když `mcr.microsoft.com/dotnet/core/runtime:3.1` se image mohla použít.

`FROM` Klíčové slovo vyžaduje plně kvalifikovaný název Image kontejneru Docker. Microsoft Container Registry (MCR, mcr.microsoft.com) je syndikátní služby Docker Hub, která hostuje veřejně přístupné kontejnery. `dotnet/core` Segment je úložiště kontejneru, kde jako `aspnet` segment je název Image kontejneru. Obrázek je označený jako `3.1`, který se používá pro správu verzí. Proto `mcr.microsoft.com/dotnet/core/aspnet:3.1` je modul runtime .net Core 3,1. Ujistěte se, že si vyžádáte verzi modulu runtime, která odpovídá modulu runtime, který cílí na vaši sadu SDK. Například aplikace vytvořená v předchozím oddílu používala sadu .NET Core 3,1 SDK a základní image, na kterou odkazuje *souboru Dockerfile* , jsou označené **3,1**.

Uložte soubor *souboru Dockerfile* . Adresářová struktura pracovní složky by měla vypadat takto. Některé soubory hlubší úrovně a složky byly vynechány, aby bylo možné ušetřit místo v tomto článku:

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

Z terminálu spusťte následující příkaz:

```Docker
docker build -t counter-image -f Dockerfile .
```

Docker zpracuje každý řádek v *souboru Dockerfile*. `.` V `docker build` příkazu dá Docker pokyn k použití aktuální složky k vyhledání *souboru Dockerfile*. Tento příkaz sestaví image a vytvoří místní úložiště s názvem **Counter-image** , která odkazuje na tuto image. Po dokončení tohoto příkazu spusťte `docker images` příkaz a zobrazí se seznam nainstalovaných imagí:

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Všimněte si, že tyto dva obrázky sdílejí stejnou hodnotu **ID obrázku** . Tato hodnota je stejná mezi oběma obrazci, protože jediný příkaz v *souboru Dockerfile* byl založen na novém obrázku na stávající imagi. Pojďme do *souboru Dockerfile*přidat tři příkazy. Každý příkaz vytvoří novou vrstvu obrázku s posledním příkazem, který představuje vstupní body úložiště **počítadla a obrázku** .

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

`COPY` Příkaz vyzve Docker ke zkopírování zadané složky ve vašem počítači do složky v kontejneru. V tomto příkladu je složka pro *publikování* zkopírována do složky s názvem *App* v kontejneru.

`WORKDIR` Příkaz změní **aktuální adresář** uvnitř kontejneru do *aplikace*.

Následující příkaz `ENTRYPOINT`instruuje Docker ke konfiguraci kontejneru tak, aby běžel jako spustitelný soubor. Po spuštění kontejneru se `ENTRYPOINT` příkaz spustí. Po ukončení tohoto příkazu se kontejner automaticky zastaví.

V terminálu spusťte `docker build -t counter-image -f Dockerfile .` příkaz a po jeho dokončení spusťte `docker images`příkaz.

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořila **ID obrázku**. Konečné **ID image** (bude se lišit) bude **cd11c3df9b19** a dál vytvoříte kontejner na základě tohoto obrázku.

## <a name="create-a-container"></a>Vytvoření kontejneru

Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner. Kontejner můžete vytvořit dvěma způsoby. Nejdřív vytvořte nový kontejner, který se zastaví.

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

Výše `docker create` uvedený příkaz vytvoří kontejner založený na obrázku **čítače-obrázek** . Výstup tohoto příkazu ukazuje **ID kontejneru** (bude se lišit) vytvořeného kontejneru. Chcete-li zobrazit seznam *všech* kontejnerů, použijte `docker ps -a` příkaz:

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>Správa kontejneru

Kontejner byl vytvořen s konkrétním názvem `core-counter`, tento název se používá ke správě kontejneru. Následující příklad používá `docker start` příkaz ke spuštění kontejneru a poté používá `docker ps` příkaz k zobrazení pouze kontejnerů, které jsou spuštěny:

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

Podobně `docker stop` příkaz zastaví kontejner. Následující příklad používá `docker stop` příkaz k zastavení kontejneru a poté používá `docker ps` příkaz k zobrazení, že žádné kontejnery nejsou spuštěny:

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>Připojit ke kontejneru

Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup. Použijte příkazy `docker start` a `docker attach` ke spuštění kontejneru a k prohlížení výstupního datového proudu. V tomto příkladu se k odpojení od běžícího kontejneru používá <kbd>Klávesová zkratka CTRL + C</kbd> . Tato klávesová zkratka ukončí proces v kontejneru, pokud není uvedeno jinak, což by zastavilo kontejner. `--sig-proxy=false` Parametr zajistí, že <kbd>CTRL + C</kbd> nebude proces v kontejneru zastavit.

Po odpojení od kontejneru znovu připojte, abyste ověřili, že pořád běží a počítá se.

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Odstranění kontejneru

Pro účely tohoto článku nechcete, aby kontejnery právě neprováděly žádné akce. Odstraňte kontejner, který jste dříve vytvořili. Pokud je kontejner spuštěný, zastavte ho.

```Docker
docker stop core-counter
```

Následující příklad zobrazí seznam všech kontejnerů. Pak pomocí příkazu tento `docker rm` kontejner odstraní a pak u všech spuštěných kontejnerů zkontroluje druhou dobu.

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>Jeden běh

Docker poskytuje `docker run` příkaz pro vytvoření a spuštění kontejneru jako jediného příkazu. Tento příkaz eliminuje nutnost spuštění `docker create` a pak. `docker start` Tento příkaz lze také nastavit tak, aby při zastavení kontejneru automaticky odstranil kontejner. Například použijte `docker run -it --rm` k provedení dvou věcí, nejdřív, automatické použití aktuálního terminálu k připojení ke kontejneru a po dokončení kontejneru ho odeberte:

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Kontejner také předává parametry do provádění aplikace .NET Core. K tomu, aby aplikace .NET Core mohla počítat jenom 3 průchody 3.

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

V `docker run -it`systému, příkaz <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, který zase zastaví kontejner. Vzhledem k `--rm` tomu, že byl zadán parametr, kontejner je automaticky odstraněn při zastavení procesu. Ověřte, že neexistuje:

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>Změnit vstupní bod

`docker run` Příkaz také umožňuje upravit `ENTRYPOINT` příkaz z *souboru Dockerfile* a spustit něco jiného, ale pouze pro tento kontejner. Například použijte následující příkaz ke spuštění `bash` nebo. `cmd.exe` V případě potřeby upravte příkaz.

#### <a name="windows"></a>[Windows](#tab/windows)

V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`. Stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončíte proces a zastavíte kontejner.

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

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

#### <a name="linux"></a>[Linux](#tab/linux)

V tomto příkladu `ENTRYPOINT` se změní na `bash`. `exit` Příkaz se spustí, který ukončí proces a zastaví kontejner.

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>Důležité příkazy

Docker má mnoho různých příkazů, které umožňují vytvářet, spravovat a pracovat s kontejnery a obrázky. Tyto příkazy Docker jsou zásadní pro správu vašich kontejnerů:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [spuštění Docker](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [zastavení Docker](https://docs.docker.com/engine/reference/commandline/stop/)
- [Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
- [Docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
- [Obrázek Docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Během tohoto kurzu jste vytvořili kontejnery a image. Pokud chcete, tyto prostředky odstraňte. Následující příkazy použijte k

01. Vypsat všechny kontejnery

    ```Docker
    docker ps -a
    ```

02. Zastavte kontejnery, které jsou spuštěné podle jejich názvu.

    ```Docker
    docker stop counter-image
    ```

03. Odstranění kontejneru

    ```Docker
    docker rm counter-image
    ```

Pak na počítači odstraňte všechny image, které už nechcete. Odstraňte image vytvořenou *souboru Dockerfile* a pak odstraňte image .NET Core, na které byl *souboru Dockerfile* založen. Můžete použít **ID obrázku** nebo **úložiště:** řetězec ve formátu značek.

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Pomocí `docker images` příkazu zobrazte seznam nainstalovaných imagí.

> [!TIP]
> Soubory obrázků můžou být velké. Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji vaší aplikace. Při plánování vytváření dalších imagí na základě tohoto modulu runtime obvykle zachováte základní image s nainstalovaným modulem runtime.

## <a name="next-steps"></a>Další kroky

- [Naučte se, jak kontejnerizace aplikaci ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Vyzkoušejte si kurz ASP.NET Core mikroslužeb.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Projděte si služby Azure, které podporují kontejnery.](https://azure.microsoft.com/overview/containers/)
- [Přečtěte si o příkazech souboru Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Prozkoumejte nástroje kontejnerů pro Visual Studio](/visualstudio/containers/overview)
