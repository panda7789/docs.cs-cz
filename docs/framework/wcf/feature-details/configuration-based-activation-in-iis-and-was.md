---
title: Aktivace založená na konfiguraci v IIS a WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: f4de4aff2fbe6b8e82dc3d6523f492d06494c79e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909773"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="f136d-102">Aktivace založená na konfiguraci v IIS a WAS</span><span class="sxs-lookup"><span data-stu-id="f136d-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="f136d-103">Normálně při hostování služby Windows Communication Foundation (WCF) v rámci služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS) je nutné zadat soubor. svc.</span><span class="sxs-lookup"><span data-stu-id="f136d-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="f136d-104">Soubor. svc obsahuje název služby a volitelný vlastní objekt pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="f136d-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="f136d-105">Tento další soubor přináší režii spravovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="f136d-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="f136d-106">Funkce aktivace na základě konfigurace odebere požadavek na soubor. svc, a proto na přidruženou režii.</span><span class="sxs-lookup"><span data-stu-id="f136d-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="f136d-107">Aktivace podle konfigurace</span><span class="sxs-lookup"><span data-stu-id="f136d-107">Configuration-Based Activation</span></span>

<span data-ttu-id="f136d-108">Aktivace na základě konfigurace přebírá metadata, která se používají k umístění do souboru. svc, a umístí je do souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="f136d-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="f136d-109">V rámci prvku`serviceHostingEnvironment`< > je <`serviceActivations`> element.</span><span class="sxs-lookup"><span data-stu-id="f136d-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="f136d-110">V rámci prvku`serviceActivations`< > je jeden nebo více <ch`add`> prvků, jeden pro každou hostovanou službu.</span><span class="sxs-lookup"><span data-stu-id="f136d-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="f136d-111">Prvek <`add`> obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo objekt pro vytváření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="f136d-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="f136d-112">Následující příklad kódu konfigurace ukazuje, jak se tento oddíl používá.</span><span class="sxs-lookup"><span data-stu-id="f136d-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="f136d-113">Každý <`add`> elementu musí určovat atribut Service nebo Factory.</span><span class="sxs-lookup"><span data-stu-id="f136d-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="f136d-114">Zadání atributů Service a Factory je povoleno.</span><span class="sxs-lookup"><span data-stu-id="f136d-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="f136d-115">S tímto souborem v souboru Web. config můžete umístit zdrojový kód služby do adresáře App_Code aplikace nebo sestavení se stavem v adresáři bin aplikace.</span><span class="sxs-lookup"><span data-stu-id="f136d-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
> - <span data-ttu-id="f136d-116">Při použití aktivace na základě konfigurace není podporován vložený kód v souborech. svc.</span><span class="sxs-lookup"><span data-stu-id="f136d-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="f136d-117">Atribut musí být nastaven na relativní adresu, například "\<podadresář >/Service.svc" nebo "~/\<sub-Directory/Service. svc". `relativeAddress`</span><span class="sxs-lookup"><span data-stu-id="f136d-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="f136d-118">Výjimka konfigurace je vyvolána, pokud zaregistrujete relativní adresu, která nemá známou příponu přidruženou ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="f136d-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="f136d-119">Zadaná relativní adresa je relativní vzhledem k kořenu virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="f136d-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="f136d-120">Z důvodu hierarchického modelu konfigurace jsou zaregistrované relativní adresy na úrovni počítače a webu děděny virtuálními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="f136d-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="f136d-121">Registrace v konfiguračním souboru mají přednost před nastaveními v souboru. svc,. xamlx,. XOML nebo jiném souboru.</span><span class="sxs-lookup"><span data-stu-id="f136d-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="f136d-122">Všechna lomítka (zpětná lomítka) v identifikátoru URI odeslanému službě IIS/WAS se automaticky převádějí na lomítko (lomítko).</span><span class="sxs-lookup"><span data-stu-id="f136d-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="f136d-123">Pokud přidáte relativní adresu obsahující "\" a odešlete identifikátor URI služby IIS, který používá relativní adresu, zpětné lomítko se převede na lomítko a služba IIS ji nemůže spárovat s relativní adresou.</span><span class="sxs-lookup"><span data-stu-id="f136d-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="f136d-124">Služba IIS odesílá informace o trasování, které označují, že se nenašly žádné shody.</span><span class="sxs-lookup"><span data-stu-id="f136d-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="f136d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f136d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="f136d-126">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="f136d-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="f136d-127">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f136d-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [<span data-ttu-id="f136d-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="f136d-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [<span data-ttu-id="f136d-129">Funkce hostování technologie Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="f136d-129">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
