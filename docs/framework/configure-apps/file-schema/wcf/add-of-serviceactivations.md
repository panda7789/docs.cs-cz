---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850328"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="bbbae-102">\<Přidat > \<> serviceActivations</span><span class="sxs-lookup"><span data-stu-id="bbbae-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="bbbae-103">Prvek konfigurace, který umožňuje definovat nastavení aktivace virtuální služby, která se mapují na typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bbbae-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="bbbae-104">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="bbbae-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="bbbae-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bbbae-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bbbae-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bbbae-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bbbae-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="bbbae-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="bbbae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceActivations >** ](serviceactivations.md)</span><span class="sxs-lookup"><span data-stu-id="bbbae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)</span></span>\
<span data-ttu-id="bbbae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="bbbae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="bbbae-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbbae-110">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbbae-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bbbae-111">Attributes and Elements</span></span>

<span data-ttu-id="bbbae-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bbbae-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbbae-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bbbae-113">Attributes</span></span>

|<span data-ttu-id="bbbae-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bbbae-114">Attribute</span></span>|<span data-ttu-id="bbbae-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bbbae-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="bbbae-116">instalací</span><span class="sxs-lookup"><span data-stu-id="bbbae-116">factory</span></span>|<span data-ttu-id="bbbae-117">Řetězec, který určuje název typu CLR továrny, která generuje prvek aktivace služby.</span><span class="sxs-lookup"><span data-stu-id="bbbae-117">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="bbbae-118">service</span><span class="sxs-lookup"><span data-stu-id="bbbae-118">service</span></span>|<span data-ttu-id="bbbae-119">ServiceType, který implementuje službu (buď plně kvalifikovaný typeName, nebo krátký TypeName (při umístění do složky App_Code).</span><span class="sxs-lookup"><span data-stu-id="bbbae-119">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="bbbae-120">Adresa relativeAddress</span><span class="sxs-lookup"><span data-stu-id="bbbae-120">relativeAddress</span></span>|<span data-ttu-id="bbbae-121">Relativní adresa v rámci aktuální aplikace služby IIS – například "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="bbbae-121">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="bbbae-122">V WCF 4,0 tato relativní adresa musí obsahovat jednu ze známých přípon souborů (. svc,. xamlx,...). Neexistuje žádný fyzický soubor pro relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="bbbae-122">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bbbae-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bbbae-123">Child Elements</span></span>

<span data-ttu-id="bbbae-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="bbbae-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbbae-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bbbae-125">Parent Elements</span></span>

|<span data-ttu-id="bbbae-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="bbbae-126">Element</span></span>|<span data-ttu-id="bbbae-127">Popis</span><span class="sxs-lookup"><span data-stu-id="bbbae-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbbae-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="bbbae-128">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="bbbae-129">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="bbbae-129">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bbbae-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbbae-130">Remarks</span></span>

<span data-ttu-id="bbbae-131">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="bbbae-131">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="bbbae-132">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="bbbae-132">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="bbbae-133">Všimněte si `<serviceHostingEnvironment>` , že je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbbae-133">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="bbbae-134">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbbae-134">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="bbbae-135">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="bbbae-135">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="bbbae-136">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bbbae-136">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="bbbae-137">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbbae-137">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="bbbae-138">Vyžaduje rozšíření v adresa relativeAddress, tj. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="bbbae-138">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="bbbae-139">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="bbbae-139">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="bbbae-140">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="bbbae-140">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbbae-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbbae-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
