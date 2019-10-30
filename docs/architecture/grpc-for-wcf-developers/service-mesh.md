---
title: Sítě – gRPC pro vývojáře WCF
description: Použití sítě k směrování a vyrovnání požadavků na služby gRPC Services v clusteru Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6bdfa57ba47ba0105092d1c140705599b7023c78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090177"
---
# <a name="service-meshes"></a>Sítě – sítě

Síť je součást infrastruktury, která přebírá řízení žádostí o služby směrování v rámci sítě. Sítě sítí mohou zpracovávat všechny druhy obav na úrovni sítě v rámci clusteru Kubernetes, včetně těchto:

- Zjišťování služby
- Vyrovnávání zatížení
- Odolnost proti chybám
- Šifr
- Sledovaný

Sítě Kubernetes fungují přidáním dalšího kontejneru, který se označuje jako *proxy vozíku*, do každého pod tím, co je zahrnuto do sítě. Proxy přebírá všechny příchozí a odchozí síťové požadavky, což umožňuje, aby konfigurace a Správa síťových aspektů byly oddělené od kontejnerů aplikací a v mnoha případech bez nutnosti provádět změny kódu aplikace.

Proveďte [příklad předchozí kapitoly](kubernetes.md#testing-the-application), ve kterém byly všechny požadavky gRPC z webové aplikace směrovány do jediné instance služby gRPC. Důvodem je, že název hostitele služby se přeloží na IP adresu a tato IP adresa se uloží do mezipaměti po dobu života instance `HttpClientHandler`. Můžete to vyřešit tak, že ručně vyřešíte vyhledávání DNS nebo vytváříte více klientů, ale tím se kód aplikace významně nemění bez nutnosti přidat jakoukoli firmu nebo hodnotu zákazníka.

Pomocí sítě služby se požadavky z kontejneru aplikace odesílají na proxy vozík, který je může rozmístit inteligentně napříč všemi instancemi jiné služby. Síť může také:

- Bez problémů můžete reagovat na selhání jednotlivých instancí služby.
- Zpracovat sémantiku opakování pro neúspěšná volání nebo vypršení časových limitů
- Přesměrovat neúspěšné požadavky na alternativní instanci bez návratu do klientské aplikace.

Na následujícím snímku obrazovky se zobrazuje aplikace StockWeb běžící s mřížkou linkeru služby bez jakýchkoli změn v kódu aplikace nebo i v případě, že se používá Image Docker. Jediná požadovaná změna byla přidání poznámky k nasazení v souborech YAML pro služby `stockdata` a `stockweb`.

![StockWeb s sítí služby](media/service-mesh/stockweb-servicemesh-screenshot.png)

Můžete vidět ze sloupce Server, že požadavky z aplikace StockWeb byly směrovány do obou replik služby StockData, a to i v případě, že pocházejí z jediné instance `HttpClient` v kódu aplikace. Pokud zkontrolujete kód, uvidíte, že všechny požadavky 100 na službu StockData se současně používají stejnou instanci `HttpClient`, ale i s sítí služby, tyto požadavky budou vyvážené i v případě, že jsou dostupné spousty instancí služby.

Sítě se vztahují jenom na přenosy v rámci clusteru. U externích klientů si přečtěte [další kapitolu vyrovnávání zatížení](load-balancing.md).

## <a name="service-mesh-options"></a>Možnosti sítě

Existují tři implementace sítě pro obecné účely, které jsou aktuálně k dispozici pro použití s Kubernetes: Istio, linkerem a Consul Connect. Všechny tři poskytují požadavky na směrování a proxy, šifrování provozu, odolnost, ověřování od hostitele do hostitele a řízení provozu.

Volba sítě služby závisí na několika faktorech:

- Specifické požadavky organizace na náklady, dodržování předpisů, placené plány podpory atd.
- Povaha clusteru, jeho velikost, počet nasazených služeb a objem přenosů v rámci sítě s clustery.
- Snadné nasazení a Správa sítě a její použití se službami

Další informace o každé síti služby jsou k dispozici na příslušných webech.

- [**Istio** – istio.IO](https://istio.io)
- [**Linkered** – linkerd.IO](https://linkerd.io)
- [**Consul** – Consul.IO/Mesh.html](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a>Příklad: Přidání linkeru do nasazení

V tomto příkladu se dozvíte, jak používat síť s propojovacími službami s aplikací *StockKube* z [předchozí části](kubernetes.md).
Chcete-li postupovat podle tohoto příkladu, je nutné [nainstalovat linkered CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Binární soubory Windows se dají stáhnout z oddílu verze GitHubu. Ujistěte se, že používáte nejnovější **stabilní** verzi a ne jednu z hraničních vydání.

Po nainstalování linkeru rozhraní příkazového řádku, postupujte podle pokynů [*Začínáme* na linkeru webu] a nainstalujte linkerované komponenty do clusteru Kubernetes. Pokyny jsou přímo předávány a instalace by v místní instanci Kubernetes měla trvat několik minut.

### <a name="add-linkerd-to-kubernetes-deployments"></a>Přidat linkery do nasazení Kubernetes

Linkerované rozhraní příkazového řádku poskytuje `inject` příkaz pro přidání nezbytných oddílů a vlastností do souborů Kubernetes. Můžete spustit příkaz a zapsat výstup do nového souboru.

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

Můžete zkontrolovat nové soubory a zjistit, jaké změny byly provedeny. Pro objekty nasazení je přidána anotace metadat, která přihlašuje linker pro vložení kontejneru proxy vozíku do objektu pod při jeho vytvoření.

Je také možné přesměrovat výstup příkazu `linkerd inject` na `kubectl` přímo. Následující příkazy budou fungovat v PowerShellu nebo v jakémkoli prostředí Linux.

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>Kontrola služeb v řídicím panelu linkeru

Spusťte Linkerový řídicí panel pomocí rozhraní příkazového řádku `linkerd`.

```console
linkerd dashboard
```

Řídicí panel poskytuje podrobné informace o všech službách, které jsou připojené k síti.

![Linkerový řídicí panel zobrazující aplikace StockKube](media/service-mesh/linkerd-screenshot.png)

Pokud zvýšíte počet replik služby StockData gRPC, jak je znázorněno v následujícím příkladu, a aktualizovat stránku StockWeb v prohlížeči, měla by se zobrazit kombinace identifikátorů ve sloupci Server, což značí, že požadavky jsou obsluhovány všemi dostupnými instancemi. .

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
>[Předchozí](kubernetes.md)
>[Další](load-balancing.md)
