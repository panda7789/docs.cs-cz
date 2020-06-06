---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850328"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="f1bf4-102">\<add> z \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="f1bf4-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="f1bf4-103">Prvek konfigurace, který umožňuje definovat nastavení aktivace virtuální služby, která se mapují na typy služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f1bf4-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="f1bf4-104">Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="f1bf4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1bf4-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1bf4-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1bf4-106">Attributes and Elements</span></span>

<span data-ttu-id="f1bf4-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1bf4-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1bf4-108">Attributes</span></span>

|<span data-ttu-id="f1bf4-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1bf4-109">Attribute</span></span>|<span data-ttu-id="f1bf4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f1bf4-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f1bf4-111">instalací</span><span class="sxs-lookup"><span data-stu-id="f1bf4-111">factory</span></span>|<span data-ttu-id="f1bf4-112">Řetězec, který určuje název typu CLR továrny, která generuje prvek aktivace služby.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="f1bf4-113">služba</span><span class="sxs-lookup"><span data-stu-id="f1bf4-113">service</span></span>|<span data-ttu-id="f1bf4-114">ServiceType, který implementuje službu (buď plně kvalifikovaný typeName, nebo krátký TypeName (při umístění do složky App_Code).</span><span class="sxs-lookup"><span data-stu-id="f1bf4-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="f1bf4-115">Adresa relativeAddress</span><span class="sxs-lookup"><span data-stu-id="f1bf4-115">relativeAddress</span></span>|<span data-ttu-id="f1bf4-116">Relativní adresa v rámci aktuální aplikace služby IIS – například "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="f1bf4-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="f1bf4-117">V WCF 4,0 tato relativní adresa musí obsahovat jednu ze známých přípon souborů (. svc,. xamlx,...). Neexistuje žádný fyzický soubor pro relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f1bf4-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1bf4-118">Child Elements</span></span>

<span data-ttu-id="f1bf4-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1bf4-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1bf4-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1bf4-120">Parent Elements</span></span>

|<span data-ttu-id="f1bf4-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1bf4-121">Element</span></span>|<span data-ttu-id="f1bf4-122">Description</span><span class="sxs-lookup"><span data-stu-id="f1bf4-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="f1bf4-123">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f1bf4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1bf4-124">Remarks</span></span>

<span data-ttu-id="f1bf4-125">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="f1bf4-126">Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="f1bf4-127">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f1bf4-128">Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f1bf4-129">Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="f1bf4-130">Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="f1bf4-131">Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f1bf4-132">Vyžaduje rozšíření v adresa relativeAddress, tj.. svc,. XOML nebo. xamlx.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f1bf4-133">Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f1bf4-134">Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.</span><span class="sxs-lookup"><span data-stu-id="f1bf4-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1bf4-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1bf4-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
