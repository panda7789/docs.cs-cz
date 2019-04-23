---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099739"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener > – Element (nastavení sítě)
Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.  
  
 \<Konfigurace >  
\<system.net>  
\<settings>  
\<httpListener>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Type  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|unescapeRequestUrl|Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaná neuvozené identifikátor URI namísto převedený identifikátoru URI.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 **UnescapeRequestUrl** atribut označuje, zda <xref:System.Net.HttpListener> používá nezpracovaná neuvozené identifikátor URI namísto převedený identifikátor URI, kde všechny procentuálně zakódovaný hodnoty se převedou a ostatní kroky normalizace pocházejí.  
  
 Když <xref:System.Net.HttpListener> instance obdrží žádost prostřednictvím `http.sys` služby, vytvoří instanci řetězec identifikátoru URI poskytuje `http.sys`a zpřístupní ho jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.  
  
 `http.sys` Služba poskytuje dva řetězce identifikátoru URI požadavku:  
  
-   Identifikátor URI nezpracované  
  
-   Převedený identifikátoru URI  
  
 Identifikátor URI nezpracované <xref:System.Uri?displayProperty=nameWithType> v řádku žádosti požadavku HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nezpracovaná URI poskytuje `http.sys` pro požadavek uvedených výše, je "/ cesta /". To představuje řetězec po příkaz HTTP byl odeslán přes síť.  
  
 `http.sys` Služby vytvoří převedený identifikátor URI z informací uvedených v požadavku pomocí identifikátoru URI k dispozici v řádku požadavku HTTP a mají předávat hlavičku hostitele k určení požadavku na zdrojový server. To se provádí porovnáváním informací z požadavku sadu registrovaných předpony identifikátoru URI. Dokumentace ke službě SDK serveru HTTP odkazuje na tento identifikátor URI převedený jako HTTP_COOKED_URL struktury.  
  
 Aby bylo možné porovnat požadavek s registrované předpony identifikátoru URI, je potřeba udělat nějaké normalizace na požadavek. Pro ukázku nad převedený identifikátoru URI by měl vypadat takto:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Služby kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> řetězec v řádku žádost o vytvoření převedený identifikátor URI a hodnota vlastnosti. Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> třída rovněž provede následující akce:  
  
-   Zrušit – řídicí sekvence kódovaného všechny procentuální hodnoty.  
  
-   Převede procentuálně zakódovaný jiné znaky než ASCII na reprezentaci znaků UTF-16. Všimněte si, že jsou podporovány UTF-8 a ANSI/DBCS znaky a znaky kódování Unicode (kódování Unicode ve formátu uXXXX %).  
  
-   Spustí další kroky normalizace, jako je komprese cestu.  
  
 Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování použité pro procentuálně zakódovaný hodnoty, nemusí být možné určit správné kódování pouhým Analýza hodnot procentuálně zakódovaný.  
  
 Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:  
  
|Klíč registru|Výchozí hodnota|Popis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Pokud je nula, `http.sys` přijímá pouze adresy kódování UTF-8.<br /><br /> Nenulová, pokud `http.sys` přijímá také kódovaný v ANSI nebo DBCS kódování adresy URL v požadavcích.|  
|FavorUTF8|1|Nenulová, pokud `http.sys` vždy pokusí dekódování adresu URL jako UTF-8. Pokud se nepovede převodu a EnableNonUTF8 nenulové, ovladač Http.sys potom pokusí dekódovat jako ANSI nebo DBCS.<br /><br /> Pokud je nula (a EnableNonUTF8 zbývá nenulový), `http.sys` pokusí dekódovat jako ANSI nebo DBCS; Pokud to není úspěšné, pokusí převod kódování UTF-8.|  
  
 Když <xref:System.Net.HttpListener> obdrží žádost, používá převedený identifikátor URI ze `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 Je potřeba pro podporu znaky kromě znaky a čísla v identifikátorech URI. Příkladem je následující identifikátor URI, který slouží k načtení informací zákazníků pro zákazníka číslo "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Všimněte si lomítko procentuálně zakódovaný v identifikátoru Uri (% 2F). To je nezbytné, protože v tomto případě představuje znak lomítka dat a oddělovač cesty.  
  
 Předání řetězce identifikátoru Uri konstruktoru povede k následující identifikátor URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Rozdělení do jeho segmentů cesty by mít za následek následující prvky:  
  
 `Customer('1`  
  
 `3812')`  
  
 Toto není cílem odesílatel požadavku.  
  
 Pokud **unescapeRequestUrl** atribut je nastaven na **false**, pak když <xref:System.Net.HttpListener> obdrží žádost, používá nezpracovaná identifikátor URI namísto převedený identifikátor URI ze `http.sys` jako vstup <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
 Výchozí hodnota **unescapeRequestUrl** atribut je **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Vlastnost lze použít k získání aktuální hodnoty **unescapeRequestUrl** atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net.HttpListener> třídy, když přijme požadavek na identifikátor URI nezpracované nahrazujícím převedený identifikátor URI ze `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.  
  
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
|Může být prázdné.||  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
