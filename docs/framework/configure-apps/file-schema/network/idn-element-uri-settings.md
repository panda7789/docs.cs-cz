---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698161"
---
# <a name="idn-element-uri-settings"></a>\<element IDN > (nastavení URI)

Určuje, jestli se má pro název domény použít analýza v mezinárodním názvu domény (IDN).
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<idn >**  
  
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
|`enabled`|Určuje, jestli se pro název domény použije analýza v mezinárodní doméně (IDN). výchozí hodnota je None.|  

### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky

|**Element**|**Popis**|  
|-----------------|---------------------|  
|[identifikátor URI](uri-element-uri-settings.md)|Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).|  

## <a name="remarks"></a>Poznámky

Existující třída <xref:System.Uri> byla rozšířena v .NET Framework 3,5. 3,0 SP1 a 2,0 SP1 s podporou pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN). Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN. Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.

Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:

1. Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0:
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Určete, jestli se má pro název domény použít analýza v mezinárodní doméně (IDN) a jestli se mají použít pravidla analýzy IRI. To lze provést v souboru Machine. config nebo v souboru App. config.

 Existují tři možné hodnoty pro IDN v závislosti na používaných serverech DNS:

- IDN povolené = vše  

     Tato hodnota převede všechny názvy domén Unicode na jejich ekvivalenty Punycode (názvy IDN).

- povolené IDN = AllExceptIntranet

     Tato hodnota převede všechny názvy domén Unicode, které nejsou v místním intranetu, aby používaly ekvivalenty Punycode (názvy IDN). V tomto případě by se měly servery DNS, které se používají pro intranet, podporovat rozlišení názvů Unicode.

- povoleno IDN = None

     Tato hodnota nepřevede žádné názvy domén Unicode tak, aby používaly Punycode. Toto je výchozí hodnota, která je konzistentní s chováním .NET Framework 2,0.

 Povolením IDN převedete všechny jmenovky Unicode v názvu domény na jejich ekvivalenty Punycode. Názvy Punycode obsahují pouze znaky ASCII a vždy začínají předponou Xn---prefix. Důvodem je podpora stávajících serverů DNS na internetu, protože většina serverů DNS podporuje jenom znaky ASCII (viz RFC 3940).

### <a name="configuration-files"></a>Konfigurační soubory

Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).

## <a name="example"></a>Příklad

Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu analýzy IRI a názvů IDN:

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
- [Schéma nastavení sítě](index.md)
