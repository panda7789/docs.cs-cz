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
# <a name="custom-filters"></a>Vlastní filtry
Vlastní filtry umožňují definovat odpovídající logiku, kterou nelze provést pomocí filtrů zpráv poskytovaných systémem. Můžete například vytvořit vlastní filtr, který zařazuje hodnotu hash určitého prvku zprávy a poté zkontroluje hodnotu, která určí, zda má filtr vrátit hodnotu true nebo false.  
  
## <a name="implementation"></a>Implementace  
 Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třídy. Při implementaci vlastního filtru může konstruktor volitelně přijmout jeden parametr řetězce. Tento parametr obsahuje informace o konfiguraci, která je předána konstruktoru MessageFilter za účelem poskytnutí všech hodnot nebo konfigurace, které filtr potřebuje za běhu, aby bylo možné provádět shody. To může být například použit k poskytnutí hodnoty, kterou filtr hledá v rámci vyhodnocované zprávy. Následující příklad ukazuje základní implementaci filtru vlastní zprávy, který přijímá parametr řetězce:  
  
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
> Ve skutečné implementaci Match metody obsahuje logiku, která bude zkoumat zprávu k určení, pokud tento filtr zprávy by měl vrátit **true** nebo **false**.  
  
### <a name="performance"></a>Výkon  
 Při implementaci vlastního filtru je důležité vzít v úvahu maximální dobu potřebnou k dokončení vyhodnocení zprávy filtrem. Vzhledem k tomu, že zpráva může být vyhodnocena proti více filtrů před nalezením shody, je důležité zajistit, že požadavek klienta není časový plán před všechny filtry mohou být vyhodnoceny. Vlastní filtr by proto měl obsahovat pouze kód potřebný k vyhodnocení obsahu nebo atributů zprávy, aby bylo možné určit, zda odpovídá kritériím filtru.  
  
 Obecně byste se měli vyhnout následujícím při implementaci vlastního filtru:  
  
- IO, jako je například ukládání dat na disk nebo do databáze.  
  
- Zbytečné zpracování, jako je například opakování více záznamů v dokumentu.  
  
- Blokování operací, jako jsou například volání, které zahrnují získání zámku na sdílené prostředky nebo provádění vyhledávání proti databázi.  
  
 Před použitím vlastního filtru v provozním prostředí byste měli spustit testy výkonu, abyste určili průměrnou dobu, po kterou filtr vyhodnocuje zprávu. V kombinaci s průměrnou dobou zpracování ostatních filtrů použitých v tabulce filtrů to umožní přesně určit maximální hodnotu časového limitu, která by měla být určena klientskou aplikací.  
  
## <a name="usage"></a>Využití  
 Chcete-li použít vlastní filtr se službou Směrování, musíte jej přidat do tabulky filtrů zadáním nové položky filtru typu Vlastní, plně kvalifikovaného názvu typu filtru zprávy a názvu sestavení.  Stejně jako u jiných MessageFilters, můžete zadat řetězec filterData, který bude předán konstruktoru vlastního filtru.  
  
 Následující příklady ukazují použití vlastního filtru se službou Směrování:  
  
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
