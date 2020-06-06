---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088378"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener> – element (nastavení sítě)
Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Typ  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|unescapeRequestUrl|Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[zdroje dat](settings-element-network-settings.md)|Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut **UnescapeRequestUrl** označuje, zda <xref:System.Net.HttpListener> Nástroj používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI, ve kterém jsou převáděny všechny hodnoty zakódované v procentech a provedeny další kroky normalizace.  
  
 Když <xref:System.Net.HttpListener> instance obdrží požadavek přes `http.sys` službu, vytvoří instanci řetězce identifikátoru URI, kterou poskytuje `http.sys` , a zpřístupní ji jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.  
  
 `http.sys`Služba zpřístupňuje dva řetězce identifikátoru URI žádosti:  
  
- Nezpracovaný identifikátor URI  
  
- Převedený identifikátor URI  
  
 Nezpracovaný identifikátor URI je <xref:System.Uri?displayProperty=nameWithType> uvedený na řádku požadavku požadavku http:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nezpracovaný identifikátor URI poskytnutý `http.sys` pro výše zmíněnou žádost je "/path/". To představuje řetězec, který následuje za příkazem HTTP, jak byl odeslán přes síť.  
  
 `http.sys`Služba vytvoří převedený identifikátor URI z informací uvedených v žádosti pomocí identifikátoru URI, který je k dispozici na řádku požadavku HTTP a hlavičce hostitele k určení serveru původu, na který má být požadavek předán. To se provádí porovnáním informací z požadavku se sadou registrovaných předpon identifikátorů URI. Dokumentace k sadě SDK serveru HTTP odkazuje na tento identifikátor URI, který je převedený jako struktura HTTP_COOKED_URL.  
  
 Aby bylo možné porovnat požadavek s registrovanými předponami identifikátoru URI, je nutné provést určitou normalizaci žádosti. Pro ukázku nad převedený identifikátor URI by byl následující:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`Služba kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> hodnotu vlastnosti a řetězec na řádku požadavku k vytvoření PŘEVEDENého identifikátoru URI. Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> Třída provede také následující:  
  
- Zruší řídicí znaky všech hodnot kódovaných v procentech.  
  
- Převede znaky, které nejsou zakódované v procentech, do reprezentace znaků UTF-16. Všimněte si, že se podporují znakové sady UTF-8 a ANSI/DBCS a také znaky Unicode (kódování Unicode pomocí formátu% uXXXX).  
  
- Provede další kroky normalizace, jako je komprese cesty.  
  
 Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování používaném v procentech zakódovaných hodnot, nemusí být možné určit správné kódování pouhým analýzou hodnot kódovaných v procentech.  
  
 Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:  
  
|Klíč registru|Výchozí hodnota|Description|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Pokud je nula, `http.sys` akceptuje pouze adresy URL kódované v kódování UTF-8.<br /><br /> Pokud je hodnota nenulová, `http.sys` v požadavcích také přijímá adresy URL kódované v kódování ANSI nebo DBCS.|  
|FavorUTF8|1|Pokud je hodnota nenulová, `http.sys` vždy se pokusí dekódovat adresu URL jako znakovou sadu UTF-8. Pokud se převod nezdařil a EnableNonUTF8 je nenulový, http. sys, pokusí se ho dekódovat jako ANSI nebo DBCS.<br /><br /> Pokud je nula (a EnableNonUTF8 není nula), `http.sys` pokusí se dekódovat jako ANSI nebo DBCS; Pokud to není úspěšné, pokusí se převod znakové sady UTF-8.|  
  
 Když aplikace <xref:System.Net.HttpListener> obdrží požadavek, použije převedený identifikátor URI z `http.sys` as Input na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 V identifikátorech URI je potřeba podporovat znaky kromě znaků a číslic. Příkladem je následující identifikátor URI, který se používá k načtení informací o zákaznících pro číslo zákazníka "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Poznamenejte si procento lomítka v identifikátoru URI (% 2F). To je nezbytné, protože v tomto případě znak lomítka představuje data a není oddělovačem cesty.  
  
 Předání řetězce do konstruktoru identifikátoru URI vede k následujícímu identifikátoru URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Rozdělení cesty k jeho segmentům by vedlo k následujícím prvkům:  
  
 `Customer('1`  
  
 `3812')`  
  
 Nejedná se o záměr odesilatele žádosti.  
  
 Pokud je atribut **UnescapeRequestUrl** nastaven na **hodnotu false**, pak při <xref:System.Net.HttpListener> přijetí žádosti použije nezpracovaný identifikátor URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 Výchozí hodnota pro atribut **UnescapeRequestUrl** je **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Vlastnost lze použít k získání aktuální hodnoty atributu **UnescapeRequestUrl** z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat třídu, <xref:System.Net.HttpListener> když obdrží požadavek na použití nezpracovaného identifikátoru URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>Informace o elementu  
  
|||
|-|-|  
|Obor názvů|System.Net|  
|Název schématu||  
|Soubor ověření||  
|Může být prázdné||  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schéma nastavení sítě](index.md)
