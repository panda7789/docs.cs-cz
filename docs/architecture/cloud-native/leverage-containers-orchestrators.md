---
title: Využití kontejnerů a orchestrátorů
description: Využití kontejnerů Docker a orchestrace Kubernetes v Azure
ms.date: 04/13/2020
ms.openlocfilehash: 64c6c0666398d9ccbc87efad18017bf278568fc4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895554"
---
# <a name="leveraging-containers-and-orchestrators"></a>Využití kontejnerů a orchestrátorů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontejnery a orchestrace jsou navržené tak, aby se vyřešily běžné problémy monolitické nasazení.

## <a name="challenges-with-monolithic-deployments"></a>Problémy s nasazeními monolitické

Většina aplikací je tradičně nasazená jako jediná jednotka. Takové aplikace jsou označovány jako monolitu. Tento obecný přístup k nasazení aplikací jako samostatných jednotek i v případě, že se skládají z několika modulů nebo sestavení, se označuje jako monolitické architektura, jak je znázorněno na obrázku 3-1.

![Architektura monolitické](./media/monolithic-architecture.png)

**Obrázek 3-1**. Architektura monolitické

I když mají výhodu jednoduchosti, monolitické architektury čelí několika problémům:

### <a name="deployment"></a>Nasazení

Aplikace monolitické vyžadují úplné nasazení celé aplikace, a to i v případě, že byla provedena pouze malá změna. Plná nasazení můžou být náročná a náchylná k chybám. Kromě toho vyžadují restart aplikace, který dočasně ovlivňuje nedostupnost.

### <a name="scaling"></a>Škálování

Aplikace monolitické je hostována výhradně na jedné instanci počítače, která často vyžaduje hardware s vysokou schopností. Pokud některá z částí monolitu vyžaduje škálování, je nutné nasadit jinou kopii celé aplikace na jiný počítač. S monolitu nemůžete škálovat součásti aplikace jednotlivě – je to vše nebo nic. Škálování komponent, které nevyžadují škálování, má za následek neefektivní a nákladné využití prostředků.

### <a name="environment"></a>Prostředí

Aplikace monolitické jsou obvykle nasazeny do hostitelského prostředí s předem instalovaným operačním systémem, modulem runtime a závislostmi knihoven. Toto prostředí se nemusí shodovat s tím, na kterém byla aplikace vyvíjena nebo testována. Nekonzistence v různých prostředích aplikací představují společný zdroj problémů pro nasazení monolitické.

### <a name="coupling"></a>Potrubí

Aplikace monolitické se může setkat s vysokým propojením napříč jeho funkčními součástmi. Bez tvrdých hranic jsou systémové změny často výsledkem nezamýšleného a nákladného vedlejšího efektu. Nové funkce nebo opravy se stávají podniknout, časově náročné a náročné na implementaci. Aktualizace vyžadují rozsáhlé testování. Spojení také znemožňuje refaktorování součástí nebo jejich prohození v alternativních implementacích. I v případě, že je vybudováno přísné oddělení obav, se v rámci architektury architektury architektury nastaví v systému jako základ kódu monolitické, který se nikdy neukončí "speciálními případy".

### <a name="platform-lock-in"></a>Zámek platformy

Aplikace monolitické je vytvořená s jedním technologickým zásobníkem. I když je nabídka jednotná, může se tento závazek stát překážkou inovace. Nové funkce a komponenty budou sestaveny pomocí aktuálního zásobníku aplikace – i když lepší volba může být vhodnější pro moderní technologie. Dlouhodobé riziko je, že vaše technologie se přestává zastaralá a zastaralá. V rámci architektury celé aplikace na novou, moderní platformu je nejlepší nákladná a riziková.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jaké jsou výhody kontejnerů a orchestrací?

V kapitole 1 jsme zavedli kontejnery. Zdůraznili jsme, jak CNCF (Cloud Native Computing Foundation) řadí kontejner jako první krok v rámci svých [cloudových nativních map](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) – doprovodné materiály pro podniky, které začínají svoji nativní cloudovou cestu. V této části se podíváme na výhody kontejnerů.

Docker je nejoblíbenější platforma pro správu kontejnerů. Pracuje s kontejnery v systému Linux nebo Windows. Kontejnery poskytují samostatné, ale reprodukovatelná aplikační prostředí, která se spouštějí stejným způsobem na jakémkoli systému. Díky tomuto aspektu jsou ideální pro vývoj a hostování cloudových nativních služeb. Kontejnery jsou od sebe izolované. Dva kontejnery na stejném hostitelském hardwaru můžou mít různé verze softwaru, aniž by to způsobilo konflikty.

Kontejnery jsou definovány jednoduchými textovými soubory, které se stanou artefakty projektu a jsou zkontrolovány do správy zdrojového kódu. I když úplné servery a virtuální počítače vyžadují ruční aktualizaci, kontejnery jsou snadno řízené správou verzí. Aplikace sestavené pro běh v kontejnerech se dají vyvíjet, testovat a nasazovat pomocí automatizovaných nástrojů jako součást kanálu sestavení.

Kontejnery jsou neměnné. Po definování kontejneru ho můžete znovu vytvořit a spustit přesně stejným způsobem. Tato neměnnosti se zapůjčuje do návrhu založeného na komponentách. Pokud se některé části aplikace rozvíjejí jinak než jiné, proč je možné znovu nasadit celou aplikaci, když můžete jenom nasadit části, které se mění nejčastěji? Různé funkce a průřezové aspekty aplikace je možné rozdělit na samostatné jednotky. Obrázek 3-2 ukazuje, jak může aplikace monolitické využít výhod kontejnerů a mikroslužeb pomocí delegování určitých funkcí nebo funkcí. Zbývající funkce samotné aplikace také byly kontejnery.

Kontejnery jsou neměnné. Po definování kontejneru ho můžete znovu vytvořit a spustit přesně stejným způsobem. Tato neměnnosti se zapůjčuje do návrhu založeného na komponentách. Pokud se některé části aplikace rozvíjejí jinak než jiné, proč je možné znovu nasadit celou aplikaci, když můžete jenom nasadit části, které se mění nejčastěji? Různé funkce a průřezové aspekty aplikace je možné rozdělit na samostatné jednotky. Obrázek 3-2 ukazuje, jak může aplikace monolitické využít výhod kontejnerů a mikroslužeb pomocí delegování určitých funkcí nebo funkcí. Zbývající funkce samotné aplikace také byly kontejnery.

![Rozdělení aplikace monolitické pro použití mikroslužeb v back-endu. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Obrázek 3-2**. Rozdělení aplikace monolitické pro použití mikroslužeb v back-endu.

Každá nativní cloudová služba je sestavená a nasazená v samostatném kontejneru. Každý se může podle potřeby aktualizovat. Jednotlivé služby můžou být hostované na uzlech s prostředky, které jsou vhodné pro každou službu. Prostředí, ve kterém každá služba běží, je neměnné, sdílí se s vývojem, testovacím a produkčním prostředím a snadnou verzí. Propojení mezi různými oblastmi aplikace probíhá explicitně jako volání nebo zprávy mezi službami, nikoli závislosti na kompilaci v rámci monolitu. Můžete také zvolit technologii, která nejlépe nastaví danou schopnost, aniž byste museli měnit zbytek aplikace.

Kontejnerové služby vyžadují automatizovanou správu. Nebylo by možné ručně spravovat velkou sadu nezávisle nasazených kontejnerů. Zvažte například následující úlohy:

- Jak budou instance kontejnerů zajištěny v rámci clusteru mnoha počítačů?
- Jak bude po nasazení, jak budou kontejnery zjišťovat a komunikovat mezi sebou?
- Jak se můžou kontejnery škálovat na vyžádání?
- Jak monitorovat stav každého kontejneru?
- Jak chránit kontejner proti selhání hardwaru a softwaru?
- Jak provedete upgrade kontejnerů pro živou aplikaci s nulovými výpadky?

Orchestrace kontejnerů řeší a automatizují tyto a další obavy.

V rámci nativního ekosystému cloudu se Kubernetes stává nástrojem Orchestrator. Je to open source platforma spravovaná platformou Cloud Native Computing (CNCF). Kubernetes automatizuje nasazení, škálování a provozní obavy z kontejnerových úloh v clusteru počítače. Instalace a Správa Kubernetes je ale obvykle odlaďuje složitá.

Mnohem lepším řešením je využití Kubernetes jako spravované služby od dodavatele cloudu. Cloud Azure nabízí plně spravovanou platformu Kubernetes s názvem [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). AKS vyabstrakce složitost a provozní režii správy Kubernetes. Kubernetes spotřebováváte jako cloudovou službu. Společnost Microsoft má odpovědnost za správu a podporu. AKS se také úzce integruje s dalšími službami Azure a nástroji pro vývoj.

AKS je technologie založená na clusteru. Fond federovaných virtuálních počítačů nebo uzlů je nasazený do cloudu Azure. Dohromady tvoří vysoce dostupné prostředí nebo cluster. Cluster se jeví jako bezproblémová a jediná entita do vaší cloudové nativní aplikace. V digestoři AKS nasadí vaše kontejnerové služby v těchto uzlech podle předdefinované strategie, která rovnoměrně distribuuje zatížení.

Kontejnerové služby vyžadují automatizovanou správu. Nebylo by možné ručně spravovat velkou sadu nezávisle nasazených kontejnerů. Zvažte například následující úlohy:

- Jak budou instance kontejnerů zajištěny v rámci clusteru mnoha počítačů?
- Jak bude po nasazení, jak budou kontejnery zjišťovat a komunikovat mezi sebou?
- Jak se můžou kontejnery škálovat na vyžádání?
- Jak monitorovat stav každého kontejneru?
- Jak chránit kontejner proti selhání hardwaru a softwaru?
- Jak provedete upgrade kontejnerů pro živou aplikaci s nulovými výpadky?

Orchestrace kontejnerů řeší a automatizují tyto a další obavy.

V rámci nativního ekosystému cloudu se Kubernetes stává nástrojem Orchestrator. Je to open source platforma spravovaná platformou Cloud Native Computing (CNCF). Kubernetes automatizuje nasazení, škálování a provozní obavy z kontejnerových úloh v clusteru počítače. Instalace a Správa Kubernetes je ale obvykle odlaďuje složitá.

Mnohem lepším řešením je využití Kubernetes jako spravované služby od dodavatele cloudu. Cloud Azure nabízí plně spravovanou platformu Kubernetes s názvem [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). AKS vyabstrakce složitost a provozní režii správy Kubernetes. Kubernetes spotřebováváte jako cloudovou službu. Společnost Microsoft má odpovědnost za správu a podporu. AKS se také úzce integruje s dalšími službami Azure a nástroji pro vývoj.

AKS je technologie založená na clusteru. Fond federovaných virtuálních počítačů nebo uzlů je nasazený do cloudu Azure. Dohromady tvoří vysoce dostupné prostředí nebo cluster. Cluster se jeví jako bezproblémová a jediná entita do vaší cloudové nativní aplikace. V digestoři AKS nasadí vaše kontejnerové služby v těchto uzlech podle předdefinované strategie, která rovnoměrně distribuuje zatížení.

## <a name="what-are-the-scaling-benefits"></a>Jaké jsou výhody škálování?

Služby postavené na kontejnerech můžou využívat výhody škálování poskytované nástroji pro orchestraci, jako je Kubernetes. Kontejnery návrhu se týkají pouze samotných. Jakmile budete mít více kontejnerů, které potřebují spolupracovat, měli byste je uspořádat na vyšší úrovni. Uspořádání velkého počtu kontejnerů a jejich sdílených závislostí, jako je například konfigurace sítě, je místo, kde nástroje pro orchestraci docházejí, aby ušetřily den. Kubernetes vytvoří vrstvu abstrakce přes skupiny kontejnerů a uspořádá je do *lusků*. Lusky se spouštějí na pracovních počítačích, které jsou označovány jako *uzly*. Tato uspořádaná struktura se označuje jako *cluster*. Obrázek 3-3 ukazuje různé komponenty clusteru Kubernetes.

![Součásti clusteru Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Obrázek 3-3**. Součásti clusteru Kubernetes.

Škálování kontejnerových úloh je klíčovou funkcí orchestrace kontejnerů. AKS podporuje automatické škálování ve dvou dimenzích: instance kontejnerů a výpočetní uzly. Společně poskytují AKS schopnost rychle a efektivně reagovat na špičky v poptávce a přidávat další prostředky. V této části probereme škálování v AKS dále.

### <a name="declarative-versus-imperative"></a>Deklarativní versus imperativní

Kubernetes podporuje deklarativní i imperativní konfiguraci. Nepodmíněný přístup zahrnuje spuštění různých příkazů, které oznamují Kubernetes, co dělat v každém kroku jak. Spusťte tuto bitovou kopii. Odstraňte tento pod. Zveřejněte tento port. Pomocí deklarativního přístupu vytvoříte konfigurační soubor nazvaný manifest, který popíšete, co chcete, a místo toho, co chcete udělat. Kubernetes přečte manifest a transformuje požadovaný koncový stav do skutečného koncového stavu.

Imperativní příkazy jsou skvělé pro výukové a interaktivní experimenty. Nicméně budete chtít deklarativně vytvořit soubory manifestu Kubernetes, které budou využívat infrastrukturu jako přístup kódu, a zajistit tak spolehlivá a opakující se nasazení. Soubor manifestu se stal artefaktem projektu a používá se v kanálu CI/CD pro automatizaci nasazení Kubernetes.

Pokud jste cluster již nakonfigurovali pomocí imperativních příkazů, můžete exportovat deklarativní manifest pomocí `kubectl get svc SERVICENAME -o yaml > service.yaml`. Tento příkaz vytvoří manifest podobný jednomu, který vidíte níže:

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

Při použití deklarativní konfigurace můžete zobrazit náhled změn, které budou provedeny před jejich potvrzením, pomocí `kubectl diff -f FOLDERNAME` složky ve složce, ve které jsou umístěny konfigurační soubory. Až si opravdu chcete změny použít, spusťte příkaz `kubectl apply -f FOLDERNAME`. Přidejte `-R` k rekurzivnímu zpracování hierarchie složek.

Můžete také použít deklarativní konfiguraci s jinými Kubernetes funkcemi, z nichž jeden je nasazování. Deklarativní nasazení vám pomůžou spravovat verze, aktualizace a škálování. Kontroler nasazení Kubernetes řídí, jak nasadit nové změny, škálovat zatížení nebo vrátit zpět k předchozí revizi. Pokud je cluster nestabilní, bude deklarativní nasazení automaticky vracet cluster zpět do požadovaného stavu. Například pokud by došlo k selhání uzlu, mechanismus nasazení znovu nasadí náhradu, aby dosáhli požadovaného stavu.

Použití deklarativní konfigurace umožňuje, aby infrastruktura byla reprezentovaná jako kód, který se dá vrátit se změnami, a zároveň používat verzi společně s kódem aplikace. Poskytuje vylepšené řízení změn a lepší podporu pro průběžné nasazování pomocí kanálu sestavení a nasazení.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jaké scénáře jsou ideální pro kontejnery a orchestraci?

Následující scénáře jsou ideální pro používání kontejnerů a orchestrací.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikace vyžadující vysokou dobu provozu a škálovatelnost

Jednotlivé aplikace, které mají vysoké požadavky na provozuschopnost a škálovatelnost, jsou ideálními kandidáty pro nativní cloudové architektury pomocí mikroslužeb, kontejnerů a orchestrací. Je možné je vyvíjet v kontejnerech, testovat napříč různými verzemi prostředí a nasazovat do provozu s nulovými výpadky. Použití clusterů Kubernetes zajišťuje, aby takové aplikace mohly také škálovat na vyžádání a automaticky obnovovat při selhání uzlu.

### <a name="large-numbers-of-applications"></a>Velký počet aplikací

Organizace, které nasazují a udržují velký počet aplikací, využívají z kontejnerů a orchestrací. V rámci nastavení kontejnerových prostředí a clusterů Kubernetes jsou primárně pevné náklady. Nasazení, údržba a aktualizace jednotlivých aplikací má náklady, které se liší podle počtu aplikací. Mimo malý počet aplikací je složitá složitost údržby vlastních aplikací ručním překračovat náklady na implementaci řešení s využitím kontejnerů a orchestrací.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kdy byste se měli vyhnout použití kontejnerů a orchestrací?

Pokud nemůžete sestavit aplikaci za použití zásad dvanácti, měli byste zvážit vyloučení kontejnerů a orchestrací. V těchto případech zvažte hostující platformu založenou na virtuálním počítači, nebo případně nějaký hybridní systém. Díky tomu můžete určité části funkcí vypnout na samostatné kontejnery nebo i na funkce bez serveru.

## <a name="development-resources"></a>Prostředky pro vývoj

V této části se zobrazuje krátký seznam vývojářských prostředků, které vám můžou pomoci začít s používáním kontejnerů a orchestrací pro vaši další aplikaci. Pokud hledáte pokyny k návrhu aplikace architektury mikroslužeb nativního pro Cloud, přečtěte si tohoto doprovodného pomocníka [.NET mikroslužby: architektura pro kontejnery aplikací .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

### <a name="local-kubernetes-development"></a>Vývoj místních Kubernetes

Kubernetes nasazení poskytují skvělou hodnotu v produkčním prostředí, ale můžou běžet i místně na svém vývojovém počítači. I když můžete jednotlivé mikroslužby pracovat nezávisle, může nastat situace, kdy budete muset spustit celý systém místně – stejně jako při nasazení do produkčního prostředí. K dispozici je několik nástrojů, které vám pomůžou: Minikube a Docker Desktop. Visual Studio také poskytuje nástroje pro vývoj v Docker.

### <a name="minikube"></a>Minikube

Co je Minikube? Projekt Minikube říká "Minikube implementuje místní Kubernetes cluster na macOS, Linux a Windows." Jeho primárními cíli je "nejlepší nástroj pro vývoj místních aplikací Kubernetes a podpora všech Kubernetes funkcí, které odpovídají." Instalace Minikube je oddělená od Docker, ale Minikube podporuje jiné hypervisory než Docker Desktop podporuje. Minikube aktuálně podporuje následující funkce Kubernetes:

- DNS
- NodePorts
- ConfigMaps a tajné klíče
- Řídicí panely
- Moduly runtime kontejnerů: Docker, RKT, CRI-O a kontejnery
- Povolení síťového rozhraní kontejneru (CNI)
- Příchozí přenos dat

Po instalaci Minikube je můžete rychle začít používat spuštěním `minikube start` příkazu, který stáhne image a spustí místní cluster Kubernetes. Po spuštění clusteru s ním budete pracovat pomocí standardních příkazů Kubernetes `kubectl` .

### <a name="docker-desktop"></a>Docker Desktop

S Kubernetes můžete také pracovat přímo z Docker desktopu ve Windows. Tato možnost je jediná, pokud používáte kontejnery Windows a je skvělou volbou pro kontejnery jiné než Windows. Obrázek 3-4 ukazuje, jak povolit místní podporu Kubernetes při spuštění Docker desktopu.

![Konfigurace Kubernetes v Docker desktopu](./media/docker-desktop-kubernetes.png)

**Obrázek 3-4**. Konfigurace Kubernetes v Docker desktopu.

Docker Desktop je nejoblíbenějším nástrojem pro místní konfiguraci a spouštění kontejnerových aplikací. Při práci s Docker desktopem se můžete místně vyvíjet na základě stejné sady imagí kontejnerů Docker, které nasadíte do produkčního prostředí. Docker Desktop je navržený tak, aby vytvořil, otestoval a dodal aplikace s podporou kontejnerů v místním prostředí. Podporuje kontejnery pro Linux i Windows. Po nahrání imagí do registru imagí, jako je Azure Container Registry nebo Docker Hub, může AKS vyžádat a nasadit je do produkčního prostředí.

### <a name="visual-studio-docker-tooling"></a>Nástroje Docker sady Visual Studio

Visual Studio podporuje vývoj Docker pro webové aplikace. Když vytváříte novou ASP.NET Core aplikaci, máte možnost ji nakonfigurovat s podporou Docker, jak je znázorněno na obrázku 3-5.

![Povolit podporu Docker pro Visual Studio](./media/visual-studio-enable-docker-support.png)

**Obrázek 3-5**. Povolit podporu Docker pro Visual Studio

Když je vybraná tato možnost, projekt se vytvoří s a `Dockerfile` v jeho kořenovém adresáři, který se dá použít k sestavení a hostování aplikace v kontejneru Docker. Příklad souboru Dockerfile je znázorněný na obrázku 3 -6. Git.

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

Kromě toho můžete kdykoli přidat podporu Docker do existující aplikace ASP.NET Core. V Průzkumník řešení sady Visual Studio klikněte pravým tlačítkem na projekt a **přidejte** > **podporu Docker**, jak je znázorněno na obrázku 3-8.

**Obrázek 3-8**. Přidání podpory Docker do sady Visual Studio

Můžete také přidat podporu orchestrace kontejnerů, která je také znázorněna na obrázku 3-8. Ve výchozím nastavení nástroj Orchestrator používá Kubernetes a Helm. Po zvolení nástroje Orchestrator se do kořenového adresáře projektu přidá `azds.yaml` soubor a přidá se `charts` složka obsahující Helm grafy používané ke konfiguraci a nasazení aplikace do Kubernetes. Obrázek 3-9 ukazuje výsledné soubory v novém projektu.

Můžete také přidat podporu orchestrace kontejnerů, která je také znázorněna na obrázku 3-8. Ve výchozím nastavení nástroj Orchestrator používá Kubernetes a Helm. Po zvolení nástroje Orchestrator se do kořenového adresáře projektu přidá `azds.yaml` soubor a přidá se `charts` složka obsahující Helm grafy používané ke konfiguraci a nasazení aplikace do Kubernetes. Obrázek 3-9 ukazuje výsledné soubory v novém projektu.

**Obrázek 3-9**. Přidání podpory orchestrace do sady Visual Studio

### <a name="visual-studio-code-docker-tooling"></a>Nástroje Visual Studio Code Docker

K dispozici je několik rozšíření pro Visual Studio Code, která podporují vývoj v Docker.

Microsoft poskytuje [Docker pro rozšíření Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker). Toto rozšíření zjednodušuje proces přidávání podpory kontejneru do aplikací. Tato generátory IT vyžaduje soubory, sestavuje image Docker a umožňuje ladit aplikaci v rámci kontejneru. Rozšíření nabízí vizuální Průzkumníka, který usnadňuje provedení akcí na kontejnerech a obrázcích, jako je například spuštění, zastavení, kontrola, odebrání a další. Rozšíření také podporuje Docker Compose, které vám umožní spravovat více spuštěných kontejnerů jako jednu jednotku.

>[!div class="step-by-step"]
>[Předchozí](scale-applications.md)
>[Další](leverage-serverless-functions.md)
