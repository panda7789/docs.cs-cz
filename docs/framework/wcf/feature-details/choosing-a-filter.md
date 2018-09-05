---
title: Výběr filtru
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: bc3bba9a2b00b35f3e0cff1786ea98cfa881f311
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743138"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="1f9d2-102">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="1f9d2-102">Choosing a Filter</span></span>
<span data-ttu-id="1f9d2-103">Při konfiguraci služby směrování, je důležité vybrat správnou zprávu filtry a nakonfigurujete je, aby bylo možné provést přesné shody proti přijímaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="1f9d2-104">Pokud filtry, které jste vybrali příliš rozsáhlá v jejich odpovídá nebo jsou nakonfigurovány nesprávně, zprávy jsou směrovány nesprávně.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="1f9d2-105">Pokud jsou příliš omezující filtry, pravděpodobně nemáte všechny platné trasy, které jsou k dispozici pro některé zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="1f9d2-106">Typy filtrů</span><span class="sxs-lookup"><span data-stu-id="1f9d2-106">Filter Types</span></span>  
 <span data-ttu-id="1f9d2-107">Při výběru filtry, které používá služba směrování, je důležité pochopit, jak každý filtr funguje a jaké informace jsou k dispozici jako součást příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="1f9d2-108">Například pokud jsou všechny zprávy přes stejný koncový bod, filtry adres a Název_koncového_bodu nejsou užitečné protože těmto filtrům neodpovídají všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="1f9d2-109">Akce</span><span class="sxs-lookup"><span data-stu-id="1f9d2-109">Action</span></span>  
 <span data-ttu-id="1f9d2-110">Zkontroluje filtr akce <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="1f9d2-111">Pokud obsah záhlaví akce ve zprávě odpovídají hodnotě dat filtru zadaná v konfiguraci filtr a potom tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1f9d2-112">Následující příklad definuje `FilterElement` filtru akce, která používá tak, aby odpovídaly zprávy s hlavičkou akce, která obsahuje hodnotu "http://namespace/contract/operation/".</span><span class="sxs-lookup"><span data-stu-id="1f9d2-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of "http://namespace/contract/operation/".</span></span>  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="1f9d2-113">Tento filtr by měla sloužit při směrování zpráv, které obsahují jedinečné záhlaví akce.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="1f9d2-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="1f9d2-114">EndpointAddress</span></span>  
 <span data-ttu-id="1f9d2-115">Filtr EndpointAddress kontroluje EndpointAddress, který v byla přijata zpráva.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1f9d2-116">Pokud na adresu, kterou se zpráva dorazí na přesně odpovídá adrese filtr zadaný v konfiguraci filtr a potom tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1f9d2-117">Následující příklad definuje `FilterElement` , která používá filtr adres tak, aby odpovídaly všechny zprávy adresované na "http://\<název_hostitele > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="1f9d2-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1f9d2-118">Je důležité si uvědomit, že část názvu hostitele adresy se může lišit podle toho, zda klient používá plně kvalifikovaný název domény, název NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1f9d2-119">Protože různé hodnoty mohou odkazovat na stejného hostitele, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění shody.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="1f9d2-120">Toto chování lze upravit umožňující porovnání k vyhodnocení názvu hostitele, při konfiguraci služby směrování prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="1f9d2-121">Tento filtr by měla sloužit, když jsou příchozí zprávy adresované jedinečnou adresu.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="1f9d2-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="1f9d2-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="1f9d2-123">Filtr EndpointAddressPrefix je podobný filtrování EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="1f9d2-124">Filtr EndpointAddressPrefix kontroluje EndpointAddress, který v byla přijata zpráva.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1f9d2-125">Ale EndpointAddressPrefix filtr funguje jako zástupný znak to provede spárováním odpovídajících adresy, které začínají hodnotu zadanou v konfiguraci filtru.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="1f9d2-126">Následující příklad definuje `FilterElement` EndpointAddressPrefix filtr, který používá tak, aby odpovídaly všechny zprávy adresované na "http://\<název_hostitele > / vdir \*".</span><span class="sxs-lookup"><span data-stu-id="1f9d2-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to "http://\<hostname>/vdir\*".</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1f9d2-127">Je důležité si uvědomit, že část názvu hostitele adresy se může lišit podle toho, zda klient používá plně kvalifikovaný název domény, název NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1f9d2-128">Protože různé hodnoty mohou odkazovat na stejného hostitele, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění shody.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="1f9d2-129">Tento filtr by měla sloužit při směrování příchozích zpráv, které sdílejí běžnou předponu adresy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="1f9d2-130">AND</span><span class="sxs-lookup"><span data-stu-id="1f9d2-130">AND</span></span>  
 <span data-ttu-id="1f9d2-131">Filtr a nefiltruje přímo na základě hodnot v rámci zprávy, ale můžete kombinovat dva filtry k vytvoření `AND` kde oba filtry musí odpovídat zprávu před vyhodnotí jako filtr a podmínka `true`.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="1f9d2-132">To umožňuje vytvořit komplexní filtry, které odpovídá pouze pokud se shodují všechny dílčí filtry.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="1f9d2-133">Následující příklad definuje filtr adresy a filtru akce a pak definuje filtr a, který se vyhodnotí zprávu před filtry adresu a akce.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="1f9d2-134">Pokud adresu a filtrů Akce shodují, pak filtr a vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
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
  
 <span data-ttu-id="1f9d2-135">Tento filtr by měla sloužit, když zkombinujete musí logiku z více filtrů k určení, kdy je třeba shodu.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="1f9d2-136">Například pokud máte více cílů, které musí přijmout jenom určité kombinace akcí a zprávy pro konkrétní adresy, můžete použít filtr a potřebné akce a adresu filtry zkombinovat.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="1f9d2-137">Vlastní</span><span class="sxs-lookup"><span data-stu-id="1f9d2-137">Custom</span></span>  
 <span data-ttu-id="1f9d2-138">Když vyberete vlastní typ filtru, je nutné zadat customtype – hodnota, která obsahuje typ, který obsahuje sestavení **MessageFilter** implementace má být použit pro tento filtr.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="1f9d2-139">Kromě toho fulltextových dat filtru musí obsahovat všechny hodnoty, které vlastní filtr může vyžadovat jeho vyhodnocení zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="1f9d2-140">Následující příklad definuje `FilterElement` , která používá `CustomAssembly.MyCustomMsgFilter` MessageFilter implementace.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="1f9d2-141">Pokud je potřeba provést vlastní logiku odpovídající proti zprávu, která není předmětem filtry, opatřeného [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], musíte vytvořit vlastní filtr, který je implementace **MessageFilter** třídy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="1f9d2-142">Například může vytvořit vlastní filtr, který porovnává pole v příchozí zprávě seznam se známými hodnot na základě předané do filtru jako konfigurace, nebo se hashuje prvek konkrétní zprávy a zkontroluje tuto hodnotu k určení, zda filtr by měla vrátit `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="1f9d2-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="1f9d2-143">EndpointName</span></span>  
 <span data-ttu-id="1f9d2-144">Filtr Název_koncového_bodu kontroluje název koncového bodu, která se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="1f9d2-145">Následující příklad definuje `FilterElement` , který využívá filtr Název_koncového_bodu pro směrování zpráv byla přijata na "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="1f9d2-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="1f9d2-146">Tento filtr je užitečný při směrovací služba poskytuje více než jeden koncový bod s názvem služby.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="1f9d2-147">Například může zveřejnit dva koncové body, které směrovací služba používá pro příjem zprávy. jeden používá priority zákazníci, kteří požadují zpracování jejich zpráv při jiný koncový bod v reálném čase přijímá zprávy, které nejsou citlivé na čas.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="1f9d2-148">I když můžete často použít úplnou adresu odpovídající k určení koncového bodu byla přijata zpráva, místo toho použít název definovaný koncový bod je pohodlný zástupce, který je často nižší náchylné k chybám, zejména při konfiguraci pomocí konfigurace služby Směrování soubor (kde názvy koncových bodů se požadovaný atribut).</span><span class="sxs-lookup"><span data-stu-id="1f9d2-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="1f9d2-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="1f9d2-149">MatchAll</span></span>  
 <span data-ttu-id="1f9d2-150">MatchAll filtr hledá shodu ve všech přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="1f9d2-151">To je užitečné, pokud všechny přijaté zprávy musí vždy směrovat do určitého koncového bodu, jako je například protokolování služby, která ukládá jejich kopii všechny přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="1f9d2-152">Následující příklad definuje `FilterElement` , která používá MatchAll filtru.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="1f9d2-153">XPath</span><span class="sxs-lookup"><span data-stu-id="1f9d2-153">XPath</span></span>  
 <span data-ttu-id="1f9d2-154">Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole určitého prvku zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="1f9d2-155">Filtrování XPath je efektivní filtrování možnost, která umožňuje přímo zkontrolovat všechny adresovatelný položky XML do zprávy. ale vyžaduje, že máte specifické znalosti struktury zprávy, které jste dostali.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="1f9d2-156">Následující příklad definuje `FilterElement` filtr XPath, který používá ke kontrole zprávu pro element s názvem "element" v rámci oboru názvů odkazuje předponu oboru názvů "ns".</span><span class="sxs-lookup"><span data-stu-id="1f9d2-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="1f9d2-157">Tento filtr je užitečný, pokud víte, že zprávy, které jste obdrželi, obsahují určitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="1f9d2-158">Pokud hostujete dvě verze stejné služby a víte, že zprávy adresované na novější verzi služby obsahují jedinečnou hodnotu ve vlastní hlavičce, je třeba vytvořit filtr, který používá výraz XPath pro navigaci k této hlavičce a porovnává hodnotu stisknutím ent v záhlaví na jiný zadaný v konfiguraci filtr k určení, jestli tento filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="1f9d2-159">Protože dotazy XPath často obsahovat jedinečný obory názvů, které jsou často dlouhé nebo komplexní řetězcové hodnoty filtr XPath vám umožní definovat jedinečný předpony pro obory názvů pomocí oboru názvů tabulky.</span><span class="sxs-lookup"><span data-stu-id="1f9d2-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="1f9d2-160">Další informace o tabulce obor názvů, naleznete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="1f9d2-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="1f9d2-161">Další informace o navrhování dotazů XPath, naleznete v tématu [syntaxi XPath](https://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="1f9d2-161">For more information about designing XPath queries, see [XPath Syntax](https://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9d2-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f9d2-162">See Also</span></span>  
 [<span data-ttu-id="1f9d2-163">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="1f9d2-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="1f9d2-164">Postupy: Používání filtrů</span><span class="sxs-lookup"><span data-stu-id="1f9d2-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
