---
title: Vlastní filtry
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ade387524c9ca6c8ef337ccf6a5b3453b7df976b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945368"
---
# <a name="custom-filters"></a><span data-ttu-id="cf124-102">Vlastní filtry</span><span class="sxs-lookup"><span data-stu-id="cf124-102">Custom Filters</span></span>
<span data-ttu-id="cf124-103">Vlastní filtry umožňují definovat odpovídající logiku, kterou nelze provést pomocí filtrů zpráv poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="cf124-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="cf124-104">Můžete například vytvořit vlastní filtr, který určí hodnotu hash konkrétního prvku zprávy, a poté ověří hodnotu, zda filtr má vrátit hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="cf124-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="cf124-105">Implementace</span><span class="sxs-lookup"><span data-stu-id="cf124-105">Implementation</span></span>  
 <span data-ttu-id="cf124-106">Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třídy.</span><span class="sxs-lookup"><span data-stu-id="cf124-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="cf124-107">Při implementaci vlastního filtru může konstruktor volitelně přijmout jeden řetězcový parametr.</span><span class="sxs-lookup"><span data-stu-id="cf124-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="cf124-108">Tento parametr obsahuje konfigurační informace, které jsou předány konstruktoru MessageFilter, aby bylo možné zadat jakékoli hodnoty nebo konfiguraci, které filtr potřebuje za běhu, aby bylo možné provést shodu.</span><span class="sxs-lookup"><span data-stu-id="cf124-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="cf124-109">Můžete to například použít k poskytnutí hodnoty, kterou filtr vyhledává v rámci hodnocené zprávy.</span><span class="sxs-lookup"><span data-stu-id="cf124-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="cf124-110">Následující příklad ukazuje základní implementaci vlastního filtru zpráv, který přijímá řetězcový parametr:</span><span class="sxs-lookup"><span data-stu-id="cf124-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="cf124-111">V samotné implementaci metody shody obsahují logiku, která prověřuje zprávu, aby zjistila, zda by filtr zpráv měl vracet **hodnotu true** nebo **false**.</span><span class="sxs-lookup"><span data-stu-id="cf124-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="cf124-112">Výkon</span><span class="sxs-lookup"><span data-stu-id="cf124-112">Performance</span></span>  
 <span data-ttu-id="cf124-113">Při implementaci vlastního filtru je důležité vzít v úvahu maximální dobu potřebnou k tomu, aby filtr dokončil vyhodnocení zprávy.</span><span class="sxs-lookup"><span data-stu-id="cf124-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="cf124-114">Vzhledem k tomu, že může být zpráva vyhodnocena proti více filtrům před nalezením shody, je důležité zajistit, aby žádost klienta neuplynula časový limit před tím, než bude možné vyhodnotit všechny filtry.</span><span class="sxs-lookup"><span data-stu-id="cf124-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="cf124-115">Vlastní filtr proto by měl obsahovat pouze kód, který je nezbytný k vyhodnocení obsahu nebo atributů zprávy, aby bylo možné zjistit, zda odpovídá kritériím filtru.</span><span class="sxs-lookup"><span data-stu-id="cf124-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="cf124-116">Obecně platí, že při implementaci vlastního filtru byste se měli vyhnout následujícímu:</span><span class="sxs-lookup"><span data-stu-id="cf124-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="cf124-117">Vstupně-výstupní operace, například ukládání dat na disk nebo do databáze.</span><span class="sxs-lookup"><span data-stu-id="cf124-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="cf124-118">Nepotřebné zpracování, jako je například opakování několika záznamů v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cf124-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="cf124-119">Blokování operací, například volání, která zahrnují získání zámku sdílených prostředků nebo provádění vyhledávání v databázi.</span><span class="sxs-lookup"><span data-stu-id="cf124-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="cf124-120">Před použitím vlastního filtru v produkčním prostředí byste měli spustit testy výkonu a určit tak průměrnou dobu, kterou filtr provede k vyhodnocení zprávy.</span><span class="sxs-lookup"><span data-stu-id="cf124-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="cf124-121">V kombinaci s průměrnou dobou zpracování dalších filtrů použitých v tabulce filtru vám to umožní přesně určit maximální hodnotu časového limitu, která by měla být určena klientskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="cf124-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="cf124-122">Použití</span><span class="sxs-lookup"><span data-stu-id="cf124-122">Usage</span></span>  
 <span data-ttu-id="cf124-123">Aby bylo možné používat vlastní filtr s směrovací službou, je nutné jej přidat do tabulky filtru zadáním nové položky filtru typu "vlastní", plně kvalifikovaného názvu typu filtru zprávy a názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="cf124-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="cf124-124">Stejně jako u jiných MessageFilters můžete zadat řetězec fulltextových, který bude předán konstruktoru vlastního filtru.</span><span class="sxs-lookup"><span data-stu-id="cf124-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="cf124-125">Následující příklady ukazují použití vlastního filtru se směrovací službou:</span><span class="sxs-lookup"><span data-stu-id="cf124-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
