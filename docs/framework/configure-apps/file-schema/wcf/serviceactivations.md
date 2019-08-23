---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936445"
---
# <a name="serviceactivations"></a><span data-ttu-id="f1377-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="f1377-101">\<serviceActivations></span></span>

<span data-ttu-id="f1377-102">Prvek konfigurace, který umožňuje přidat nastavení definující nastavení aktivace virtuální služby, která jsou namapována na vaše typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f1377-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="f1377-103">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="f1377-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="f1377-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1377-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="f1377-105">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="f1377-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="f1377-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="f1377-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="f1377-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1377-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1377-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1377-108">Attributes and Elements</span></span>

<span data-ttu-id="f1377-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1377-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1377-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1377-110">Attributes</span></span>

<span data-ttu-id="f1377-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1377-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f1377-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1377-112">Child Elements</span></span>

|<span data-ttu-id="f1377-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1377-113">Element</span></span>|<span data-ttu-id="f1377-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f1377-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f1377-115">\<add></span><span class="sxs-lookup"><span data-stu-id="f1377-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="f1377-116">Přidá prvek konfigurace, který určuje aktivaci aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="f1377-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f1377-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1377-117">Parent Elements</span></span>

|<span data-ttu-id="f1377-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1377-118">Element</span></span>|<span data-ttu-id="f1377-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f1377-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f1377-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="f1377-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="f1377-121">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="f1377-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f1377-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1377-122">Remarks</span></span>

<span data-ttu-id="f1377-123">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="f1377-123">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="f1377-124">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="f1377-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="f1377-125">Všimněte si `<serviceHostingEnvironment>` , že je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1377-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f1377-126">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1377-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f1377-127">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="f1377-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="f1377-128">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f1377-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="f1377-129">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1377-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f1377-130">Vyžaduje rozšíření v adresa relativeAddress, tj. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="f1377-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f1377-131">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f1377-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f1377-132">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="f1377-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1377-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1377-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
