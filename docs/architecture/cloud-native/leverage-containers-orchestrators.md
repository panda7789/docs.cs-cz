---
title: Využití kontejnerů a orchestrátorů
description: Využití kontejnerů Dockeru a orchestrátorů Kubernetes v Azure
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989035"
---
# <a name="leveraging-containers-and-orchestrators"></a>Využití kontejnerů a orchestrátorů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontejnery a orchestratory jsou navrženy tak, aby řešily problémy společné pro monolitické přístupy nasazení.

## <a name="challenges-with-monolithic-deployments"></a>Výzvy s monolitickými nasazeními

Většina aplikací byla tradičně nasazena jako jedna jednotka. Tyto žádosti se označují jako monolit. Tento obecný přístup nasazení aplikací jako jednotlivých jednotek, i když jsou složeny z více modulů nebo sestavení, se označuje jako monolitická architektura, jak je znázorněno na obrázku 3-1.

![Monolitická architektura.](./media/monolithic-architecture.png)

**Obrázek 3-1**. Monolitická architektura.

Ačkoli mají výhodu jednoduchosti, monolitické architektury čelí řadě výzev:

### <a name="deployments"></a>Nasazení

Nasazení do monolitických aplikací obvykle vyžaduje restartování celé aplikace, i když je nahrazen pouze jeden malý modul. V závislosti na počtu počítačů hostujících aplikaci to může mít za následek prostoje během nasazení.

### <a name="hosting"></a>Hostování

Monolitické aplikace jsou hostovány výhradně na jedné instanci počítače. To může vyžadovat vyšší možnosti hardwaru, než jakýkoli modul v distribuované aplikaci by potřeboval. Také pokud se některá část aplikace stane kritickým bodem, celá aplikace musí být nasazena do dalších uzlů počítače, aby bylo možné horizontální navýšení kapacity.

### <a name="environment"></a>Prostředí

Monolitické aplikace se obvykle nasazují do existujícího hostitelského prostředí (operační systém, nainstalované architektury atd.). Toto prostředí nemusí odpovídat prostředí, ve kterém byla aplikace vyvinuta nebo testována. Nekonzistence v prostředí aplikace jsou běžným zdrojem problémů pro monolitické nasazení.

### <a name="coupling"></a>Tažné

Monolitické aplikace budou mít pravděpodobně velké spojení mezi různými částmi aplikace a mezi aplikací a jejím prostředím. To může ztížit pozdější faktor mimo určitou službu nebo obavy, aby se zvýšila její škálovatelnost nebo se vyměnila v alternativní implementaci. Tato spojka také vede k mnohem větším potenciálním dopadům na změny systému, což vyžaduje rozsáhlé testování ve větších aplikacích.

### <a name="technology-choice"></a>Volba technologie

Monolitické aplikace jsou sestaveny a nasazeny jako celek. To nabízí jednoduchost a jednotnost, ale může být překážkou pro inovace. I když nová funkce nebo modul v systému může být vhodnější pro modernější platformu nebo rámec, je pravděpodobné, že bude sestaven pomocí aktuálního přístupu aplikace z důvodu konzistence a snadnost vývoje a nasazení.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jaké jsou výhody kontejnerů a orchestrátorů?

Docker je nejoblíbenější platforma pro správu kontejnerů a zobrazování a umožňuje rychlou práci s kontejnery na Linuxu a Windows. Kontejnery poskytují samostatné, ale reprodukovatelné aplikační prostředí, které běží stejným způsobem v libovolném systému. Díky tomu jsou ideální pro vývoj a hostování aplikací a součástí aplikací v aplikacích nativních pro cloud. Kontejnery jsou od sebe izolovány, takže dva kontejnery na stejném hostitelském hardwaru mohou mít nainstalovány různé verze softwaru a dokonce i operační systém, aniž by došlo ke konfliktům závislostí.

A co víc, kontejnery jsou definovány jednoduchými soubory, které lze zkontrolovat do správy zdrojového kódu. Na rozdíl od úplných serverů, dokonce i virtuálních počítačů, které často vyžadují ruční práci k instalaci aktualizací nebo instalaci dalších služeb, může být kontejnerová infrastruktura snadno řízena verzí. Aplikace vytvořené pro spuštění v kontejnerech tedy mohou být vyvíjeny, testovány a nasazovány pomocí automatizovaných nástrojů jako součást kanálu sestavení.

Kontejnery jsou neměnné. Jakmile budete mít definici kontejneru, můžete znovu vytvořit tento kontejner a bude fungovat přesně stejným způsobem. Tato neměnnost se hodí k návrhu založenému na komponentách. Pokud se některé části aplikace nemění tak často jako jiné, proč znovu nasadit celou aplikaci, když můžete jen nasadit součásti, které se mění nejčastěji? Různé funkce a průřezové obavy aplikace lze rozdělit do samostatných jednotek. Obrázek 3-2 ukazuje, jak monolitické aplikace můžete využít kontejnery a mikroslužeb delegováním určité funkce nebo funkce. Zbývající funkce v samotné aplikaci byla také kontejnerizována.

![Rozdělení monolitické aplikace pro použití mikroslužeb v back-endu. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Obrázek 3-2**. Rozdělení monolitické aplikace pro použití mikroslužeb v back-endu.

Cloudové nativní aplikace vytvořené pomocí samostatných kontejnerů těží ze schopnosti nasadit tolik nebo tak málo aplikace podle potřeby. Jednotlivé služby mohou být hostovány na uzlech s prostředky odpovídajícími každé službě. Prostředí, ve které je každá služba spuštěna, je neměnné, lze je sdílet mezi dev, test em a výrobou a lze je snadno verzi. Párování mezi různými oblastmi aplikace dochází explicitně jako volání nebo zprávy mezi službami, nikoli závislosti v době kompilace v rámci monolitu. A jakákoli v dané části celkové aplikace si můžete vybrat technologii, která dává největší smysl pro tuto funkci nebo schopnost, aniž by bylo nutné změnit zbytek aplikace.

## <a name="what-are-the-scaling-benefits"></a>Jaké jsou výhody škálování?

Služby postavené na kontejnerech můžou využívat výhody škálování poskytované nástroji orchestrace, jako je Kubernetes. Podle návrhu kontejnery vědí jen o sobě. Jakmile začnete mít více kontejnerů, které potřebují spolupracovat, může být vhodné je uspořádat na vyšší úrovni. Uspořádání velkého počtu kontejnerů a jejich sdílených závislostí, jako je například konfigurace sítě, je místo, kde nástroje orchestrace přicházejí k uložení dne! Kubernetes je platforma orchestrace kontejnerů navržená k automatizaci nasazení, škálování a správy kontejnerizovaných aplikací. Vytvoří vrstvu abstrakce nad skupinami kontejnerů a uspořádá je do *podů*. Pody běží na pracovních počítačích označované jako *uzly*. Celá organizovaná skupina se označuje jako *cluster*. Obrázek 3-3 znázorňuje různé součásti clusteru Kubernetes.

![Komponenty clusteru Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Obrázek 3-3**. Komponenty clusteru Kubernetes.

Kubernetes má integrovanou podporu pro škálování clusterů tak, aby splňovaly požadavky. V kombinaci s kontejnerovými mikroslužbami to poskytuje cloudové nativní aplikace s možností rychle a efektivně reagovat na špičky v poptávce s dalšími prostředky, kdy a kde jsou potřeba.

### <a name="declarative-versus-imperative"></a>Deklarativní versus imperativ

Kubernetes podporuje deklarativní i imperativní konfiguraci objektu. Imperativní přístup zahrnuje spuštění různých příkazů, které kubernetes říkají, co má dělat na každém kroku cesty. *Spusťte* tento obrázek. *Odstraňte* tento pod. *Vystavit* tento port. S deklarativní přístup, použijte konfigurační soubor, který *popisuje, co chcete* místo *toho, co dělat* a Kubernetes zjistí, co dělat k dosažení požadovaného koncového stavu. Pokud jste již nakonfigurovali cluster pomocí imperativních `kubectl get svc SERVICENAME -o yaml > service.yaml`příkazů, můžete exportovat deklarativní manifest pomocí aplikace . To bude produkovat soubor manifestu, jako je tento:

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

Při použití deklarativní konfigurace můžete zobrazit náhled změn, `kubectl diff -f FOLDERNAME` které budou provedeny před jejich potvrzením pomocí proti složce, kde jsou umístěny konfigurační soubory. Jakmile si budete jisti, že chcete `kubectl apply -f FOLDERNAME`změny použít, spusťte aplikaci . Přidejte `-R` k rekurzivnímu zpracování hierarchie složek.

Kromě služeb můžete použít deklarativní konfiguraci pro jiné funkce Kubernetes, jako je například *nasazení*. Deklarativní nasazení používají řadiče nasazení k aktualizaci prostředků clusteru. Nasazení se používají k zavedení nových změn, škálování nahoru pro podporu většízatížení nebo vrátit zpět k předchozí revizi. Pokud je cluster nestabilní, deklarativní nasazení poskytují mechanismus pro automatické převedení clusteru zpět do požadovaného stavu.

Použití deklarativní konfigurace umožňuje infrastruktury, které mají být reprezentovány jako kód, který lze se změnami a verzí vedle kódu aplikace. To poskytuje lepší řízení změn a lepší podporu pro průběžné nasazení pomocí kanálu sestavení a nasazení vázané na změny správy zdrojového kódu.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jaké scénáře jsou ideální pro kontejnery a orchestrátory?

Následující scénáře jsou ideální pro použití kontejnerů a orchestrátory.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikace vyžadující vysokou dostupnost a škálovatelnost

Jednotlivé aplikace, které mají požadavky na vysokou dostupnost a škálovatelnost, jsou ideálními kandidáty pro architektury nativní pro cloud pomocí mikroslužeb, kontejnerů a orchestrátorů. Tyto aplikace mohou být vyvinuty v kontejnerech pomocí prostředí s verzí, lze rozsáhle testovat před odchodem do produkčního prostředí a mohou být nasazeny do produkčního prostředí s nulovými prostoji. Použití clusterů Kubernetes zajišťuje, že tyto aplikace mohou také škálovat na vyžádání a automaticky se zotavit z selhání uzlů.

### <a name="large-numbers-of-applications"></a>Velký počet aplikací

Organizace, které nasazují a musí následně udržovat velký počet aplikací těžit z kontejnerů a orchestrátory. Počáteční úsilí při nastavování kontejnerizovaných prostředí a clusterů Kubernetes je především fixní náklady. Nasazení, údržba a aktualizace jednotlivých aplikací má náklady, které se liší podle počtu aplikací, které musí být udržovány. Kromě určitépoměrně malý počet aplikací, složitost údržby vlastních aplikací ručně přesahuje náklady na implementaci řešení pomocí kontejnerů a orchestrátory.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kdy byste se měli vyhnout použití kontejnerů a orchestrátorů?

Pokud nejste ochotni nebo schopni vytvořit aplikaci podle principů twelve-factor app, budete pravděpodobně lépe vyhnout kontejnery a orchestrátory. V těchto případech může být nejlepší pokročit s hostitelskou platformou založenou na virtuálním zařízení nebo případně s nějakým hybridním systémem, ve kterém můžete oddělit určité části funkcí do samostatných kontejnerů nebo dokonce bezserverových funkcí.

## <a name="development-resources"></a>Rozvojové zdroje

Tato část zobrazuje krátký seznam prostředků pro vývoj, které vám mohou pomoci začít používat kontejnery a orchestrátory pro další aplikaci. Pokud hledáte návod, jak navrhnout aplikaci architektury mikroslužeb nativní pro cloud, přečtěte si doprovod této knihy [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Místní vývoj Kubernetes

Nasazení Kubernetes poskytují velkou hodnotu v produkčním prostředí, ale můžete je také spustit místně. I když většinu času je dobré mít možnost pracovat na jednotlivých aplikacích nebo mikroslužeb nezávisle, někdy je dobré mít možnost spustit celý systém místně stejně jako se spustí při nasazení do produkčního prostředí. Existuje několik způsobů, jak toho dosáhnout, z nichž dva jsou Minikube a Docker Desktop. Visual Studio také poskytuje nástroje pro vývoj Dockeru.

### <a name="minikube"></a>Minikube (Minikube)

Co je Minikube? Projekt Minikube říká: "Minikube implementuje místní cluster Kubernetes v systémech macOS, Linux a Windows." Jeho hlavním cílem je "být nejlepším nástrojem pro vývoj místních aplikací Kubernetes a podporovat všechny funkce Kubernetes, které se hodí." Instalace Minikube je oddělená od Dockeru, ale Minikube podporuje různé hypervisory, než podporuje Docker Desktop. Minikube aktuálně podporuje následující funkce Kubernetes:

- DNS
- Porty uzlů
- ConfigMapy a tajné klíče
- Řídicí panely
- Kontejnerové runtimes: Docker, rkt, CRI-O a kontejnery
- Povolení rozhraní kontejnerové sítě (CNI)
- Příchozí přenos dat

Po instalaci Minikube, můžete rychle začít `minikube start` používat spuštěním příkazu, který stáhne obrázek a spustit místní Kubernetes clusteru. Po spuštění clusteru s ním budete pracovat pomocí standardních příkazů Kubernetes. `kubectl`

### <a name="docker-desktop"></a>Desktop Dockeru

Můžete také pracovat s Kubernetes přímo z Docker Desktop v systému Windows. Toto je vaše jediná možnost, pokud používáte kontejnery Windows, a je skvělou volbou i pro kontejnery, které nejsou windows. Standardní konfigurační aplikace Docker Desktop se používá ke konfiguraci Kubernetes spuštěných z Docker Desktop.

![Konfigurace Kubernetes v Docker Desktop](./media/docker-desktop-kubernetes.png)

**Obrázek 3-4**. Konfigurace Kubernetes v Docker Desktop.

Docker Desktop je již nejoblíbenější nástroj pro konfiguraci a spuštění kontejnerizovaných aplikací místně. Při práci s Docker Desktop, můžete vyvíjet místně proti přesně stejnou sadu iobrazek kontejneru Dockeru, které budete nasadit do produkčního prostředí. Docker Desktop je navržen tak, aby "sestavení, testování a odeslání" kontejnerizované aplikace místně. Jakmile jsou bitové kopie odeslány do registru bitových kopií, jako je Azure Container Registry nebo Docker Hub, pak služby jako Azure Kubernetes Service (AKS) spravovat aplikaci v produkčním prostředí.

### <a name="visual-studio-docker-tooling"></a>Nástroje Pro docker u sady Visual Studio

Visual Studio podporuje vývoj Dockeru pro webové aplikace. Když vytvoříte novou ASP.NET základní aplikaci, budete mít možnost ji nakonfigurovat s podporou Dockeru jako součást procesu vytváření projektu, jak je znázorněno na obrázku 3-5.

![Podpora Pro tekutá zařízení Visual Studio](./media/visual-studio-enable-docker-support.png)

**Obrázek 3-5**. Podpora Pro tekutá zařízení Visual Studio

Když je vybrána tato možnost, `Dockerfile` projekt je vytvořen s v jeho kořenovém adresáři, který lze použít k vytvoření a hostování aplikace v kontejneru Dockeru. Příklad Dockerfile je znázorněn na obrázku 3-6.

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

**Obrázek 3-6**. Visual Studio generované Dockerfile

Výchozí chování při spuštění aplikace je nakonfigurován pro použití Dockeru také. Obrázek 3-7 ukazuje různé možnosti spuštění, které jsou k dispozici z nového projektu ASP.NET Core vytvořeného s přidanou podporou Dockeru.

![Možnosti spuštění dockeru visual studia](./media/visual-studio-docker-run-options.png)

**Obrázek 3-7**. Možnosti spuštění dockeru visual studia

Kromě místního vývoje poskytuje [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) pohodlný způsob, jak může více vývojářů pracovat s vlastními konfiguracemi Kubernetes v rámci Azure. Jak můžete vidět na obrázku 3-7, můžete také spustit aplikaci v Azure Dev Spaces.

Pokud nepřidáte podporu Dockeru do aplikace ASP.NET Core, můžete ji vždy přidat později. V Průzkumníku řešení Visual Studia klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **podporu Dockeru**, jak je znázorněno na obrázku 3-8.

![Visual Studio přidat podporu Dockeru](./media/visual-studio-add-docker-support.png)

**Obrázek 3-8**. Visual Studio přidat podporu Dockeru

Kromě podpory Dockeru můžete také přidat podporu orchestrace kontejnerů, která je také znázorněna na obrázku 3-8. Ve výchozím nastavení orchestrátor používá Kubernetes a Helm. Po výběru orchestrator, `azds.yaml` soubor je přidán do kořenového `charts` adresáře projektu a je přidána složka obsahující Helm grafy slouží ke konfiguraci a nasazení aplikace kubernetes. Obrázek 3-9 znázorňuje výsledné soubory v novém projektu.

![Visual Studio přidat orchestrator podporu](./media/visual-studio-add-orchestrator-support.png)

**Obrázek 3-9**. Visual Studio přidat orchestrator podporu

## <a name="references"></a>Odkazy

- [Co je Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalace Kubernetes s Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Předchozí](scale-applications.md)
>[další](leverage-serverless-functions.md)
