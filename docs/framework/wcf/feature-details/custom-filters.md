---
title: Vlastní filtry
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185214"
---
# <a name="custom-filters"></a><span data-ttu-id="11b67-102">Vlastní filtry</span><span class="sxs-lookup"><span data-stu-id="11b67-102">Custom Filters</span></span>
<span data-ttu-id="11b67-103">Vlastní filtry umožňují definovat odpovídající logiku, kterou nelze provést pomocí filtrů zpráv poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="11b67-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="11b67-104">Můžete například vytvořit vlastní filtr, který zařazuje hodnotu hash určitého prvku zprávy a poté zkontroluje hodnotu, která určí, zda má filtr vrátit hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="11b67-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="11b67-105">Implementace</span><span class="sxs-lookup"><span data-stu-id="11b67-105">Implementation</span></span>  
 <span data-ttu-id="11b67-106">Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třídy.</span><span class="sxs-lookup"><span data-stu-id="11b67-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="11b67-107">Při implementaci vlastního filtru může konstruktor volitelně přijmout jeden parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="11b67-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="11b67-108">Tento parametr obsahuje informace o konfiguraci, která je předána konstruktoru MessageFilter za účelem poskytnutí všech hodnot nebo konfigurace, které filtr potřebuje za běhu, aby bylo možné provádět shody.</span><span class="sxs-lookup"><span data-stu-id="11b67-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="11b67-109">To může být například použit k poskytnutí hodnoty, kterou filtr hledá v rámci vyhodnocované zprávy.</span><span class="sxs-lookup"><span data-stu-id="11b67-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="11b67-110">Následující příklad ukazuje základní implementaci filtru vlastní zprávy, který přijímá parametr řetězce:</span><span class="sxs-lookup"><span data-stu-id="11b67-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
> <span data-ttu-id="11b67-111">Ve skutečné implementaci Match metody obsahuje logiku, která bude zkoumat zprávu k určení, pokud tento filtr zprávy by měl vrátit **true** nebo **false**.</span><span class="sxs-lookup"><span data-stu-id="11b67-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="11b67-112">Výkon</span><span class="sxs-lookup"><span data-stu-id="11b67-112">Performance</span></span>  
 <span data-ttu-id="11b67-113">Při implementaci vlastního filtru je důležité vzít v úvahu maximální dobu potřebnou k dokončení vyhodnocení zprávy filtrem.</span><span class="sxs-lookup"><span data-stu-id="11b67-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="11b67-114">Vzhledem k tomu, že zpráva může být vyhodnocena proti více filtrů před nalezením shody, je důležité zajistit, že požadavek klienta není časový plán před všechny filtry mohou být vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="11b67-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="11b67-115">Vlastní filtr by proto měl obsahovat pouze kód potřebný k vyhodnocení obsahu nebo atributů zprávy, aby bylo možné určit, zda odpovídá kritériím filtru.</span><span class="sxs-lookup"><span data-stu-id="11b67-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="11b67-116">Obecně byste se měli vyhnout následujícím při implementaci vlastního filtru:</span><span class="sxs-lookup"><span data-stu-id="11b67-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="11b67-117">IO, jako je například ukládání dat na disk nebo do databáze.</span><span class="sxs-lookup"><span data-stu-id="11b67-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="11b67-118">Zbytečné zpracování, jako je například opakování více záznamů v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11b67-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="11b67-119">Blokování operací, jako jsou například volání, které zahrnují získání zámku na sdílené prostředky nebo provádění vyhledávání proti databázi.</span><span class="sxs-lookup"><span data-stu-id="11b67-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="11b67-120">Před použitím vlastního filtru v provozním prostředí byste měli spustit testy výkonu, abyste určili průměrnou dobu, po kterou filtr vyhodnocuje zprávu.</span><span class="sxs-lookup"><span data-stu-id="11b67-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="11b67-121">V kombinaci s průměrnou dobou zpracování ostatních filtrů použitých v tabulce filtrů to umožní přesně určit maximální hodnotu časového limitu, která by měla být určena klientskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="11b67-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="11b67-122">Využití</span><span class="sxs-lookup"><span data-stu-id="11b67-122">Usage</span></span>  
 <span data-ttu-id="11b67-123">Chcete-li použít vlastní filtr se službou Směrování, musíte jej přidat do tabulky filtrů zadáním nové položky filtru typu Vlastní, plně kvalifikovaného názvu typu filtru zprávy a názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="11b67-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="11b67-124">Stejně jako u jiných MessageFilters, můžete zadat řetězec filterData, který bude předán konstruktoru vlastního filtru.</span><span class="sxs-lookup"><span data-stu-id="11b67-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="11b67-125">Následující příklady ukazují použití vlastního filtru se službou Směrování:</span><span class="sxs-lookup"><span data-stu-id="11b67-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
