---
title: Využití kontejnerů a orchestrátorů
description: Využití kontejnerů Docker a orchestrace Kubernetes v Azure
ms.date: 06/30/2019
ms.openlocfilehash: 7b136ed2760ea471f42ff82d20298ff8714c6dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087233"
---
# <a name="leveraging-containers-and-orchestrators"></a>Využití kontejnerů a orchestrátorů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontejnery a orchestrace jsou navržené tak, aby se vyřešily běžné problémy monolitické nasazení.

## <a name="challenges-with-monolithic-deployments"></a>Problémy s nasazeními monolitické

Většina aplikací je tradičně nasazená jako jediná jednotka. Takové aplikace jsou označovány jako monolitu. Tento obecný přístup k nasazení aplikací jako samostatných jednotek i v případě, že se skládají z několika modulů nebo sestavení, se označuje jako monolitické architektura, jak je znázorněno na obrázku 3-1.

![Architektura monolitické](./media/monolithic-architecture.png)

**Obrázek 3-1**. Architektura monolitické

I když mají výhodu jednoduchosti, monolitické architektury čelí několika problémům:

### <a name="deployments"></a>Nasazení

Nasazení do aplikací monolitické obvykle vyžaduje restartování celé aplikace, i když se nahrazuje jenom jeden malý modul. V závislosti na počtu počítačů, které hostují aplikaci, to může způsobit výpadky během nasazení.

### <a name="hosting"></a>Hosting

Aplikace monolitické se hostují výhradně na jedné instanci počítače. To může vyžadovat hardware s vyššími schopnostmi, než bude potřeba kterýkoli modul v distribuované aplikaci. Také pokud se některá z částí aplikace stal kritickým bodem, musí být celá aplikace nasazena do dalších uzlů počítače, aby bylo možné horizontální navýšení kapacity.

### <a name="environment"></a>Prostředí

Aplikace monolitické jsou obvykle nasazeny do existujícího hostitelského prostředí (operační systém, nainstalovaná rozhraní atd.). Toto prostředí nemusí odpovídat prostředí, ve kterém se aplikace vyvinula nebo otestovala. Nekonzistence v prostředí aplikace představují společný zdroj problémů pro nasazení monolitické.

### <a name="coupling"></a>Potrubí

Aplikace monolitické pravděpodobně budou mít velkou flexibilitu mezi různými částmi aplikace a mezi aplikací a jejím prostředím. Díky tomu může být obtížné rozložit konkrétní službu nebo se k ní zabývat později, aby se zvýšila její škálovatelnost nebo swap v jiné implementaci. Toto propojení také vede k většímu množství možných dopadů na změny systému, což vyžaduje rozsáhlé testování ve větších aplikacích.

### <a name="technology-choice"></a>Volba technologie

Aplikace monolitické jsou sestavené a nasazené jako jednotka. Tato možnost nabízí jednoduchost a jednotnost, ale může být překážkou pro inovace. I když může být nová funkce nebo modul v systému vhodnější pro pokročilejší platformu nebo architekturu, je pravděpodobné, že bude vytvořen pomocí aktuálního přístupu aplikace v zájmu konzistence a také snadného vývoje a nasazení.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jaké jsou výhody kontejnerů a orchestrací?

Docker je nejoblíbenější platforma pro správu a vytváření imagí kontejnerů a umožňuje rychlou práci s kontejnery v systémech Linux a Windows. Kontejnery poskytují samostatné, ale reprodukovatelná aplikační prostředí, která se spouštějí stejným způsobem na jakémkoli systému. Díky tomu jsou ideální pro vývoj a hostování aplikací a komponent aplikací v cloudových nativních aplikacích. Kontejnery jsou izolované od sebe, takže dva kontejnery na stejném hostiteli můžou mít různé verze softwaru a dokonce i operační systém, a to bez závislostí způsobujících konflikty.

A co více kontejnerů jsou definovány jednoduchými soubory, které lze zkontrolovat do správy zdrojového kódu. Na rozdíl od úplných serverů, dokonce i virtuálních počítačů, které často vyžadují ruční práci na použití aktualizací nebo instalaci dalších služeb, může infrastruktura kontejnerů snadno řídit verzí. Proto aplikace sestavené pro spouštění v kontejnerech je možné vyvíjet, testovat a nasazovat pomocí automatizovaných nástrojů jako součást kanálu sestavení.

Kontejnery jsou neměnné. Jakmile budete mít definici kontejneru, můžete tento kontejner znovu vytvořit a spustí se přesně stejným způsobem. Tato neměnnosti se zapůjčuje do návrhu založeného na komponentách. Pokud se některé části aplikace nemění tak často jako jiné, proč je možné znovu nasadit celou aplikaci, když můžete jenom nasadit části, které se mění nejčastěji? Různé funkce a průřezové aspekty aplikace je možné rozdělit na samostatné jednotky. Obrázek 3-2 ukazuje, jak může aplikace monolitické využít výhod kontejnerů a mikroslužeb pomocí delegování určitých funkcí nebo funkcí. Zbývající funkce samotné aplikace také byly kontejnery.

![rozdělení aplikace monolitické, aby používala mikroslužby v back-endu.](./media/breaking-up-monolith-with-backend-microservices.png)
**obrázek 3-2**. Rozdělení aplikace monolitické pro použití mikroslužeb v back-endu.

Cloudové nativní aplikace sestavené pomocí samostatných kontejnerů využívají výhod nasazení aplikace v případě potřeby co nejvíc nebo i trochu. Jednotlivé služby můžou být hostované na uzlech s prostředky, které jsou vhodné pro každou službu. Prostředí, ve kterém je každá služba spuštěná, je neměnné, dá se sdílet mezi vývojem, testováním a výrobou a dá se snadno používat ve verzi. Propojení mezi různými oblastmi aplikace probíhá explicitně jako volání nebo zprávy mezi službami, nikoli závislosti na kompilaci v rámci monolitu. A libovolná část celkové aplikace může zvolit technologii, která dává smysl pro tuto funkci nebo schopnost, a to bez nutnosti provádět změny ve zbývající části aplikace.

## <a name="what-are-the-scaling-benefits"></a>Jaké jsou výhody škálování?

Služby postavené na kontejnerech můžou využívat výhody škálování poskytované nástroji pro orchestraci, jako je Kubernetes. Kontejnery návrhu se týkají pouze samotných. Jakmile začnete mít více kontejnerů, které potřebují společně spolupracovat, může být vhodné je uspořádat na vyšší úrovni. Uspořádání velkého počtu kontejnerů a jejich sdílených závislostí, jako je například konfigurace sítě, je místo, kde nástroje pro orchestraci docházejí, aby ušetřily den. Kubernetes je platforma pro orchestraci kontejnerů navržená pro automatizaci nasazení, škálování a správy kontejnerových aplikací. Vytvoří vrstvu abstrakce nad skupinami kontejnerů a uspořádá je do *lusků*. Lusky se spouštějí na pracovních počítačích, které jsou označovány jako *uzly*. Celá uspořádaná skupina se označuje jako *cluster*. Obrázek 3-3 ukazuje různé komponenty clusteru Kubernetes.

![součásti clusteru Kubernetes.](./media/kubernetes-cluster-components.png)
**obrázek 3-3**. Součásti clusteru Kubernetes.

Kubernetes má integrovanou podporu pro škálování clusterů tak, aby splňovala požadavky. V kombinaci s dodanými mikroslužbami poskytuje cloudové nativní aplikace s možností rychle a efektivně reagovat na špičky v poptávce s dalšími prostředky, když jsou a tam, kde jsou potřeba.

### <a name="declarative-versus-imperative"></a>Deklarativní versus imperativní

Kubernetes podporuje deklarativní i imperativní konfiguraci objektů. Nepodmíněný přístup zahrnuje spuštění různých příkazů, které oznamují Kubernetes, co dělat v každém kroku jak. *Spusťte* tuto bitovou kopii. *Odstraňte* tento pod. *Zveřejněte* tento port. V případě deklarativního přístupu použijete konfigurační soubor, který popisuje, *co chcete* , místo *abyste mohli dělat* a Kubernetes vyhodnotit, co se má udělat, abyste dosáhli požadovaného koncového stavu. Pokud jste cluster již nakonfigurovali pomocí imperativních příkazů, můžete vyexportovat deklarativní manifest pomocí `kubectl get svc SERVICENAME -o yaml > service.yaml`. Tím se vytvoří soubor manifestu, jako je tento:

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

Při použití deklarativní konfigurace můžete zobrazit náhled změn, které budou provedeny před jejich potvrzením, pomocí `kubectl diff -f FOLDERNAME` ve složce, ve které jsou umístěny konfigurační soubory. Až si opravdu chcete změny použít, spusťte `kubectl apply -f FOLDERNAME`. Přidejte `-R` k rekurzivnímu zpracování hierarchie složek.

Kromě služeb můžete použít deklarativní konfiguraci pro jiné funkce Kubernetes, jako jsou například *nasazení*. Deklarativní nasazení používají řadiče nasazení k aktualizaci prostředků clusteru. Nasazení se používají k zavedení nových změn, horizontálnímu navýšení kapacity pro podporu většího zatížení nebo návrat k předchozí revizi. Pokud je cluster nestabilní, deklarativní nasazení poskytuje mechanismus pro automatické převedení clusteru zpátky do požadovaného stavu.

Použití deklarativní konfigurace umožňuje, aby infrastruktura byla reprezentovaná jako kód, který se dá vrátit se změnami, a zároveň používat verzi společně s kódem aplikace. To poskytuje vylepšené řízení změn a lepší podporu pro průběžné nasazování pomocí sestavení a nasazení kanálu vázaného na změny správy zdrojového kódu.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jaké scénáře jsou ideální pro kontejnery a orchestraci?

Následující scénáře jsou ideální pro používání kontejnerů a orchestrací.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikace vyžadující vysokou dobu provozu a škálovatelnost

Jednotlivé aplikace, které mají vysoké požadavky na provozuschopnost a škálovatelnost, jsou ideálními kandidáty pro nativní cloudové architektury pomocí mikroslužeb, kontejnerů a orchestrací. Tyto aplikace je možné vyvíjet v kontejnerech pomocí prostředí s použitím verzí, které je možné před tím, než budete moct začít používat, a můžou být nasazené do produkčního prostředí s nulovými výpadky. Použití clusterů Kubernetes zajišťuje, aby takové aplikace mohly také škálovat na vyžádání a automaticky obnovovat při selhání uzlu.

### <a name="large-numbers-of-applications"></a>Velký počet aplikací

Organizace, které nasazují a musí následně uchovávat velký počet aplikací, přináší výhody kontejnerů a orchestrací. V rámci nastavení kontejnerových prostředí a clusterů Kubernetes jsou primárně pevné náklady. Nasazení, údržba a aktualizace jednotlivých aplikací má cenu, která se liší v závislosti na počtu aplikací, které musí být zachovány. Nad rámec určitého poměrně malého počtu aplikací je složitá složitost údržby vlastních aplikací ručně a náklady na implementaci řešení s využitím kontejnerů a orchestrací.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kdy byste se měli vyhnout použití kontejnerů a orchestrací?

Pokud nebudete nebo nebudete moct sestavovat aplikaci po dvanácti zásadách aplikace, bude pravděpodobně lepší vycházet z předcházení kontejnerům a orchestraci. V těchto případech může být nejlepší přesunout vpřed s hostující platformou založenou na virtuálním počítači, nebo potenciálně nějaký hybridní systém, ve kterém můžete určité části funkcí vypnout do samostatných kontejnerů nebo i bez serveru.

## <a name="development-resources"></a>Prostředky pro vývoj

V této části se zobrazuje krátký seznam vývojářských prostředků, které vám můžou pomoci začít s používáním kontejnerů a orchestrací pro vaši další aplikaci. Pokud hledáte pokyny k návrhu aplikace architektury mikroslužeb nativního pro Cloud, přečtěte si tohoto doprovodného pomocníka [.NET mikroslužby: architektura pro kontejnery aplikací .NET](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Vývoj místních Kubernetes

Kubernetes nasazení poskytují skvělou hodnotu v produkčním prostředí, ale můžete je také spouštět místně. I když je v podstatě možné pracovat na jednotlivých aplikacích nebo mikroslužbách nezávisle, je možné, že budete mít schopnost spustit celý systém místně stejně jako při nasazení do produkčního prostředí. Existuje několik způsobů, jak toho dosáhnout, z nichž dva jsou Minikube a Docker Desktop. Visual Studio také poskytuje nástroje pro vývoj v Docker.

### <a name="minikube"></a>Minikube

Co je Minikube? Projekt Minikube říká "Minikube implementuje místní Kubernetes cluster na macOS, Linux a Windows." Jeho primárními cíli je "nejlepší nástroj pro vývoj místních aplikací Kubernetes a podpora všech Kubernetes funkcí, které odpovídají." Instalace Minikube je oddělená od Docker, ale Minikube podporuje jiné hypervisory než Docker Desktop podporuje. Minikube aktuálně podporuje následující funkce Kubernetes:

- DNS
- NodePorts
- ConfigMaps a tajné klíče
- Řídicí panely
- Moduly runtime kontejnerů: Docker, RKT, CRI-O a kontejnery
- Povolení síťového rozhraní kontejneru (CNI)
- Příchozí přenos dat

Po instalaci Minikube je můžete rychle začít používat spuštěním příkazu `minikube start`, který stáhne image a spustí místní cluster Kubernetes. Po spuštění clusteru s ním budete pracovat pomocí standardních příkazů Kubernetes `kubectl`.

### <a name="docker-desktop"></a>Docker Desktop

S Kubernetes můžete také pracovat přímo z Docker desktopu ve Windows. Tato možnost je jediná, pokud používáte kontejnery Windows a je skvělou volbou pro kontejnery jiné než Windows. Standardní aplikace Docker Desktop Configuration se používá ke konfiguraci Kubernetes spuštěného z Docker desktopu.

![Konfigurace Kubernetes v Docker desktopu](./media/docker-desktop-kubernetes.png)

**Obrázek 3-4**. Konfigurace Kubernetes v Docker desktopu.

Docker Desktop už je nejoblíbenějším nástrojem pro místní konfiguraci a spouštění kontejnerových aplikací. Při práci s Docker desktopem se můžete místně vyvíjet na základě stejné sady imagí kontejnerů Docker, které nasadíte do produkčního prostředí. Docker Desktop je navržený tak, aby vytvořil, otestoval a dodal aplikace s podporou kontejnerů v místním prostředí. Po odeslání imagí do registru imagí, jako je Azure Container Registry nebo Docker Hub, služby, jako je Azure Kubernetes Service (AKS), spravují aplikaci v produkčním prostředí.

### <a name="visual-studio-docker-tooling"></a>Nástroje Docker sady Visual Studio

Visual Studio podporuje vývoj Docker pro webové aplikace. Když vytvoříte novou ASP.NET Core aplikaci, budete mít možnost ji nakonfigurovat s podporou Docker jako součást procesu vytváření projektu, jak je znázorněno na obrázku 3-5.

![Povolit podporu Docker pro Visual Studio](./media/visual-studio-enable-docker-support.png)

**Obrázek 3-5**. Povolit podporu Docker pro Visual Studio

Když je vybraná tato možnost, projekt se vytvoří s `Dockerfile` v jeho kořenovém adresáři, který se dá použít k sestavení a hostování aplikace v kontejneru Docker. Na obrázku 3-6 se zobrazuje příklad souboru Dockerfile.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**Obrázek 3-6**. Souboru Dockerfile vygenerované v aplikaci Visual Studio

Výchozí chování při spuštění aplikace je nakonfigurováno pro použití Docker. Obrázek 3-7 ukazuje různé možnosti spuštění, které jsou k dispozici z nového projektu ASP.NET Core vytvořeného pomocí přidání podpory Docker.

![Možnosti spuštění aplikace Visual Studio Docker](./media/visual-studio-docker-run-options.png)

**Obrázek 3-7**. Možnosti spuštění aplikace Visual Studio Docker

Kromě místního vývoje [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) poskytuje vývojářům pohodlný způsob, jak v rámci Azure pracovat s vlastními konfiguracemi Kubernetes. Jak vidíte na obrázku 3-7, můžete také spustit aplikaci v Azure Dev Spaces.

Pokud nepřidáte do vaší aplikace ASP.NET Core podporu Docker při jejím vytváření, můžete ji kdykoli přidat později. V Průzkumník řešení sady Visual Studio klikněte pravým tlačítkem myši na projekt a vyberte přidat **podporu > Docker**, jak je znázorněno na obrázku 3-8.

![Přidat podporu Docker pro Visual Studio](./media/visual-studio-add-docker-support.png)

**Obrázek 3-8**. Přidat podporu Docker pro Visual Studio

Kromě podpory Docker můžete také přidat podporu orchestrace kontejnerů, která je také znázorněna na obrázku 3-8. Ve výchozím nastavení nástroj Orchestrator používá Kubernetes a Helm. Po zvolení nástroje Orchestrator se do kořenového adresáře projektu přidá soubor `azds.yaml` a přidá se složka `charts` obsahující grafy Helm, které slouží ke konfiguraci a nasazení aplikace do Kubernetes. Obrázek 3-9 ukazuje výsledné soubory v novém projektu.

![Přidání podpory nástroje Orchestrator pro Visual Studio](./media/visual-studio-add-orchestrator-support.png)

**Obrázek 3-9**. Přidání podpory nástroje Orchestrator pro Visual Studio

## <a name="references"></a>Reference

- [Co je Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalace Kubernetes pomocí Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Předchozí](scale-applications.md)
>[Další](leverage-serverless-functions.md)
