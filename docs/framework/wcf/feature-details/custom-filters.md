---
title: Vlastní filtry
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 9ef94d95737fb743af56f411bcc0f39ceea679a0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912689"
---
# <a name="custom-filters"></a><span data-ttu-id="dfc62-102">Vlastní filtry</span><span class="sxs-lookup"><span data-stu-id="dfc62-102">Custom Filters</span></span>
<span data-ttu-id="dfc62-103">Vlastní filtry umožňují definovat odpovídající logiku, která nelze provést pomocí zprávy poskytnuté systémem filtry.</span><span class="sxs-lookup"><span data-stu-id="dfc62-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="dfc62-104">Například může vytvořit vlastní filtr, který hashuje prvek konkrétní zprávy a poté zkontroluje hodnotu k určení, zda filtr by měl vrátit hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="dfc62-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="dfc62-105">Implementace</span><span class="sxs-lookup"><span data-stu-id="dfc62-105">Implementation</span></span>  
 <span data-ttu-id="dfc62-106">Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třída.</span><span class="sxs-lookup"><span data-stu-id="dfc62-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="dfc62-107">Při implementaci vlastní filtr, konstruktor může volitelně přijmout jako parametr jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="dfc62-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="dfc62-108">Tento parametr obsahuje informace o konfiguraci, který je předán konstruktoru MessageFilter negace, odpovídá všechny hodnoty nebo konfiguraci, kterou filtr musí za běhu, aby bylo možné provést.</span><span class="sxs-lookup"><span data-stu-id="dfc62-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="dfc62-109">Například to může být použije zadejte hodnotu, která filtr hledá v rámci zprávy právě vyhodnocována.</span><span class="sxs-lookup"><span data-stu-id="dfc62-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="dfc62-110">Následující příklad ukazuje základní implementaci filtru vlastní zprávu, která přijímá řetězcový parametr:</span><span class="sxs-lookup"><span data-stu-id="dfc62-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
>  <span data-ttu-id="dfc62-111">Ve skutečné implementaci, obsahuje alespoň jednu metodu porovnání logiku, která se zaměřuje zpráva, kterou chcete určit, pokud by měla vrátit tomuto filtru zprávy **true** nebo **false**.</span><span class="sxs-lookup"><span data-stu-id="dfc62-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="dfc62-112">Výkon</span><span class="sxs-lookup"><span data-stu-id="dfc62-112">Performance</span></span>  
 <span data-ttu-id="dfc62-113">Při implementaci vlastního filtru, je potřeba vzít v úvahu delší dobu potřebnou pro filtr k vyzkoušení zprávu.</span><span class="sxs-lookup"><span data-stu-id="dfc62-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="dfc62-114">Vzhledem k tomu, že zpráva může být porovnán s více filtrů, předtím, než je nalezena shoda, je důležité zajistit, že žádost klienta nemá časový limit před vyhodnocením všechny filtry.</span><span class="sxs-lookup"><span data-stu-id="dfc62-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="dfc62-115">Vlastní filtr proto by měl obsahovat pouze kódu potřebného k vyhodnocení obsahu nebo atributů zprávu, aby bylo možné zjistit, jestli odpovídá kritéria filtru.</span><span class="sxs-lookup"><span data-stu-id="dfc62-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="dfc62-116">Obecně byste se měli vyhnout následující při implementaci vlastního filtru:</span><span class="sxs-lookup"><span data-stu-id="dfc62-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="dfc62-117">Vstupně-výstupních operací, jako je ukládání dat na disk nebo do databáze.</span><span class="sxs-lookup"><span data-stu-id="dfc62-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="dfc62-118">Nepotřebná zpracování, např. opakování ve smyčce přes více záznamů v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dfc62-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="dfc62-119">Blokovat operace, jako je volání, které se týkají získání zámku na sdílených prostředků nebo vyhledávání proti databázi.</span><span class="sxs-lookup"><span data-stu-id="dfc62-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="dfc62-120">Před použitím vlastního filtru v provozním prostředí, byste provést testy výkonu k určení průměrnou dobu filtru trvá vyhodnotit zprávu.</span><span class="sxs-lookup"><span data-stu-id="dfc62-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="dfc62-121">V kombinaci s Průměrná doba zpracování jiných filtry použité v tabulce filtrů, to umožní vám přesně určit maximální hodnotu časového limitu, který by měl být určeno klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="dfc62-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="dfc62-122">Použití</span><span class="sxs-lookup"><span data-stu-id="dfc62-122">Usage</span></span>  
 <span data-ttu-id="dfc62-123">Pokud chcete používat vlastní filtr službou směrování, je třeba přidat ji do tabulky filtru tak, že zadáte novou položku Filtr typu "Vlastní" název plně kvalifikovaný typ filtru zpráv a název vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfc62-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="dfc62-124">Stejně jako u jiných MessageFilters, můžete zadat řetězec fulltextových dat filtru, která bude předána do konstruktoru vlastního filtru.</span><span class="sxs-lookup"><span data-stu-id="dfc62-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="dfc62-125">Následující příklady ukazují použití vlastního filtru se službou směrování:</span><span class="sxs-lookup"><span data-stu-id="dfc62-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
