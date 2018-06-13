---
title: '&lt;httpListener&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a327f757f26c815d5b2cffe179af68bbe3d152eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744873"
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; – Element (nastavení sítě)
Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.  
  
 \<Konfigurace >  
\<system.net>  
\<Nastavení >  
\<httpListener >  
  
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
|unescapeRequestUrl|Logická hodnota, která označuje, pokud <xref:System.Net.HttpListener> instance používá nezpracovaná neuvozené URI místo převedený identifikátor URI.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 **UnescapeRequestUrl** atribut uvádí, pokud <xref:System.Net.HttpListener> místo převedený identifikátor URI, kde se převedou všechny hodnoty kódováním procent a jsou přesměrováni další kroky normalizaci používá nezpracovaná neuvozené identifikátor URI.  
  
 Když <xref:System.Net.HttpListener> instance obdrží žádost prostřednictvím `http.sys` služby, vytvoří instanci řetězce identifikátoru URI poskytuje `http.sys`a zpřístupní ho jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.  
  
 `http.sys` Service poskytuje dva řetězce identifikátoru URI žádosti:  
  
-   Nezpracovaná URI  
  
-   Převedený URI  
  
 Je identifikátor URI, nezpracovaná <xref:System.Uri?displayProperty=nameWithType> uvedené v řádku žádosti požadavku HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nezpracovaná URI poskytované `http.sys` pro požadavek uvedených výše, je "/ cesta /". To představuje řetězec následující příkaz protokolu HTTP, protože byla odeslána po síti.  
  
 `http.sys` Service vytvoří převedený URI z informací uvedených v žádosti pomocí identifikátoru URI uvedené v řádku požadavku HTTP a předáte hlavičku hostitele k určení požadavku na zdrojový server. Děje se tak, že porovnáte informace z požadavku sadu registrovaných předpony identifikátoru URI. V dokumentaci sady SDK serveru HTTP označuje jako strukturu HTTP_COOKED_URL tento převedený identifikátor URI.  
  
 Aby bylo možné k porovnání požadavek s registrované předpony identifikátoru URI, je třeba provést některé normalizaci na požadavek. Pro ukázku výše převedený URI vypadat takto:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Služby kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> hodnotu vlastnosti a řetězce v požadavku řádku k vytvoření převedený URI. Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> třída také provede následující akce:  
  
-   Zrušení – řídicí sekvence kódovaného všechny procentuální hodnoty.  
  
-   Převede kódováním procent jiné znaky než ASCII do znázornění UTF-16 znaků. Všimněte si, že znaky znakové sady UTF-8 a ANSI/DBCS se podporují i znaky znakové sady Unicode (kódování Unicode v formátu uXXXX %).  
  
-   Spustí další kroky normalizaci, jako cesta komprese.  
  
 Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování použité pro kódování v procentech hodnoty, nemusí být možné určit správné kódování právě analýzou hodnoty kódováním procent.  
  
 Proto `http.sys` poskytuje dva klíče registru pro úpravy proces:  
  
|Klíč registru|Výchozí hodnota|Popis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Pokud nula, `http.sys` přijímá jenom kódování UTF-8 adresy URL.<br /><br /> Pokud nulová, `http.sys` také přijímá kódování ANSI nebo kódováním DBCS adresy URL v žádosti.|  
|FavorUTF8|1|Pokud nulová, `http.sys` vždy pokusí dekódovat adresu URL jako UTF-8 nejprve; Pokud tento převod selže a EnableNonUTF8 je nulová, ovladač Http.sys potom pokusí dekódovat jako ANSI nebo DBCS.<br /><br /> Pokud nula (a EnableNonUTF8 je nulová), `http.sys` pokusí dekódovat jako ANSI nebo DBCS; Pokud tento není úspěšné, se pokusí o převodu znakové sady UTF-8.|  
  
 Když <xref:System.Net.HttpListener> přijme požadavek, používá převedený URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 Je třeba pro podporu znaky kromě znaky a čísla v identifikátory URI. Následující identifikátor URI, který se používá k načtení informací o zákazníka pro zákazníka je například číslo "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Poznámka: lomítko kódováním procent v identifikátoru Uri (% 2F). To je nutné, protože v takovém případě lomítko představuje data a ne cesta oddělovač.  
  
 Předání řetězec Uri konstruktor povede k identifikátoru URI následující:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Rozdělení do jeho segmentů cesty by mělo za následek následující prvky:  
  
 `Customer('1`  
  
 `3812')`  
  
 Nejedná se o záměr odesílatel požadavku.  
  
 Pokud **unescapeRequestUrl** je atribut nastaven na **false**, pak když <xref:System.Net.HttpListener> přijme požadavek, používá nezpracovaná URI místo převedený URI z `http.sys` jako vstup <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 Výchozí hodnota **unescapeRequestUrl** atribut je **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Vlastnost lze použít k získání aktuální hodnota **unescapeRequestUrl** atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net.HttpListener> třídy, pokud obdrží požadavek na místo převedený URI z používat nezpracovaná URI `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
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
|Ověření souboru||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
