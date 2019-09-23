---
title: Kubernetes-gRPC pro vývojáře WCF
description: Spuštění ASP.NET Core gRPC Services v clusteru Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3af1b92ade106cf2338816ec69e6b13312681339
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184405"
---
# <a name="kubernetes"></a>Kubernetes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Přestože je možné ručně spustit kontejnery na hostitelích Docker, pro spolehlivé provozní systémy je vhodnější použít modul orchestrace kontejnerů ke správě více instancí spuštěných v několika serverech v clusteru. K dispozici jsou různé moduly pro orchestraci kontejnerů, včetně Kubernetes, Docker Swarm a Apache Mesos. V těchto modulech ale Kubernetes je daleko a nejvíce využíváno, takže bude tato kapitola zaměřena.

Kubernetes obsahuje následující funkce:

- **Plánování** spouští kontejnery na více uzlech v rámci clusteru, což zajišťuje vyvážené využití dostupného prostředku, udržování kontejnerů běžících v případě výpadků a zpracování kumulativních aktualizací pro nové verze imagí nebo nové konfigurace.
- **Kontroly stavu** monitorují kontejnery, aby bylo zajištěno pokračování služby.
- **Služba DNS & Service Discovery** zpracovává směrování mezi službami v rámci clusteru.
- Příchozí **zpřístupňuje** vybrané služby externě a obecně poskytuje vyrovnávání zatížení napříč instancemi těchto služeb.
- **Správa prostředků** připojuje externí prostředky, jako je třeba úložiště, do kontejnerů.

Tato kapitola podrobně popisuje, jak nasadit službu ASP.NET Core gRPC a webovou stránku, která tuto službu spotřebovává do clusteru Kubernetes. Použitá ukázková aplikace je k dispozici v úložišti [RendleLabs/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.

## <a name="kubernetes-terminology"></a>Terminologie Kubernetes

Kubernetes používá *konfiguraci požadovaného stavu*: rozhraní API se používá k popisu objektů, jako jsou *lusky*, *nasazení* a *služby*, a *Řídicí rovina* se stará o implementaci požadovaného stavu napříč všemi *uzly.* v *clusteru*. Cluster Kubernetes má *Hlavní* uzel, který spouští *rozhraní Kubernetes API*, které se dá komunikovat prostřednictvím kódu programu `kubectl` nebo pomocí nástroje příkazového řádku. `kubectl`může vytvářet a spravovat objekty pomocí argumentů příkazového řádku, ale funguje nejlépe s YAML soubory, které obsahují data deklarace pro objekty Kubernetes.

### <a name="kubernetes-yaml-files"></a>Soubory Kubernetes YAML

Každý soubor Kubernetes YAML bude mít alespoň tři vlastnosti nejvyšší úrovně.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

Tato `apiVersion` vlastnost slouží k určení verze (a rozhraní API), pro který je soubor určen. `kind` Vlastnost určuje druh objektu, který YAML představuje. Vlastnost obsahuje vlastnosti objektu `name`, například, `namespace`nebo `labels`. `metadata`

Většina souborů YAML Kubernetes bude také obsahovat `spec` oddíl, který popisuje prostředky a konfiguraci potřebné k vytvoření objektu.

### <a name="pods"></a>Podů

Lusky jsou základními jednotkami spuštění v Kubernetes. Můžou spouštět více kontejnerů, ale také se používají ke spouštění jednoduchých kontejnerů. Pod ní také najdete všechny prostředky úložiště, které jsou požadovány kontejnery, a síťovou IP adresu.

### <a name="services"></a>Služby

Služby jsou meta objekty, které popisují lusky (nebo sady lusků) a poskytují způsob, jak k nim přistupovat v rámci clusteru, jako je například mapování názvu služby na skupinu pod IP adresou pomocí služby DNS clusteru.

### <a name="deployments"></a>Nasazení

Nasazení jsou *popsány stavové* objekty pro lusky. Pokud vytvoříte v případě ručně, při jeho ukončení se nerestartuje. Nasazení se používají k tomu, aby cluster informoval a kolik replik v těchto luskech měl běžet v současné době.

### <a name="other-objects"></a>Další objekty

Lusky, služby a nasazení představují jenom tři základní typy objektů. Existují spousty dalších typů objektů, které jsou spravovány clusterem Kubernetes. Další informace najdete v dokumentaci k [konceptům Kubernetes](https://kubernetes.io/docs/concepts/) .

### <a name="namespaces"></a>Jmenné prostory

Clustery Kubernetes jsou navržené tak, aby se škálovat na stovky nebo tisíce uzlů a spouštěly podobné počty služeb. Aby nedocházelo ke konfliktům mezi názvy objektů, používají se obory názvů k seskupení objektů dohromady jako součást větších aplikací. Vlastní služby Kubernetes běží v `default` oboru názvů. Všechny uživatelské objekty by měly být vytvořeny ve vlastních oborech názvů, aby se předešlo potenciálním konfliktům s výchozími objekty nebo jinými klienty v clusteru.

## <a name="get-started-with-kubernetes"></a>Začínáme s Kubernetes

Pokud používáte Docker Desktop pro Windows nebo macOS, je Kubernetes již k dispozici. Stačí ho povolit v části Kubernetes okna nastavení.

![Povolit Kubernetes v Docker desktopu](media/kubernetes/enable-kubernetes-docker-desktop.png)

Chcete-li spustit místní cluster Kubernetes v systému Linux, podívejte se na [minikube](https://github.com/kubernetes/minikube), nebo [MicroK8s](https://microk8s.io/) , pokud je vaše distribuce systému Linux podporována [přichycení](https://snapcraft.io/).

Pokud chcete ověřit, že je cluster spuštěný a přístupný, `kubectl version` spusťte příkaz.

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

V tomto příkladu jsou spuštěny `kubectl` rozhraní příkazového řádku a serveru Kubernetes verze 1.14.6. Každá verze `kubectl` nástroje má podporovat předchozí a další verzi serveru, takže `kubectl` 1,14 by měla fungovat i s verzemi serveru 1,13 a 1,15.

## <a name="run-services-on-kubernetes"></a>Spuštění služeb na Kubernetes

Ukázková aplikace obsahuje `kube` adresář obsahující tři soubory YAML. Soubor deklaruje vlastní `stocks`obor názvů. `namespace.yml` Soubor deklaruje nasazení a službu pro aplikaci gRPC `stockweb.yml` a soubor deklaruje nasazení a službu pro webovou aplikaci ASP.NET Core 3,0 MVC, která využívá službu gRPC. `stockdata.yml`

Chcete-li `YAML` použít soubor `kubectl`s, použijte `apply -f` příkaz.

```console
kubectl apply -f object.yml
```

`apply` Příkaz zkontroluje platnost souboru YAML a zobrazí všechny chyby obdržené z rozhraní API, ale nečeká na vytvoření všech objektů deklarovaných v souboru, protože to může nějakou dobu trvat. `kubectl get` Pomocí příkazu s relevantními typy objektů ověřte vytvoření objektu v clusteru.

### <a name="the-namespace-declaration"></a>Deklarace oboru názvů

Deklarace oboru názvů je jednoduchá a vyžaduje pouze přiřazení `name`.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

Použijte `kubectl` k`namespace.yml` použití souboru a kontrolu úspěšného vytvoření oboru názvů.

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>Aplikace StockData

`stockdata.yml` Soubor deklaruje dva objekty: nasazení a službu.

#### <a name="the-stockdata-deployment"></a>Nasazení StockData

Část nasazení poskytuje `spec` vlastní nasazení, včetně počtu požadovaných replik, `template` a pro objekty pod, které má nasazení vytvořit a spravovat. Všimněte si, že objekty nasazení jsou spravovány pomocí `apps` rozhraní API, jak je uvedeno v `apiVersion`, nikoli v hlavním rozhraní Kubernetes API.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

`spec.selector` Vlastnost se používá ke spárování spuštěných lusků s nasazením. `metadata.labels` Vlastnost pod musí `matchLabels` odpovídat vlastnosti nebo volání rozhraní API se nezdaří.

`template.spec` Oddíl deklaruje kontejner, který má být spuštěn. Při práci s místním clusterem Kubernetes, jako je ten, který poskytuje Docker Desktop, můžete zadat obrázky, které byly vytvořeny místně, pokud mají značku verze.

> [!IMPORTANT]
> Ve výchozím nastavení se Kubernetes vždycky pokusí vyhledat novou image a zkusit si ji stáhnout. Pokud nenalezne obrázek v žádné z jeho známých úložišť, vytvoření pod se nezdaří. Chcete-li pracovat s místními bitovými `imagePullPolicy` kopiemi, nastavte na `Never`.

`ports` Vlastnost určuje, které porty kontejneru by měly být publikovány na pod.  `stockservice` Image spustí službu na standardním portu HTTP, takže se publikuje port 80.

V `resources` části se aplikují omezení prostředků na kontejner běžící v poli pod. To je dobrý postup, protože zabrání jednotlivcům pod spotřebou veškerého dostupného procesoru nebo paměti na uzlu.

> [!NOTE]
> ASP.NET Core 3,0 je optimalizované a vyladěné pro spouštění v kontejnerech s omezenými `dotnet/core/aspnet` prostředky a image Docker nastavuje proměnnou prostředí, která `dotnet` sděluje modulu runtime, že je v kontejneru.

#### <a name="the-stockdata-service"></a>Služba StockData

Část služby YAML souboru deklaruje službu, která poskytuje přístup k Luskům v rámci clusteru.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

Specifikace služby používá `selector` vlastnost, která se shoduje se `Pods`spuštěným, v tomto případě hledá lusky pomocí `run: stockdata`popisku. Pojmenovaná `port` v poli pro spárování jsou publikována pomocí pojmenované služby. Jiné lusky běžící v `stocks` oboru názvů mají přístup k http na této `http://stockdata` službě pomocí adresy. Lusky běžící v jiných oborech názvů `http://stockdata.stocks` můžou používat název hostitele. Přístup ke službě mezi obory názvů můžete řídit pomocí [zásad sítě](https://kubernetes.io/docs/concepts/services-networking/network-policies/).

#### <a name="deploy-the-stockdata-application"></a>Nasazení aplikace StockData

Použijte `kubectl` k`stockdata.yml` instalaci souboru a kontrole, jestli se vytvořilo nasazení a služba.

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>Aplikace StockWeb

`stockweb.yml` Soubor deklaruje nasazení a službu pro aplikaci MVC.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>Proměnné prostředí

Část objektu nasazení určuje proměnné prostředí, které mají být nastaveny v kontejneru, ve kterém jsou `stockweb:1.0.0` spuštěny obrázky. `env`

Proměnná prostředí bude namapována `StockData:Address` na nastavení konfigurace díky poskytovateli konfigurace EnvironmentVariables. **`StockData__Address`** Toto nastavení používá pro samostatné oddíly dvojitá podtržítka mezi názvy. Adresa používá název `stockdata` služby, který je spuštěný ve stejném oboru názvů Kubernetes.

Proměnná prostředí nastaví přepínač, který umožňuje nešifrované připojení HTTP/2 pro <xref:System.Net.Http.HttpClient>. <xref:System.AppContext> **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** Tato proměnná prostředí je ekvivalentem nastavení přepínače v kódu, jak je znázorněno zde.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Použití proměnné prostředí pro přepínač znamená, že nastavení může být snadno změněno v závislosti na kontextu, ve kterém je aplikace spuštěná.

#### <a name="service-types"></a>Typy služeb

Aby byla webová aplikace přístupná z vnějšku clusteru, `type: NodePort` je použita vlastnost. Tento typ vlastnosti způsobí, že Kubernetes publikuje port 80 ve službě na libovolný port na soketech externích sítí clusteru. Přiřazený port lze najít pomocí `kubectl get service` příkazu.

Služba by neměla být přístupná z vnějšku clusteru, takže používala výchozí `ClusterIP`typ. `stockdata`

Provozní systémy budou pravděpodobně využívat integrovaný nástroj pro vyrovnávání zatížení a zpřístupňují veřejné aplikace externím uživatelům. Služby, které jsou `LoadBalancer` k dispozici tímto způsobem, by měly používat typ.

Další informace o typech služeb najdete v dokumentaci k [publikování služby Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .

#### <a name="deploy-the-stockweb-application"></a>Nasazení aplikace StockWeb

Použijte `kubectl` k`stockweb.yml` instalaci souboru a kontrole, jestli se vytvořilo nasazení a služba.

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

Výstup z `get service` příkazu ukazuje, že port http byl publikován na portu `32564` v externí síti; u Docker desktopu bude to localhost. K aplikaci lze přistupovat procházením `http://localhost:32564`.

### <a name="testing-the-application"></a>Testování aplikace

Aplikace StockWeb zobrazí seznam akcií NASDAQ, které se načítají z jednoduché služby Request-Reply. Pro demonstrační účely zobrazuje každý řádek také jedinečné ID instance služby, která ho vrátila.

![Snímek obrazovky StockWeb](media/kubernetes/stockweb-screenshot.png)

Pokud se počet replik `stockdata` služby zvýšil, může se stát, že se hodnota **serveru** změní z řádku na řádek, ale ve skutečnosti všechny 100 záznamy se vždycky vrátí ze stejné instance. Pokud aktualizujete stránku každých několik sekund, ID serveru zůstane stejné. Proč k tomu dochází? Tady jsou dva faktory.

Nejprve systém zjišťování služby Kubernetes ve výchozím nastavení používá Vyrovnávání zatížení pomocí kruhového dotazování. Při prvním dotazování serveru DNS se vrátí první vyhovující IP adresa pro službu. V dalším čase, další IP adresa v seznamu atd., až do konce, v tomto okamžiku se smyčkou vrátí zpět na začátek.

Za druhé [](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)se používáproklientagRPCaplikaceStockWebajespravovánpomocíASP.NETCoreHttpClientFactoryajednainstancetohotoklientasepoužíváprokaždévolání`HttpClient` stránky. Klient nástroje provádí pouze jedno vyhledání DNS, takže všechny požadavky jsou směrovány na stejnou IP adresu. Vzhledem k tomu, `HttpClientHandler` že z důvodu výkonu z mezipaměti je mezipaměť více požadavků, bude v rychlém úspěchu více *využívala* stejná IP adresa, dokud nevyprší platnost položky DNS v mezipaměti nebo z nějakého důvodu nebude odstraněna instance obslužné rutiny.

To znamená, že ve výchozím nastavení nejsou požadavky na službu gRPC vyvážené napříč všemi instancemi této služby v clusteru. Různí spotřebitelé budou používat různé instance, ale nezaručují dobrou distribuci požadavků a vyvážené používání prostředků.

Další kapitola, [sítě a sítě](service-mesh.md), se podíváme na to, jak tento problém vyřešit.

>[!div class="step-by-step"]
>[Předchozí](docker.md)
>[Další](service-mesh.md)
