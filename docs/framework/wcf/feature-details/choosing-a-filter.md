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
# <a name="choosing-a-filter"></a>Výběr filtru
Při konfiguraci služby směrování, je důležité vybrat filtry správné zpráv a nakonfigurovat je pro přesné shody proti zprávy, které vám umožňují. Pokud filtry, které jste vybrali jsou v jejich odpovídá příliš široké, nebo jsou nesprávně nakonfigurované, zprávy jsou směrovány nesprávně. Pokud jsou filtry příliš omezující, nemusí mít žádné platné tras, které jsou k dispozici pro některé zprávy.  
  
## <a name="filter-types"></a>Typy filtrů  
 Když vyberete filtry, které používají službu směrování, je důležité pochopit, jak každý filtr funguje a jaké informace jsou k dispozici jako součást příchozí zprávy. Například pokud jsou všechny zprávy přes stejný koncový bod, filtry adres a EndpointName nejsou užitečné vzhledem k tomu, že všechny zprávy splňují tyto filtry.  
  
### <a name="action"></a>Akce  
 Zkontroluje filtr akce <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> vlastnost. Pokud obsah hlavičky akce ve zprávě odpovídají hodnotě dat filtru, který je zadaný v konfiguraci filtru, pak tento filtr vrátí `true`. V následujícím příkladu definuje `FilterElement` používající filtr akce tak, aby odpovídaly zprávy s hlavičku akce, která obsahuje hodnotu "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Tento filtr by měl být použit při směrování zprávy, které obsahují hlavičku jedinečný akce.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 Filtr EndpointAddress zkontroluje EndpointAddress, která byla přijata zpráva na. Pokud adresu zpráva dorazí na přesně odpovídá adrese filtr zadaný v konfiguraci filtru, pak tento filtr vrátí `true`. V následujícím příkladu definuje `FilterElement` používající filtr adres tak, aby odpovídaly všechny zprávy adresované do "http://\<hostname > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Je důležité si uvědomit, že část názvu hostitele adresy může lišit v závislosti na tom, zda klient používá s plně kvalifikovaným názvem domény, název pro rozhraní NetBIOS, IP adresu nebo jiný název. Protože odlišné hodnoty mohou odkazovat na stejném hostiteli, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění odpovídá.  
>   
>  Toto chování můžete upravit tak, aby povolit porovnání vyhodnotit název hostitele, při konfiguraci služby směrování prostřednictvím kódu programu.  
  
 Tento filtr by měl být použit při jsou příchozí zprávy adresované jedinečnou adresu.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 Filtr EndpointAddressPrefix je podobná EndpointAddress filtru. Filtr EndpointAddressPrefix zkontroluje EndpointAddress, která byla přijata zpráva na. Ale filtru EndpointAddressPrefix funguje jako zástupný znak pomocí odpovídajících adresy, které začínají hodnota zadaná v konfiguraci filtru. V následujícím příkladu definuje `FilterElement` používající EndpointAddressPrefix filtru tak, aby odpovídaly všechny zprávy adresované do "http://\<hostname > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Je důležité si uvědomit, že část názvu hostitele adresy může lišit v závislosti na tom, zda klient používá s plně kvalifikovaným názvem domény, název pro rozhraní NetBIOS, IP adresu nebo jiný název. Protože odlišné hodnoty mohou odkazovat na stejném hostiteli, je výchozí chování pro tuto chvíli nechcete použít část názvu hostitele adresy při provádění odpovídá.  
  
 Tento filtr by měl být použit při směrování příchozích zpráv, které sdílejí společné předpona adresy.  
  
### <a name="and"></a>AND  
 Filtr a nefiltruje přímo na hodnotu ve zprávě, ale umožňuje zkombinovat dva filtry k vytvoření `AND` podmínky, které oba filtry musí se shodovat zprávu a filtru se vyhodnocuje `true`. To umožňuje vytváření složitých filtrů, které odpovídá pouze pokud se shodují všechny dílčí filtry. V následujícím příkladu definuje filtr adres a filtru akce a pak definuje filtr a, která vyhodnotí zprávu před filtry adres i akce. Pokud adresu a filtrů Akce shodují, pak filtr a vrací `true`.  
  
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
  
 Tento filtr by měl být použit při musíte kombinovat logiku z více filtrů k určení, kdy má být nalezena shoda k. Například pokud máte více cílů, které musí obdržet pouze určité kombinace akce a zprávy pro konkrétní adresy, můžete použít filtr a se zkombinovat filtry potřebné akce a adresu.  
  
### <a name="custom"></a>Vlastní  
 Když vyberete typ filtru vlastní, je nutné zadat hodnotu customType, která obsahuje sestavení, které obsahuje typ **MessageFilter** implementace má být použit pro tento filtr. Kromě toho fulltextových dat filtru musí obsahovat všechny hodnoty, které vlastní filtr může vyžadovat ohodnocení zprávy. V následujícím příkladu definuje `FilterElement` používající `CustomAssembly.MyCustomMsgFilter` MessageFilter implementace.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Pokud potřebujete provést vlastní logiky odpovídající proti zprávu, která není předmětem filtry součástí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], musíte vytvořit vlastní filtr, který je implementací **MessageFilter** třídy. Například může vytvořit vlastní filtr, který porovnává pole v příchozí zpráva seznam známých hodnot na základě předané filtru jako konfigurace, nebo se rozdělí elementu konkrétní zprávy a poté zkoumá tuto hodnotu určit zda filtr by měla vrátit `true` nebo `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Filtr EndpointName kontroluje název koncového bodu, který se zobrazila zpráva. V následujícím příkladu definuje `FilterElement` používající EndpointName filtru pro směrování zpráv byla přijata "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Tento filtr je užitečné, když směrovací služby zpřístupní více než jeden koncový bod s názvem služby. Například mohou být vystaveny dva koncové body, které služba Směrování se používá pro příjem zpráv; jeden se používá s prioritou zákazníci, kteří vyžadují v reálném čase, zpracování jejich zpráv při jiný koncový bod přijímá zprávy, které nejsou čas velká a malá písmena.  
  
 I když můžete používat často úplná adresa odpovídající k určení kterému koncovému bodu byla přijata zpráva, místo toho použít název koncového bodu definovaného je vhodné zástupce, který je často méně náchylný, zejména v případě, že konfigurace směrování služby pomocí nástroje Konfigurace soubor (kde názvy koncových bodů jsou povinný atribut).  
  
### <a name="matchall"></a>MatchAll  
 Filtr MatchAll odpovídá všechny přijaté zprávy. Je vhodné, pokud všechny přijaté zprávy musí vždy směrovat na konkrétní, jako je například služba protokolování, která ukládá kopie všechny přijaté zprávy. V následujícím příkladu definuje `FilterElement` používající MatchAll filtru.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 Filtr XPath umožňuje zadat dotaz XPath, který se používá ke kontrole určitého prvku zprávy. Filtrování XPath je výkonný filtrování možnost, která umožňuje přímo zkontrolovat všechny XML adresovatelné položky v rámci message; ale vyžaduje, že máte konkrétní znalosti struktury zprávy, které jste obdrželi. V následujícím příkladu definuje `FilterElement` používající filtr XPath kontrola zprávu pro element s názvem "elementu" v rámci oboru názvů odkazuje Předpona oboru názvů "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Tento filtr je užitečné, pokud víte, že zprávy, které jste obdrželi, obsahují konkrétní hodnotu. Například pokud hostujete dvě verze stejné služby a víte, že zprávy adresované na novější verzi služby obsahovat jedinečnou hodnotu ve vlastní hlavičky, můžete vytvořit filtr, který používá XPath přejděte na tuto hlavičku a porovnává hodnotu stisknutím trola v hlavičce na jiný zadaný v konfiguraci filtr k určení, jestli odpovídá filtru.  
  
 Protože dotazů XPath často obsahují jedinečný obory názvů, které jsou často zdlouhavé nebo komplexní řetězcové hodnoty filtr XPath umožňuje obor názvů tabulku použijte k definování jedinečný předpon pro obory. Další informace o tabulce obor názvů najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Další informace o návrhu dotazů XPath najdete v tématu [syntaxe jazyka XPath](http://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Viz také  
 [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Postupy: Používání filtrů](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
