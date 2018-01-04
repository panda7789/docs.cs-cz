---
title: "Vlastní filtry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d24e517a8fd63a3363d080ebbabf2c1e3306b76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-filters"></a>Vlastní filtry
Vlastní filtry umožňují definovat odpovídající logiky, která nelze provést pomocí filtrů zpráv systému. Například může vytvořit vlastní filtr, který vytvoří hodnotu hash elementu konkrétní zprávy a poté zkoumá hodnotu, která určí, zda filtr by měla vrátit hodnotu true nebo false.  
  
## <a name="implementation"></a>Implementace  
 Vlastní filtr je implementací <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třída. Při implementaci vlastního filtru, konstruktor může volitelně přijmout parametr jeden řetězec. Tento parametr obsahuje informace o konfiguraci, která předaný konstruktoru MessageFilter Chcete-li poskytovat, že všechny hodnoty nebo konfigurace, která filtr musí za běhu, aby bylo možné provést odpovídá. Například to lze použít pro zadejte hodnotu, která filtr vyhledává ve zprávě vyhodnocovaný. Následující příklad ukazuje základní implementace filtru vlastní zprávu, která přijímá řetězcový parametr:  
  
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
>  V implementaci skutečné metodu nebo metody shodu obsahuje logiku, která bude zkontrolujte zprávy k určení, pokud by měla vrátit tento filtr zpráv **true** nebo **false**.  
  
### <a name="performance"></a>Výkon  
 Při implementaci vlastního filtru, je potřeba vzít v úvahu maximální délku čas potřebný pro filtr k dokončení testování zprávu. Vzhledem k tomu, že zpráva může být porovnán s více filtrů, než je nalezena shoda, je důležité zajistit, že nemá požadavku klienta není vypršení časového limitu před vyhodnocením všechny filtry. Vlastní filtr proto musí obsahovat pouze kód, nutné vyhodnotit obsah nebo atributy zprávy, aby bylo možné zjistit, jestli odpovídá kritéria filtru.  
  
 Obecně platí neměli byste následující při implementaci vlastního filtru:  
  
-   Vstupně-výstupní operace, jako je například ukládání dat na disk nebo do databáze.  
  
-   Nepotřebné zpracování, např. opakování ve smyčce přes více záznamů v dokumentu.  
  
-   Blokování operace, například volání, které se týkají získání zámku na sdílených prostředků nebo provádění hledání proti databázi.  
  
 Před použitím vlastního filtru v provozním prostředí, byste měli spustit testy výkonu k určení průměrnou délku dobu, která filtr potřebná k vyhodnocení zprávu. V kombinaci s průměrný čas zpracovávání ostatní filtry použité v tabulce filtru, to vám umožní přesně určit maximální časový limit hodnotu, která musí být zadán klientskou aplikací.  
  
## <a name="usage"></a>Použití  
 Pokud chcete používat vlastní filtr se službou směrování, je třeba přidat ji do tabulky filtru tak, že zadáte nový záznam filtru typu "Vlastní," název plně kvalifikovaný typ filtru zpráv a název vaší sestavení.  Stejně jako u jiných MessageFilters zadaný řetězec fulltextových dat filtru, která bude předána do konstruktoru vlastního filtru.  
  
 Následující příklady ukazují použití vlastního filtru se službou směrování:  
  
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
