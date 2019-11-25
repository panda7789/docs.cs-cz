---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088378"
---
# <a name="httplistener-element-network-settings"></a>\<element > httpListener (nastavení sítě)
Přizpůsobuje parametry používané třídou <xref:System.Net.HttpListener>.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nastavení >** ](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpListener >**

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
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[možnost](settings-element-network-settings.md)|Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut **UnescapeRequestUrl** označuje, zda <xref:System.Net.HttpListener> používá nezpracovaný identifikátor URI bez řídicího znaku namísto PŘEVEDENého identifikátoru URI, kde jsou převáděny všechny hodnoty zakódované v procentech a jsou provedeny další kroky normalizace.  
  
 Když instance <xref:System.Net.HttpListener> obdrží požadavek prostřednictvím služby `http.sys`, vytvoří instanci řetězce identifikátoru URI, kterou poskytuje `http.sys`, a zpřístupní ji jako vlastnost <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.  
  
 Služba `http.sys` zpřístupňuje dva řetězce identifikátoru URI žádosti:  
  
- Nezpracovaný identifikátor URI  
  
- Převedený identifikátor URI  
  
 Nezpracovaný identifikátor URI je <xref:System.Uri?displayProperty=nameWithType>, který je k dispozici na řádku požadavku požadavku HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nezpracovaný identifikátor URI poskytnutý `http.sys` pro výše uvedenou žádost je "/path/". To představuje řetězec, který následuje za příkazem HTTP, jak byl odeslán přes síť.  
  
 Služba `http.sys` vytvoří převedený identifikátor URI z informací uvedených v žádosti pomocí identifikátoru URI, který je k dispozici na řádku požadavku HTTP a v hlavičce hostitele k určení serveru původu, na který má být požadavek předán. To se provádí porovnáním informací z požadavku se sadou registrovaných předpon identifikátorů URI. Dokumentace k sadě SDK serveru HTTP odkazuje na tento identifikátor URI, který je převedený jako struktura HTTP_COOKED_URL.  
  
 Aby bylo možné porovnat požadavek s registrovanými předponami identifikátoru URI, je nutné provést určitou normalizaci žádosti. Pro ukázku nad převedený identifikátor URI by byl následující:  
  
 `http://www.contoso.com/path/`  
  
 Služba `http.sys` kombinuje hodnotu vlastnosti <xref:System.Uri.Host%2A?displayProperty=nameWithType> a řetězec na řádku požadavku k vytvoření převedeného identifikátoru URI. Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> Třída provede také následující:  
  
- Zruší řídicí znaky všech hodnot kódovaných v procentech.  
  
- Převede znaky, které nejsou zakódované v procentech, do reprezentace znaků UTF-16. Všimněte si, že se podporují znakové sady UTF-8 a ANSI/DBCS a také znaky Unicode (kódování Unicode pomocí formátu% uXXXX).  
  
- Provede další kroky normalizace, jako je komprese cesty.  
  
 Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování používaném v procentech zakódovaných hodnot, nemusí být možné určit správné kódování pouhým analýzou hodnot kódovaných v procentech.  
  
 Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:  
  
|Klíč registru|Výchozí hodnota|Popis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|první|Pokud je nula, `http.sys` přijímá pouze adresy URL kódované v kódování UTF-8.<br /><br /> Pokud je hodnota nenulová, `http.sys` také v žádostech přijímat adresy URL kódované v kódování ANSI nebo DBCS.|  
|FavorUTF8|první|Pokud není nula, `http.sys` se vždy pokusí dekódovat adresu URL jako UTF-8 First; Pokud se převod nezdařil a EnableNonUTF8 je nenulová, http. sys se pak pokusí dekódovat jako ANSI nebo DBCS.<br /><br /> Pokud je nula (a EnableNonUTF8 není nula), `http.sys` se pokusí dekódovat jako ANSI nebo DBCS; Pokud se to nepodaří, pokusí se převod UTF-8.|  
  
 Když <xref:System.Net.HttpListener> obdrží požadavek, použije převedený identifikátor URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 V identifikátorech URI je potřeba podporovat znaky kromě znaků a číslic. Příkladem je následující identifikátor URI, který se používá k načtení informací o zákaznících pro číslo zákazníka "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Poznamenejte si procento lomítka v identifikátoru URI (% 2F). To je nezbytné, protože v tomto případě znak lomítka představuje data a není oddělovačem cesty.  
  
 Předání řetězce do konstruktoru identifikátoru URI vede k následujícímu identifikátoru URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Rozdělení cesty k jeho segmentům by vedlo k následujícím prvkům:  
  
 `Customer('1`  
  
 `3812')`  
  
 Nejedná se o záměr odesilatele žádosti.  
  
 Pokud je atribut **UnescapeRequestUrl** nastaven na **hodnotu false**, pak když <xref:System.Net.HttpListener> obdrží požadavek, použije nezpracovaný identifikátor URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 Výchozí hodnota pro atribut **UnescapeRequestUrl** je **true**.  
  
 Vlastnost <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> lze použít k získání aktuální hodnoty atributu **UnescapeRequestUrl** z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat třídu <xref:System.Net.HttpListener>, když obdrží požadavek na použití nezpracovaného IDENTIFIKÁTORu URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schéma nastavení sítě](index.md)
