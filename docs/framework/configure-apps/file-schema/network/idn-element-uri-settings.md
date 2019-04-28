---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 2d2729f9120d6b6fe673904ad2bf6d005ddf5469
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705101"
---
# <a name="idn-element-uri-settings"></a>\<IDN > – Element (nastavení Uri)
Určuje, pokud analýza mezinárodních názvů domén (IDN) se použije na název domény.  
  
## <a name="schema-hierarchy"></a>Schema Hierarchy  
 [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identifikátor URI > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|`enabled`|Určuje, že jestli parsování mezinárodních názvů domén (IDN) se použije pro název domény výchozí hodnota je none.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).|  
  
## <a name="remarks"></a>Poznámky  
 Existující <xref:System.Uri> bylo rozšířeno třídy v rozhraní .NET Framework 3.5. 3.0 SP1 a 2.0 SP1 s podporou International Resource identifikátory (IRI) a mezinárodní názvy domén (IDN). Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud výslovně povolit IRI a IDN podporovat. Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.  
  
 Povolení podpory pro IRI, jsou požadovány následující dvě změny:  
  
1. Přidejte následující řádek do souboru machine.config, v adresáři rozhraní .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Zadejte, jestli chcete parsování mezinárodních názvů domén (IDN) k názvu domény a určuje, zda by měl použít IRI pravidel pro analýzu. To můžete udělat v souboru machine.config nebo v souboru app.config.  
  
 Existují tři možné hodnoty pro IDN v závislosti na servery DNS, které se používají:  
  
- IDN, povoleno = All  
  
     Tato hodnota se převede názvy domén, Unicode na jejich ekvivalenty kódování Punycode (názvy IDN).  
  
- IDN, povoleno = AllExceptIntranet  
  
     Tato hodnota se převede všechny názvy domén Unicode nejsou v místním intranetu používat kódování Punycode ekvivalenty (názvy IDN). V tomto případě zpracování mezinárodních názvů na místní Intranet, které se používají pro intranetové servery DNS by měly podporovat překlad kódování Unicode.  
  
- IDN, povoleno = None  
  
     Tato hodnota neprovede konverzi názvy domén, Unicode používat kódování Punycode. Toto je výchozí hodnota je shodný se chování rozhraní .NET Framework 2.0.  
  
 Povolení IDN převede všechny popisky kódování Unicode v názvu domény na jejich ekvivalenty kódování Punycode. Kódování Punycode názvy obsahovat pouze znaky ASCII a vždy začínají předponou xn –. Důvodem je k podpoře existujících serverů DNS na Internetu, protože většina servery DNS podporují jenom znaky ASCII (viz RFC 3940).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.  
  
### <a name="code"></a>Kód  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
