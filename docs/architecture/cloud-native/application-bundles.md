---
title: Aplikační komplety nativní pro cloud
description: Architekt cloudových nativních aplikací .NET pro Azure | Balíčky nativních aplikací cloudu
ms.date: 06/30/2019
ms.openlocfilehash: 6f85ca14ff4d17f9c7a90a9ace51a1448b89fcb3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895685"
---
# <a name="cloud-native-application-bundles"></a>Aplikační komplety nativní pro cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Klíčovou vlastností aplikací nativních pro Cloud je, že využívají vlastnosti cloudu k urychlení vývoje. To často znamená, že plná aplikace používá různé druhy technologií. Aplikace se můžou dodávat v kontejnerech Docker, některé služby můžou použít Azure Functions, zatímco jiné části můžou běžet přímo na virtuálních počítačích, které jsou přidělené na rozsáhlých serverech s hardwarovou akcelerací GPU. Neexistují žádné dvě aplikace nativní pro Cloud, takže je obtížné poskytnout jeden mechanismus pro jejich odeslání.

Kontejnery Docker se můžou spouštět na Kubernetes pomocí grafu Helm pro nasazení. Azure Functions mohou být přiděleny pomocí šablon Terraformu. A konečně, virtuální počítače se dají přidělit pomocí Terraformu, ale vybudované pomocí Ansible. Toto je celá část technologií a neexistuje žádný způsob, jak je zabalit dohromady do přijatelného balíčku. Až do této chvíle.

Balíčky nativních aplikací cloudu (CNABs) jsou společnou snahou o řadu společností, jako je Microsoft, Docker a HashiCorp, pro vývoj specifikace pro balení distribuovaných aplikací.

Úsilí bylo oznámeno v prosinci 2018, proto je stále k dispozici reálná práce, která umožňuje vystavit úsilí pro větší komunitu. Nicméně již existuje [otevřená specifikace](https://github.com/deislabs/cnab-spec) a referenční implementace známá jako [DUFFLE](https://duffle.sh/). Tento nástroj, který byl napsán na cestách, je společným úsilím mezi Docker a Microsoftem.

CNABs může obsahovat různé druhy technologií instalace. To umožňuje, aby existovaly věci jako grafy Helm, šablony Terraformu a Ansible Playbooky ve stejném balíčku. Po sestavení jsou balíčky samostatně obsažené a přenosné; je možné je nainstalovat z USB Stick.  Balíčky jsou kryptograficky podepsány, aby bylo zajištěno, že pocházejí ze strany, které vyžádají.

Jádrem CNAB je soubor s názvem `bundle.json`. Tento soubor definuje obsah sady, Terraformu nebo obrázky nebo cokoli jiného. Obrázek 11-9 definuje CNAB, který vyvolá některé Terraformu. Všimněte si ale, že ve skutečnosti definuje obrázek vyvolání, který se používá k vyvolání Terraformu. Po zabalení je soubor Docker umístěný v adresáři *cnab* integrovaný do bitové kopie Docker, která bude součástí sady prostředků. Pokud se Terraformu nainstaluje v kontejneru Docker v balíčku, znamená to, že uživatelé nemusí mít na svém počítači nainstalovanou Terraformu pro spuštění sdružování.

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

**Obrázek 11-13** – ukázkový soubor terraformu

`bundle.json` Také definuje sadu parametrů, které jsou předány do terraformu. Parametrizace sady umožňuje instalaci v různých prostředích.

Formát CNAB je také flexibilní a umožňuje ho použít pro jakýkoliv Cloud. Může se dokonce používat i pro místní řešení, jako je [OpenStack](https://www.openstack.org/).

## <a name="devops-decisions"></a>DevOps rozhodnutí

K dispozici je spousta skvělých nástrojů v DevOps prostoru a ještě více fantastickách knih a dokumentů, jak to bude úspěšné. Oblíbená kniha pro zahájení práce na DevOps je [projekt v Phoenixu](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), který následuje po transformaci fiktivní společnosti z NoOps na DevOps. Jedna věc je určena pro určité: DevOps již není "dobrým", když nasazujete komplexní cloudové nativní aplikace. Je to požadavek a měl by být plánován na začátku libovolného projektu a měl by být naplánován na jeho zdroj.

>[!div class="step-by-step"]
>[Předchozí](infrastructure-as-code.md)
>[Další](summary.md)
