---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855131"
---
# <a name="serviceactivations"></a><span data-ttu-id="46011-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="46011-101">\<serviceActivations></span></span>

<span data-ttu-id="46011-102">Prvek konfigurace, který umožňuje přidat nastavení definující nastavení aktivace virtuální služby, která jsou namapována na vaše typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="46011-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="46011-103">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="46011-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="46011-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="46011-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="46011-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="46011-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="46011-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="46011-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="46011-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceActivations >**</span><span class="sxs-lookup"><span data-stu-id="46011-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="46011-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46011-108">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46011-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46011-109">Attributes and Elements</span></span>

<span data-ttu-id="46011-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46011-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="46011-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="46011-111">Attributes</span></span>

<span data-ttu-id="46011-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="46011-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46011-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46011-113">Child Elements</span></span>

|<span data-ttu-id="46011-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="46011-114">Element</span></span>|<span data-ttu-id="46011-115">Popis</span><span class="sxs-lookup"><span data-stu-id="46011-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46011-116">\<add></span><span class="sxs-lookup"><span data-stu-id="46011-116">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="46011-117">Přidá prvek konfigurace, který určuje aktivaci aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="46011-117">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="46011-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46011-118">Parent Elements</span></span>

|<span data-ttu-id="46011-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="46011-119">Element</span></span>|<span data-ttu-id="46011-120">Popis</span><span class="sxs-lookup"><span data-stu-id="46011-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46011-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="46011-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="46011-122">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="46011-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="46011-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46011-123">Remarks</span></span>

<span data-ttu-id="46011-124">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="46011-124">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="46011-125">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="46011-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="46011-126">Všimněte si `<serviceHostingEnvironment>` , že je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="46011-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="46011-127">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="46011-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="46011-128">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="46011-128">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="46011-129">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="46011-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="46011-130">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="46011-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="46011-131">Vyžaduje rozšíření v adresa relativeAddress, tj. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="46011-131">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="46011-132">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="46011-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="46011-133">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="46011-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="46011-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46011-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
