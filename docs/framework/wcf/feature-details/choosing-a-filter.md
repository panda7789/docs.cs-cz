---
title: Výběr filtru
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 282f6e9e2bc986feee0d1825ee9d87217d453e50
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964816"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="ea813-102">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="ea813-102">Choosing a Filter</span></span>
<span data-ttu-id="ea813-103">Při konfiguraci směrovací služby je důležité vybrat správné filtry zpráv a nakonfigurovat je tak, aby vám umožnily přesně odpovídat na zprávy, které obdržíte.</span><span class="sxs-lookup"><span data-stu-id="ea813-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="ea813-104">Pokud jsou filtry, které vyberete, příliš široké v jejich shodách nebo jsou nesprávně nakonfigurované, zprávy se nesprávně směrují.</span><span class="sxs-lookup"><span data-stu-id="ea813-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="ea813-105">Pokud jsou filtry příliš omezující, nemusí být pro některé z vašich zpráv k dispozici žádné platné trasy.</span><span class="sxs-lookup"><span data-stu-id="ea813-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="ea813-106">Typy filtrů</span><span class="sxs-lookup"><span data-stu-id="ea813-106">Filter Types</span></span>

<span data-ttu-id="ea813-107">Když vyberete filtry, které služba Směrování používá, je důležité pochopit, jak každý filtr funguje, a jaké informace jsou k dispozici jako součást příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="ea813-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="ea813-108">Pokud jsou například všechny zprávy přijímány přes stejný koncový bod, nejsou filtry adresa a koncový bod užitečné, protože všechny zprávy odpovídají těmto filtrům.</span><span class="sxs-lookup"><span data-stu-id="ea813-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="ea813-109">Akce</span><span class="sxs-lookup"><span data-stu-id="ea813-109">Action</span></span>

<span data-ttu-id="ea813-110">Filtr akcí kontroluje vlastnost <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea813-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="ea813-111">Pokud se obsah záhlaví akce ve zprávě shoduje s hodnotou dat filtru zadanou v konfiguraci filtru, pak tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="ea813-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="ea813-112">Následující příklad definuje `FilterElement`, který používá filtr akcí, aby odpovídal zprávám s hlavičkou akce, která obsahuje hodnotu `http://namespace/contract/operation/`.</span><span class="sxs-lookup"><span data-stu-id="ea813-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="ea813-113">Tento filtr by měl být použit při směrování zpráv, které obsahují jedinečnou hlavičku akce.</span><span class="sxs-lookup"><span data-stu-id="ea813-113">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="ea813-114">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea813-114">EndpointAddress</span></span>

<span data-ttu-id="ea813-115">Filtr EndpointAddress zkontroluje adresu EndpointAddress, na které byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="ea813-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="ea813-116">Pokud adresa, kterou zpráva dorazí, přesně odpovídá adrese filtru zadané v konfiguraci filtru, pak tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="ea813-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="ea813-117">V následujícím příkladu je definován `FilterElement`, který používá filtr adres, aby odpovídal všem zprávám, které jsou adresovány "http://\<hostname >/vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="ea813-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="ea813-118">Je důležité si uvědomit, že část s názvem hostitele v adrese se může lišit v závislosti na tom, zda klient používá plně kvalifikovaný název domény, název rozhraní NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="ea813-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="ea813-119">Vzhledem k tomu, že rozdílné hodnoty mohou odkazovat na stejného hostitele, výchozí chování pro toto porovnání není použití části názvu hostitele v této adrese při provádění shody.</span><span class="sxs-lookup"><span data-stu-id="ea813-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="ea813-120">Toto chování je možné upravit, aby při programové konfiguraci směrovací služby bylo porovnání vyhodnoceno jako název hostitele.</span><span class="sxs-lookup"><span data-stu-id="ea813-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="ea813-121">Tento filtr by měl být použit při adresování příchozích zpráv na jedinečnou adresu.</span><span class="sxs-lookup"><span data-stu-id="ea813-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="ea813-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="ea813-122">EndpointAddressPrefix</span></span>

<span data-ttu-id="ea813-123">Filtr EndpointAddressPrefix se podobá filtru EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="ea813-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="ea813-124">Filtr EndpointAddressPrefix zkontroluje adresu EndpointAddress, na které byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="ea813-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="ea813-125">Filtr EndpointAddressPrefix ale funguje jako zástupný znak odpovídajícími adresami, které začínají hodnotou zadanou v konfiguraci filtru.</span><span class="sxs-lookup"><span data-stu-id="ea813-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="ea813-126">Následující příklad definuje `FilterElement`, který používá filtr EndpointAddressPrefix k vyhledání všech zpráv, které jsou adresovány `http://<hostname>/vdir*`.</span><span class="sxs-lookup"><span data-stu-id="ea813-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="ea813-127">Je důležité si uvědomit, že část s názvem hostitele v adrese se může lišit v závislosti na tom, zda klient používá plně kvalifikovaný název domény, název rozhraní NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="ea813-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="ea813-128">Vzhledem k tomu, že rozdílné hodnoty mohou odkazovat na stejného hostitele, výchozí chování pro toto porovnání není použití části názvu hostitele v této adrese při provádění shody.</span><span class="sxs-lookup"><span data-stu-id="ea813-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="ea813-129">Tento filtr by měl být použit při směrování příchozích zpráv, které sdílejí společnou předponu adresy.</span><span class="sxs-lookup"><span data-stu-id="ea813-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="ea813-130">AND</span><span class="sxs-lookup"><span data-stu-id="ea813-130">AND</span></span>

<span data-ttu-id="ea813-131">Filtr AND přímo nefiltruje na hodnotu v rámci zprávy, ale umožňuje kombinovat dva další filtry, aby se vytvořila podmínka `AND`, kde oba filtry musí odpovídat zprávě předtím, než se filtr a vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ea813-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="ea813-132">To vám umožňuje vytvářet komplexní filtry, které se shodují jenom v případě, že se všechny dílčí filtry shodují.</span><span class="sxs-lookup"><span data-stu-id="ea813-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="ea813-133">Následující příklad definuje filtr adresy a filtr akcí a pak definuje filtr a, který vyhodnocuje zprávu proti filtrům adresa a akce.</span><span class="sxs-lookup"><span data-stu-id="ea813-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="ea813-134">Pokud adresa i filtr akce odpovídají, pak filtr a vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="ea813-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

<span data-ttu-id="ea813-135">Tento filtr by měl být použit v případě, že je nutné zkombinovat logiku z více filtrů, aby bylo možné určit, kdy má být provedeno porovnávání.</span><span class="sxs-lookup"><span data-stu-id="ea813-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="ea813-136">Například pokud máte více cílů, které musí přijímat pouze určité kombinace akcí a zpráv pro konkrétní adresy, můžete použít filtr a ke kombinování potřebných filtrů akcí a adres.</span><span class="sxs-lookup"><span data-stu-id="ea813-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="ea813-137">Vlastní</span><span class="sxs-lookup"><span data-stu-id="ea813-137">Custom</span></span>

<span data-ttu-id="ea813-138">Při výběru vlastního typu filtru je nutné zadat hodnotu customType, která obsahuje typ sestavení, které obsahuje implementaci **MessageFilter** , která se má použít pro tento filtr.</span><span class="sxs-lookup"><span data-stu-id="ea813-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="ea813-139">Kromě toho musí fulltextových obsahovat všechny hodnoty, které může vlastní filtr vyžadovat při vyhodnocování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ea813-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="ea813-140">Následující příklad definuje `FilterElement`, který používá implementaci `CustomAssembly.MyCustomMsgFilter` MessageFilter.</span><span class="sxs-lookup"><span data-stu-id="ea813-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="ea813-141">Pokud potřebujete provést vlastní odpovídající logiku proti zprávě, která není pokryta filtry uvedenými v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], je nutné vytvořit vlastní filtr, který je implementací třídy **MessageFilter** .</span><span class="sxs-lookup"><span data-stu-id="ea813-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="ea813-142">Můžete například vytvořit vlastní filtr, který porovná pole v příchozí zprávě se seznamem známých hodnot poskytnutým filtru jako konfigurací, nebo, který určí hodnotu hash konkrétního prvku zprávy, a poté ověří tuto hodnotu, aby určil, zda má filtr vracet `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="ea813-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="ea813-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="ea813-143">EndpointName</span></span>

<span data-ttu-id="ea813-144">Filtr koncového bodu kontroluje název koncového bodu, který zprávu přijal.</span><span class="sxs-lookup"><span data-stu-id="ea813-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="ea813-145">Následující příklad definuje `FilterElement`, který používá filtr koncového bodu ke směrování zpráv přijatých na "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="ea813-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="ea813-146">Tento filtr je užitečný, když směrovací služba zveřejňuje více než jeden pojmenovaný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="ea813-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="ea813-147">Můžete například vystavit dva koncové body, které služba Směrování používá pro příjem zpráv. jednu používá přednostní zákazníci, kteří vyžadují zpracování svých zpráv v reálném čase, zatímco druhý koncový bod přijímá zprávy, které nejsou citlivé na čas.</span><span class="sxs-lookup"><span data-stu-id="ea813-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="ea813-148">I když můžete často použít úplnou spárování adres k určení, který koncový bod přijal zprávu, je místo toho pohodlný zástupce, který je často méně náchylné k chybám, zejména při konfiguraci směrovací služby s použitím konfigurace. soubor (kde jsou požadovány názvy koncových bodů).</span><span class="sxs-lookup"><span data-stu-id="ea813-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="ea813-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="ea813-149">MatchAll</span></span>

<span data-ttu-id="ea813-150">Filtr MatchAll odpovídá jakékoli přijaté zprávě.</span><span class="sxs-lookup"><span data-stu-id="ea813-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="ea813-151">To je užitečné v případě, že musíte vždy směrovat všechny přijaté zprávy do konkrétního koncového bodu, například protokolovací služby, která ukládá kopii všech přijatých zpráv.</span><span class="sxs-lookup"><span data-stu-id="ea813-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="ea813-152">Následující příklad definuje `FilterElement`, který používá filtr MatchAll.</span><span class="sxs-lookup"><span data-stu-id="ea813-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="ea813-153">XPath</span><span class="sxs-lookup"><span data-stu-id="ea813-153">XPath</span></span>

<span data-ttu-id="ea813-154">Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole konkrétního prvku v rámci zprávy.</span><span class="sxs-lookup"><span data-stu-id="ea813-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="ea813-155">Filtrování XPath je výkonné možnosti filtrování, které vám umožní přímo zkontrolovat v rámci zprávy jakoukoli položku, která je schopná adresovat kód XML. vyžaduje ale, abyste měli konkrétní znalosti struktury zpráv, které přijímáte.</span><span class="sxs-lookup"><span data-stu-id="ea813-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="ea813-156">Následující příklad definuje `FilterElement`, který používá filtr XPath ke kontrole zprávy pro element s názvem "element" v oboru názvů, na který odkazuje předpona oboru názvů "NS".</span><span class="sxs-lookup"><span data-stu-id="ea813-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="ea813-157">Tento filtr je užitečný, pokud víte, že zprávy, které přijímáte, obsahují konkrétní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ea813-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="ea813-158">Pokud například používáte dvě verze stejné služby a víte, že zprávy adresované do novější verze služby obsahují ve vlastní hlavičce jedinečnou hodnotu, můžete vytvořit filtr, který používá XPath k přechodu na tuto hlavičku a porovná hodnotu pres. k určení, zda filtr odpovídá, můžete v hlavičce k druhému uvedenému v konfiguraci filtru.</span><span class="sxs-lookup"><span data-stu-id="ea813-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="ea813-159">Vzhledem k tomu, že dotazy XPath často obsahují jedinečné obory názvů, které jsou často dlouhé nebo složité řetězcové hodnoty, umožňuje filtr XPath definovat jedinečné předpony pro vaše obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ea813-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="ea813-160">Další informace o tabulce oboru názvů najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="ea813-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>

<span data-ttu-id="ea813-161">Další informace o návrhu dotazů XPath naleznete v tématu [syntax XPath](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ea813-161">For more information about designing XPath queries, see [XPath Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea813-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea813-162">See also</span></span>

- [<span data-ttu-id="ea813-163">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="ea813-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [<span data-ttu-id="ea813-164">Postupy: Používání filtrů</span><span class="sxs-lookup"><span data-stu-id="ea813-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
