---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920027"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="dfbc4-102">\<Přidat > \<> serviceActivations</span><span class="sxs-lookup"><span data-stu-id="dfbc4-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="dfbc4-103">Prvek konfigurace, který umožňuje definovat nastavení aktivace virtuální služby, která se mapují na typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dfbc4-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="dfbc4-104">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="dfbc4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dfbc4-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="dfbc4-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="dfbc4-106">\<serviceHostingEnvironment></span></span>

## <a name="syntax"></a><span data-ttu-id="dfbc4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfbc4-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfbc4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dfbc4-108">Attributes and Elements</span></span>

<span data-ttu-id="dfbc4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfbc4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="dfbc4-110">Attributes</span></span>

|<span data-ttu-id="dfbc4-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="dfbc4-111">Attribute</span></span>|<span data-ttu-id="dfbc4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dfbc4-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dfbc4-113">instalací</span><span class="sxs-lookup"><span data-stu-id="dfbc4-113">factory</span></span>|<span data-ttu-id="dfbc4-114">Řetězec, který určuje název typu CLR továrny, která generuje prvek aktivace služby.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="dfbc4-115">service</span><span class="sxs-lookup"><span data-stu-id="dfbc4-115">service</span></span>|<span data-ttu-id="dfbc4-116">ServiceType, který implementuje službu (buď plně kvalifikovaný typeName, nebo krátký TypeName (při umístění do složky App_Code).</span><span class="sxs-lookup"><span data-stu-id="dfbc4-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="dfbc4-117">Adresa relativeAddress</span><span class="sxs-lookup"><span data-stu-id="dfbc4-117">relativeAddress</span></span>|<span data-ttu-id="dfbc4-118">Relativní adresa v rámci aktuální aplikace služby IIS – například "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="dfbc4-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="dfbc4-119">V WCF 4,0 tato relativní adresa musí obsahovat jednu ze známých přípon souborů (. svc,. xamlx,...). Neexistuje žádný fyzický soubor pro relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="dfbc4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dfbc4-120">Child Elements</span></span>

<span data-ttu-id="dfbc4-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="dfbc4-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dfbc4-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dfbc4-122">Parent Elements</span></span>

|<span data-ttu-id="dfbc4-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="dfbc4-123">Element</span></span>|<span data-ttu-id="dfbc4-124">Popis</span><span class="sxs-lookup"><span data-stu-id="dfbc4-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfbc4-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="dfbc4-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="dfbc4-126">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-126">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dfbc4-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfbc4-127">Remarks</span></span>

<span data-ttu-id="dfbc4-128">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-128">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="dfbc4-129">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="dfbc4-130">Všimněte si `<serviceHostingEnvironment>` , že je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="dfbc4-131">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="dfbc4-132">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-132">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="dfbc4-133">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="dfbc4-134">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="dfbc4-135">Vyžaduje rozšíření v adresa relativeAddress, tj. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-135">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="dfbc4-136">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="dfbc4-137">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="dfbc4-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfbc4-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfbc4-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
