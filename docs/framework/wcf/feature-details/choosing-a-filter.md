---
title: Výběr filtru
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 91b3802217a920ef3eeeccb5c4f85c66afee2430
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494124"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="1a0ca-102">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="1a0ca-102">Choosing a Filter</span></span>
<span data-ttu-id="1a0ca-103">Při konfiguraci služby směrování, je důležité vybrat filtry správné zpráv a nakonfigurovat je pro přesné shody proti zprávy, které vám umožňují.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="1a0ca-104">Pokud filtry, které jste vybrali jsou v jejich odpovídá příliš široké, nebo jsou nesprávně nakonfigurované, zprávy jsou směrovány nesprávně.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="1a0ca-105">Pokud jsou filtry příliš omezující, nemusí mít žádné platné tras, které jsou k dispozici pro některé zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="1a0ca-106">Typy filtrů</span><span class="sxs-lookup"><span data-stu-id="1a0ca-106">Filter Types</span></span>  
 <span data-ttu-id="1a0ca-107">Když vyberete filtry, které používají službu směrování, je důležité pochopit, jak každý filtr funguje a jaké informace jsou k dispozici jako součást příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="1a0ca-108">Například pokud jsou všechny zprávy přes stejný koncový bod, filtry adres a EndpointName nejsou užitečné vzhledem k tomu, že všechny zprávy splňují tyto filtry.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="1a0ca-109">Akce</span><span class="sxs-lookup"><span data-stu-id="1a0ca-109">Action</span></span>  
 <span data-ttu-id="1a0ca-110">Zkontroluje filtr akce <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="1a0ca-111">Pokud obsah hlavičky akce ve zprávě odpovídají hodnotě dat filtru, který je zadaný v konfiguraci filtru, pak tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1a0ca-112">V následujícím příkladu definuje `FilterElement` používající filtr akce tak, aby odpovídaly zprávy s hlavičku akce, která obsahuje hodnotu "http://namespace/contract/operation/".</span><span class="sxs-lookup"><span data-stu-id="1a0ca-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of "http://namespace/contract/operation/".</span></span>  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="1a0ca-113">Tento filtr by měl být použit při směrování zprávy, které obsahují hlavičku jedinečný akce.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="1a0ca-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="1a0ca-114">EndpointAddress</span></span>  
 <span data-ttu-id="1a0ca-115">Filtr EndpointAddress zkontroluje EndpointAddress, která byla přijata zpráva na.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1a0ca-116">Pokud adresu zpráva dorazí na přesně odpovídá adrese filtr zadaný v konfiguraci filtru, pak tento filtr vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1a0ca-117">V následujícím příkladu definuje `FilterElement` používající filtr adres tak, aby odpovídaly všechny zprávy adresované do "http://\<hostname > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="1a0ca-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1a0ca-118">Je důležité si uvědomit, že část názvu hostitele adresy může lišit v závislosti na tom, zda klient používá s plně kvalifikovaným názvem domény, název pro rozhraní NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1a0ca-119">Protože odlišné hodnoty mohou odkazovat na stejném hostiteli, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění odpovídá.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="1a0ca-120">Toto chování můžete upravit tak, aby povolit porovnání vyhodnotit název hostitele, při konfiguraci služby směrování prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="1a0ca-121">Tento filtr by měl být použit při jsou příchozí zprávy adresované jedinečnou adresu.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="1a0ca-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="1a0ca-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="1a0ca-123">Filtr EndpointAddressPrefix je podobná EndpointAddress filtru.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="1a0ca-124">Filtr EndpointAddressPrefix zkontroluje EndpointAddress, která byla přijata zpráva na.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1a0ca-125">Ale filtru EndpointAddressPrefix funguje jako zástupný znak pomocí odpovídajících adresy, které začínají hodnota zadaná v konfiguraci filtru.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="1a0ca-126">V následujícím příkladu definuje `FilterElement` používající EndpointAddressPrefix filtru tak, aby odpovídaly všechny zprávy adresované do "http://\<hostname > / vdir \*".</span><span class="sxs-lookup"><span data-stu-id="1a0ca-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to "http://\<hostname>/vdir\*".</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1a0ca-127">Je důležité si uvědomit, že část názvu hostitele adresy může lišit v závislosti na tom, zda klient používá s plně kvalifikovaným názvem domény, název pro rozhraní NetBIOS, IP adresu nebo jiný název.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1a0ca-128">Protože odlišné hodnoty mohou odkazovat na stejném hostiteli, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění odpovídá.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="1a0ca-129">Tento filtr by měl být použit při směrování příchozích zpráv, které sdílejí společné předpona adresy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="1a0ca-130">AND</span><span class="sxs-lookup"><span data-stu-id="1a0ca-130">AND</span></span>  
 <span data-ttu-id="1a0ca-131">Filtr a nefiltruje přímo na hodnotu ve zprávě, ale umožňuje zkombinovat dva filtry k vytvoření `AND` podmínky, které oba filtry musí se shodovat zprávu a filtru se vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="1a0ca-132">To umožňuje vytváření složitých filtrů, které odpovídá pouze pokud se shodují všechny dílčí filtry.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="1a0ca-133">V následujícím příkladu definuje filtr adres a filtru akce a pak definuje filtr a, která vyhodnotí zprávu před filtry adres i akce.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="1a0ca-134">Pokud adresu a filtrů Akce shodují, pak filtr a vrací `true`.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
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
  
 <span data-ttu-id="1a0ca-135">Tento filtr by měl být použit při musíte kombinovat logiku z více filtrů k určení, kdy má být nalezena shoda k.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="1a0ca-136">Například pokud máte více cílů, které musí obdržet pouze určité kombinace akce a zprávy pro konkrétní adresy, můžete použít filtr a se zkombinovat filtry potřebné akce a adresu.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="1a0ca-137">Vlastní</span><span class="sxs-lookup"><span data-stu-id="1a0ca-137">Custom</span></span>  
 <span data-ttu-id="1a0ca-138">Když vyberete typ filtru vlastní, je nutné zadat hodnotu customType, která obsahuje sestavení, které obsahuje typ **MessageFilter** implementace má být použit pro tento filtr.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="1a0ca-139">Kromě toho fulltextových dat filtru musí obsahovat všechny hodnoty, které vlastní filtr může vyžadovat ohodnocení zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="1a0ca-140">V následujícím příkladu definuje `FilterElement` používající `CustomAssembly.MyCustomMsgFilter` MessageFilter implementace.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="1a0ca-141">Pokud potřebujete provést vlastní logiky odpovídající proti zprávu, která není předmětem filtry součástí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], musíte vytvořit vlastní filtr, který je implementací **MessageFilter** třídy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="1a0ca-142">Například může vytvořit vlastní filtr, který porovnává pole v příchozí zpráva seznam známých hodnot na základě předané filtru jako konfigurace, nebo se rozdělí elementu konkrétní zprávy a poté zkoumá tuto hodnotu určit zda filtr by měla vrátit `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="1a0ca-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="1a0ca-143">EndpointName</span></span>  
 <span data-ttu-id="1a0ca-144">Filtr EndpointName kontroluje název koncového bodu, který se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="1a0ca-145">V následujícím příkladu definuje `FilterElement` používající EndpointName filtru pro směrování zpráv byla přijata "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="1a0ca-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="1a0ca-146">Tento filtr je užitečné, když směrovací služby zpřístupní více než jeden koncový bod s názvem služby.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="1a0ca-147">Například mohou být vystaveny dva koncové body, které služba Směrování se používá pro příjem zpráv; jeden se používá s prioritou zákazníci, kteří vyžadují v reálném čase, zpracování jejich zpráv při jiný koncový bod přijímá zprávy, které nejsou čas velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="1a0ca-148">I když můžete používat často úplná adresa odpovídající k určení kterému koncovému bodu byla přijata zpráva, místo toho použít název koncového bodu definovaného je vhodné zástupce, který je často méně náchylný, zejména v případě, že konfigurace směrování služby pomocí nástroje Konfigurace soubor (kde názvy koncových bodů jsou povinný atribut).</span><span class="sxs-lookup"><span data-stu-id="1a0ca-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="1a0ca-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="1a0ca-149">MatchAll</span></span>  
 <span data-ttu-id="1a0ca-150">Filtr MatchAll odpovídá všechny přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="1a0ca-151">Je vhodné, pokud všechny přijaté zprávy musí vždy směrovat na konkrétní, jako je například služba protokolování, která ukládá kopie všechny přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="1a0ca-152">V následujícím příkladu definuje `FilterElement` používající MatchAll filtru.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="1a0ca-153">XPath</span><span class="sxs-lookup"><span data-stu-id="1a0ca-153">XPath</span></span>  
 <span data-ttu-id="1a0ca-154">Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole určitého prvku zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="1a0ca-155">Filtrování XPath je výkonný filtrování možnost, která umožňuje přímo zkontrolovat všechny XML adresovatelné položky v rámci message; ale vyžaduje, že máte konkrétní znalosti struktury zprávy, které jste obdrželi.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="1a0ca-156">V následujícím příkladu definuje `FilterElement` používající filtr XPath kontrola zprávu pro element s názvem "elementu" v rámci oboru názvů odkazuje Předpona oboru názvů "ns".</span><span class="sxs-lookup"><span data-stu-id="1a0ca-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="1a0ca-157">Tento filtr je užitečné, pokud víte, že zprávy, které jste obdrželi, obsahují konkrétní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="1a0ca-158">Například pokud hostujete dvě verze stejné služby a víte, že zprávy adresované na novější verzi služby obsahovat jedinečnou hodnotu ve vlastní hlavičky, můžete vytvořit filtr, který používá XPath přejděte na tuto hlavičku a porovnává hodnotu stisknutím trola v hlavičce na jiný zadaný v konfiguraci filtr k určení, jestli odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="1a0ca-159">Protože dotazů XPath často obsahují jedinečný obory názvů, které jsou často zdlouhavé nebo komplexní řetězcové hodnoty filtr XPath umožňuje obor názvů tabulku použijte k definování jedinečný předpon pro obory.</span><span class="sxs-lookup"><span data-stu-id="1a0ca-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="1a0ca-160">Další informace o tabulce obor názvů najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="1a0ca-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="1a0ca-161">Další informace o návrhu dotazů XPath najdete v tématu [syntaxe jazyka XPath](http://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="1a0ca-161">For more information about designing XPath queries, see [XPath Syntax](http://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0ca-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a0ca-162">See Also</span></span>  
 [<span data-ttu-id="1a0ca-163">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="1a0ca-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="1a0ca-164">Postupy: Používání filtrů</span><span class="sxs-lookup"><span data-stu-id="1a0ca-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
