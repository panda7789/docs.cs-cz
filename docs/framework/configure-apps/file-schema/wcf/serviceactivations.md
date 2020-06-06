---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855131"
---
# \<serviceActivations>

<span data-ttu-id="3d8e9-101">Prvek konfigurace, který umožňuje přidat nastavení definující nastavení aktivace virtuální služby, která jsou namapována na vaše typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3d8e9-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="3d8e9-102">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="3d8e9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d8e9-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d8e9-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d8e9-104">Attributes and Elements</span></span>

<span data-ttu-id="3d8e9-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d8e9-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d8e9-106">Attributes</span></span>

<span data-ttu-id="3d8e9-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d8e9-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d8e9-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d8e9-108">Child Elements</span></span>

|<span data-ttu-id="3d8e9-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d8e9-109">Element</span></span>|<span data-ttu-id="3d8e9-110">Description</span><span class="sxs-lookup"><span data-stu-id="3d8e9-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="3d8e9-111">Přidá prvek konfigurace, který určuje aktivaci aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d8e9-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d8e9-112">Parent Elements</span></span>

|<span data-ttu-id="3d8e9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d8e9-113">Element</span></span>|<span data-ttu-id="3d8e9-114">Description</span><span class="sxs-lookup"><span data-stu-id="3d8e9-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="3d8e9-115">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d8e9-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d8e9-116">Remarks</span></span>

<span data-ttu-id="3d8e9-117">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-117">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="3d8e9-118">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="3d8e9-119">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="3d8e9-120">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="3d8e9-121">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="3d8e9-122">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="3d8e9-123">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="3d8e9-124">Vyžaduje rozšíření v adresa relativeAddress, tj.. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="3d8e9-125">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="3d8e9-126">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d8e9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d8e9-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
