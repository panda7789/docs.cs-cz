---
title: Vlastní filtry
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857217"
---
# <a name="custom-filters"></a>Vlastní filtry
Vlastní filtry umožňují definovat odpovídající logiku, která nelze provést pomocí zprávy poskytnuté systémem filtry. Například může vytvořit vlastní filtr, který hashuje prvek konkrétní zprávy a poté zkontroluje hodnotu k určení, zda filtr by měl vrátit hodnotu true nebo false.  
  
## <a name="implementation"></a>Implementace  
 Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třída. Při implementaci vlastní filtr, konstruktor může volitelně přijmout jako parametr jeden řetězec. Tento parametr obsahuje informace o konfiguraci, který je předán konstruktoru MessageFilter negace, odpovídá všechny hodnoty nebo konfiguraci, kterou filtr musí za běhu, aby bylo možné provést. Například to může být použije zadejte hodnotu, která filtr hledá v rámci zprávy právě vyhodnocována. Následující příklad ukazuje základní implementaci filtru vlastní zprávu, která přijímá řetězcový parametr:  
  
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
>  Ve skutečné implementaci, obsahuje alespoň jednu metodu porovnání logiku, která se zaměřuje zpráva, kterou chcete určit, pokud by měla vrátit tomuto filtru zprávy **true** nebo **false**.  
  
### <a name="performance"></a>Výkon  
 Při implementaci vlastního filtru, je potřeba vzít v úvahu delší dobu potřebnou pro filtr k vyzkoušení zprávu. Vzhledem k tomu, že zpráva může být porovnán s více filtrů, předtím, než je nalezena shoda, je důležité zajistit, že žádost klienta nemá časový limit před vyhodnocením všechny filtry. Vlastní filtr proto by měl obsahovat pouze kódu potřebného k vyhodnocení obsahu nebo atributů zprávu, aby bylo možné zjistit, jestli odpovídá kritéria filtru.  
  
 Obecně byste se měli vyhnout následující při implementaci vlastního filtru:  
  
- Vstupně-výstupních operací, jako je ukládání dat na disk nebo do databáze.  
  
- Nepotřebná zpracování, např. opakování ve smyčce přes více záznamů v dokumentu.  
  
- Blokovat operace, jako je volání, které se týkají získání zámku na sdílených prostředků nebo vyhledávání proti databázi.  
  
 Před použitím vlastního filtru v provozním prostředí, byste provést testy výkonu k určení průměrnou dobu filtru trvá vyhodnotit zprávu. V kombinaci s Průměrná doba zpracování jiných filtry použité v tabulce filtrů, to umožní vám přesně určit maximální hodnotu časového limitu, který by měl být určeno klientské aplikace.  
  
## <a name="usage"></a>Použití  
 Pokud chcete používat vlastní filtr službou směrování, je třeba přidat ji do tabulky filtru tak, že zadáte novou položku Filtr typu "Vlastní" název plně kvalifikovaný typ filtru zpráv a název vašeho sestavení.  Stejně jako u jiných MessageFilters, můžete zadat řetězec fulltextových dat filtru, která bude předána do konstruktoru vlastního filtru.  
  
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
