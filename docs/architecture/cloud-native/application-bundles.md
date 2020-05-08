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
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="f3bed-103">Aplikační komplety nativní pro cloud</span><span class="sxs-lookup"><span data-stu-id="f3bed-103">Cloud Native Application Bundles</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f3bed-104">Klíčovou vlastností aplikací nativních pro Cloud je, že využívají vlastnosti cloudu k urychlení vývoje.</span><span class="sxs-lookup"><span data-stu-id="f3bed-104">A key property of cloud-native applications is that they leverage the properties of the cloud to speed up development.</span></span> <span data-ttu-id="f3bed-105">To často znamená, že plná aplikace používá různé druhy technologií.</span><span class="sxs-lookup"><span data-stu-id="f3bed-105">This often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="f3bed-106">Aplikace se můžou dodávat v kontejnerech Docker, některé služby můžou použít Azure Functions, zatímco jiné části můžou běžet přímo na virtuálních počítačích, které jsou přidělené na rozsáhlých serverech s hardwarovou akcelerací GPU.</span><span class="sxs-lookup"><span data-stu-id="f3bed-106">Applications may be shipped in Docker containers, some services may use Azure Functions while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="f3bed-107">Neexistují žádné dvě aplikace nativní pro Cloud, takže je obtížné poskytnout jeden mechanismus pro jejich odeslání.</span><span class="sxs-lookup"><span data-stu-id="f3bed-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="f3bed-108">Kontejnery Docker se můžou spouštět na Kubernetes pomocí grafu Helm pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="f3bed-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="f3bed-109">Azure Functions mohou být přiděleny pomocí šablon Terraformu.</span><span class="sxs-lookup"><span data-stu-id="f3bed-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="f3bed-110">A konečně, virtuální počítače se dají přidělit pomocí Terraformu, ale vybudované pomocí Ansible.</span><span class="sxs-lookup"><span data-stu-id="f3bed-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="f3bed-111">Toto je celá část technologií a neexistuje žádný způsob, jak je zabalit dohromady do přijatelného balíčku.</span><span class="sxs-lookup"><span data-stu-id="f3bed-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="f3bed-112">Až do této chvíle.</span><span class="sxs-lookup"><span data-stu-id="f3bed-112">Until now.</span></span>

<span data-ttu-id="f3bed-113">Balíčky nativních aplikací cloudu (CNABs) jsou společnou snahou o řadu společností, jako je Microsoft, Docker a HashiCorp, pro vývoj specifikace pro balení distribuovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="f3bed-113">Cloud Native Application Bundles (CNABs) are a joint effort of a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="f3bed-114">Úsilí bylo oznámeno v prosinci 2018, proto je stále k dispozici reálná práce, která umožňuje vystavit úsilí pro větší komunitu.</span><span class="sxs-lookup"><span data-stu-id="f3bed-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="f3bed-115">Nicméně již existuje [otevřená specifikace](https://github.com/deislabs/cnab-spec) a referenční implementace známá jako [DUFFLE](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="f3bed-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="f3bed-116">Tento nástroj, který byl napsán na cestách, je společným úsilím mezi Docker a Microsoftem.</span><span class="sxs-lookup"><span data-stu-id="f3bed-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="f3bed-117">CNABs může obsahovat různé druhy technologií instalace.</span><span class="sxs-lookup"><span data-stu-id="f3bed-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="f3bed-118">To umožňuje, aby existovaly věci jako grafy Helm, šablony Terraformu a Ansible Playbooky ve stejném balíčku.</span><span class="sxs-lookup"><span data-stu-id="f3bed-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="f3bed-119">Po sestavení jsou balíčky samostatně obsažené a přenosné; je možné je nainstalovat z USB Stick.</span><span class="sxs-lookup"><span data-stu-id="f3bed-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="f3bed-120">Balíčky jsou kryptograficky podepsány, aby bylo zajištěno, že pocházejí ze strany, které vyžádají.</span><span class="sxs-lookup"><span data-stu-id="f3bed-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="f3bed-121">Jádrem CNAB je soubor s názvem `bundle.json`.</span><span class="sxs-lookup"><span data-stu-id="f3bed-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="f3bed-122">Tento soubor definuje obsah sady, Terraformu nebo obrázky nebo cokoli jiného.</span><span class="sxs-lookup"><span data-stu-id="f3bed-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="f3bed-123">Obrázek 11-9 definuje CNAB, který vyvolá některé Terraformu.</span><span class="sxs-lookup"><span data-stu-id="f3bed-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="f3bed-124">Všimněte si ale, že ve skutečnosti definuje obrázek vyvolání, který se používá k vyvolání Terraformu.</span><span class="sxs-lookup"><span data-stu-id="f3bed-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="f3bed-125">Po zabalení je soubor Docker umístěný v adresáři *cnab* integrovaný do bitové kopie Docker, která bude součástí sady prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3bed-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="f3bed-126">Pokud se Terraformu nainstaluje v kontejneru Docker v balíčku, znamená to, že uživatelé nemusí mít na svém počítači nainstalovanou Terraformu pro spuštění sdružování.</span><span class="sxs-lookup"><span data-stu-id="f3bed-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="f3bed-127">**Obrázek 11-13** – ukázkový soubor terraformu</span><span class="sxs-lookup"><span data-stu-id="f3bed-127">**Figure 11-13** - An example Terraform file</span></span>

<span data-ttu-id="f3bed-128">`bundle.json` Také definuje sadu parametrů, které jsou předány do terraformu.</span><span class="sxs-lookup"><span data-stu-id="f3bed-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="f3bed-129">Parametrizace sady umožňuje instalaci v různých prostředích.</span><span class="sxs-lookup"><span data-stu-id="f3bed-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="f3bed-130">Formát CNAB je také flexibilní a umožňuje ho použít pro jakýkoliv Cloud.</span><span class="sxs-lookup"><span data-stu-id="f3bed-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="f3bed-131">Může se dokonce používat i pro místní řešení, jako je [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="f3bed-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="f3bed-132">DevOps rozhodnutí</span><span class="sxs-lookup"><span data-stu-id="f3bed-132">DevOps Decisions</span></span>

<span data-ttu-id="f3bed-133">K dispozici je spousta skvělých nástrojů v DevOps prostoru a ještě více fantastickách knih a dokumentů, jak to bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f3bed-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="f3bed-134">Oblíbená kniha pro zahájení práce na DevOps je [projekt v Phoenixu](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), který následuje po transformaci fiktivní společnosti z NoOps na DevOps.</span><span class="sxs-lookup"><span data-stu-id="f3bed-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="f3bed-135">Jedna věc je určena pro určité: DevOps již není "dobrým", když nasazujete komplexní cloudové nativní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3bed-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="f3bed-136">Je to požadavek a měl by být plánován na začátku libovolného projektu a měl by být naplánován na jeho zdroj.</span><span class="sxs-lookup"><span data-stu-id="f3bed-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3bed-137">[Předchozí](infrastructure-as-code.md)
>[Další](summary.md)</span><span class="sxs-lookup"><span data-stu-id="f3bed-137">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
