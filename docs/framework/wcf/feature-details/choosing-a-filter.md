---
title: Výběr filtru
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 377d4f5c221ad37acf954b1dafc8712a388122ff
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478497"
---
# <a name="choosing-a-filter"></a>Výběr filtru
Při konfiguraci služby směrování, je důležité vybrat správnou zprávu filtry a nakonfigurujete je, aby bylo možné provést přesné shody proti přijímaných zpráv. Pokud filtry, které jste vybrali příliš rozsáhlá v jejich odpovídá nebo jsou nakonfigurovány nesprávně, zprávy jsou směrovány nesprávně. Pokud jsou příliš omezující filtry, pravděpodobně nemáte všechny platné trasy, které jsou k dispozici pro některé zprávy.  
  
## <a name="filter-types"></a>Typy filtrů  
 Při výběru filtry, které používá služba směrování, je důležité pochopit, jak každý filtr funguje a jaké informace jsou k dispozici jako součást příchozí zprávy. Například pokud jsou všechny zprávy přes stejný koncový bod, filtry adres a Název_koncového_bodu nejsou užitečné protože těmto filtrům neodpovídají všechny zprávy.  
  
### <a name="action"></a>Akce  
 Zkontroluje filtr akce <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> vlastnost. Pokud obsah záhlaví akce ve zprávě odpovídají hodnotě dat filtru zadaná v konfiguraci filtr a potom tento filtr vrátí `true`. Následující příklad definuje `FilterElement` filtru akce, která používá tak, aby odpovídaly zprávy s hlavičkou akce, která obsahuje hodnotu `http://namespace/contract/operation/`.
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Tento filtr by měla sloužit při směrování zpráv, které obsahují jedinečné záhlaví akce.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 Filtr EndpointAddress kontroluje EndpointAddress, který v byla přijata zpráva. Pokud na adresu, kterou se zpráva dorazí na přesně odpovídá adrese filtr zadaný v konfiguraci filtr a potom tento filtr vrátí `true`. Následující příklad definuje `FilterElement` , která používá filtr adres tak, aby odpovídaly všechny zprávy adresované na "http://\<název_hostitele > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Je důležité si uvědomit, že část názvu hostitele adresy se může lišit podle toho, zda klient používá plně kvalifikovaný název domény, název NetBIOS, IP adresu nebo jiný název. Protože různé hodnoty mohou odkazovat na stejného hostitele, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění shody.  
>   
>  Toto chování lze upravit umožňující porovnání k vyhodnocení názvu hostitele, při konfiguraci služby směrování prostřednictvím kódu programu.  
  
 Tento filtr by měla sloužit, když jsou příchozí zprávy adresované jedinečnou adresu.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 Filtr EndpointAddressPrefix je podobný filtrování EndpointAddress. Filtr EndpointAddressPrefix kontroluje EndpointAddress, který v byla přijata zpráva. Ale EndpointAddressPrefix filtr funguje jako zástupný znak to provede spárováním odpovídajících adresy, které začínají hodnotu zadanou v konfiguraci filtru. Následující příklad definuje `FilterElement` EndpointAddressPrefix filtr, který používá tak, aby odpovídaly všechny zprávy adresované `http://<hostname>/vdir*`.  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Je důležité si uvědomit, že část názvu hostitele adresy se může lišit podle toho, zda klient používá plně kvalifikovaný název domény, název NetBIOS, IP adresu nebo jiný název. Protože různé hodnoty mohou odkazovat na stejného hostitele, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění shody.  
  
 Tento filtr by měla sloužit při směrování příchozích zpráv, které sdílejí běžnou předponu adresy.  
  
### <a name="and"></a>AND  
 Filtr a nefiltruje přímo na základě hodnot v rámci zprávy, ale můžete kombinovat dva filtry k vytvoření `AND` kde oba filtry musí odpovídat zprávu před vyhodnotí jako filtr a podmínka `true`. To umožňuje vytvořit komplexní filtry, které odpovídá pouze pokud se shodují všechny dílčí filtry. Následující příklad definuje filtr adresy a filtru akce a pak definuje filtr a, který se vyhodnotí zprávu před filtry adresu a akce. Pokud adresu a filtrů Akce shodují, pak filtr a vrátí `true`.  
  
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
  
 Tento filtr by měla sloužit, když zkombinujete musí logiku z více filtrů k určení, kdy je třeba shodu. Například pokud máte více cílů, které musí přijmout jenom určité kombinace akcí a zprávy pro konkrétní adresy, můžete použít filtr a potřebné akce a adresu filtry zkombinovat.  
  
### <a name="custom"></a>Vlastní  
 Když vyberete vlastní typ filtru, je nutné zadat customtype – hodnota, která obsahuje typ, který obsahuje sestavení **MessageFilter** implementace má být použit pro tento filtr. Kromě toho fulltextových dat filtru musí obsahovat všechny hodnoty, které vlastní filtr může vyžadovat jeho vyhodnocení zpráv. Následující příklad definuje `FilterElement` , která používá `CustomAssembly.MyCustomMsgFilter` MessageFilter implementace.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Pokud je potřeba provést vlastní logiku odpovídající proti zprávu, která není předmětem filtry, opatřeného [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], musíte vytvořit vlastní filtr, který je implementace **MessageFilter** třídy. Například může vytvořit vlastní filtr, který porovnává pole v příchozí zprávě seznam se známými hodnot na základě předané do filtru jako konfigurace, nebo se hashuje prvek konkrétní zprávy a zkontroluje tuto hodnotu k určení, zda filtr by měla vrátit `true` nebo `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Filtr Název_koncového_bodu kontroluje název koncového bodu, která se zobrazila zpráva. Následující příklad definuje `FilterElement` , který využívá filtr Název_koncového_bodu pro směrování zpráv byla přijata na "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Tento filtr je užitečný při směrovací služba poskytuje více než jeden koncový bod s názvem služby. Například může zveřejnit dva koncové body, které směrovací služba používá pro příjem zprávy. jeden používá priority zákazníci, kteří požadují zpracování jejich zpráv při jiný koncový bod v reálném čase přijímá zprávy, které nejsou citlivé na čas.  
  
 I když můžete často použít úplnou adresu odpovídající k určení koncového bodu byla přijata zpráva, místo toho použít název definovaný koncový bod je pohodlný zástupce, který je často nižší náchylné k chybám, zejména při konfiguraci pomocí konfigurace služby Směrování soubor (kde názvy koncových bodů se požadovaný atribut).  
  
### <a name="matchall"></a>MatchAll  
 MatchAll filtr hledá shodu ve všech přijaté zprávy. To je užitečné, pokud všechny přijaté zprávy musí vždy směrovat do určitého koncového bodu, jako je například protokolování služby, která ukládá jejich kopii všechny přijaté zprávy. Následující příklad definuje `FilterElement` , která používá MatchAll filtru.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole určitého prvku zprávy. Filtrování XPath je efektivní filtrování možnost, která umožňuje přímo zkontrolovat všechny adresovatelný položky XML do zprávy. ale vyžaduje, že máte specifické znalosti struktury zprávy, které jste dostali. Následující příklad definuje `FilterElement` filtr XPath, který používá ke kontrole zprávu pro element s názvem "element" v rámci oboru názvů odkazuje předponu oboru názvů "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Tento filtr je užitečný, pokud víte, že zprávy, které jste obdrželi, obsahují určitou hodnotu. Pokud hostujete dvě verze stejné služby a víte, že zprávy adresované na novější verzi služby obsahují jedinečnou hodnotu ve vlastní hlavičce, je třeba vytvořit filtr, který používá výraz XPath pro navigaci k této hlavičce a porovnává hodnotu stisknutím ent v záhlaví na jiný zadaný v konfiguraci filtr k určení, jestli tento filtr odpovídá.  
  
 Protože dotazy XPath často obsahovat jedinečný obory názvů, které jsou často dlouhé nebo komplexní řetězcové hodnoty filtr XPath vám umožní definovat jedinečný předpony pro obory názvů pomocí oboru názvů tabulky. Další informace o tabulce obor názvů, naleznete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Další informace o navrhování dotazů XPath, naleznete v tématu [syntaxi XPath](https://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Viz také  
 [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Postupy: Používání filtrů](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
