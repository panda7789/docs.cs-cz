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
# <a name="custom-filters"></a>Vlastní filtry
Vlastní filtry umožňují definovat odpovídající logiku, kterou nelze provést pomocí filtrů zpráv poskytovaných systémem. Můžete například vytvořit vlastní filtr, který určí hodnotu hash konkrétního prvku zprávy, a poté ověří hodnotu, zda filtr má vrátit hodnotu true nebo false.  
  
## <a name="implementation"></a>Implementace  
 Vlastní filtr je implementace <xref:System.ServiceModel.Dispatcher.MessageFilter> abstraktní základní třídy. Při implementaci vlastního filtru může konstruktor volitelně přijmout jeden řetězcový parametr. Tento parametr obsahuje konfigurační informace, které jsou předány konstruktoru MessageFilter, aby bylo možné zadat jakékoli hodnoty nebo konfiguraci, které filtr potřebuje za běhu, aby bylo možné provést shodu. Můžete to například použít k poskytnutí hodnoty, kterou filtr vyhledává v rámci hodnocené zprávy. Následující příklad ukazuje základní implementaci vlastního filtru zpráv, který přijímá řetězcový parametr:  
  
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
> V samotné implementaci metody shody obsahují logiku, která prověřuje zprávu, aby zjistila, zda by filtr zpráv měl vracet **hodnotu true** nebo **false**.  
  
### <a name="performance"></a>Výkon  
 Při implementaci vlastního filtru je důležité vzít v úvahu maximální dobu potřebnou k tomu, aby filtr dokončil vyhodnocení zprávy. Vzhledem k tomu, že může být zpráva vyhodnocena proti více filtrům před nalezením shody, je důležité zajistit, aby žádost klienta neuplynula časový limit před tím, než bude možné vyhodnotit všechny filtry. Vlastní filtr proto by měl obsahovat pouze kód, který je nezbytný k vyhodnocení obsahu nebo atributů zprávy, aby bylo možné zjistit, zda odpovídá kritériím filtru.  
  
 Obecně platí, že při implementaci vlastního filtru byste se měli vyhnout následujícímu:  
  
- Vstupně-výstupní operace, například ukládání dat na disk nebo do databáze.  
  
- Nepotřebné zpracování, jako je například opakování několika záznamů v dokumentu.  
  
- Blokování operací, například volání, která zahrnují získání zámku sdílených prostředků nebo provádění vyhledávání v databázi.  
  
 Před použitím vlastního filtru v produkčním prostředí byste měli spustit testy výkonu a určit tak průměrnou dobu, kterou filtr provede k vyhodnocení zprávy. V kombinaci s průměrnou dobou zpracování dalších filtrů použitých v tabulce filtru vám to umožní přesně určit maximální hodnotu časového limitu, která by měla být určena klientskou aplikací.  
  
## <a name="usage"></a>Použití  
 Aby bylo možné používat vlastní filtr s směrovací službou, je nutné jej přidat do tabulky filtru zadáním nové položky filtru typu "vlastní", plně kvalifikovaného názvu typu filtru zprávy a názvu sestavení.  Stejně jako u jiných MessageFilters můžete zadat řetězec fulltextových, který bude předán konstruktoru vlastního filtru.  
  
 Následující příklady ukazují použití vlastního filtru se směrovací službou:  
  
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
