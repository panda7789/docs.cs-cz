---
title: "&lt;IDN&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 44e2db95ec354fff4356a3619fa8230faf67544d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltidngt-element-uri-settings"></a>&lt;IDN&gt; – Element (nastavení Uri)
Určuje, zda analýza mezinárodní název domény (IDN) je použita na název domény.  
  
## <a name="schema-hierarchy"></a>Schéma hierarchie  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identifikátor URI > elementu (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<IDN >](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
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
|`enabled`|Určuje, že pokud analýza mezinárodní název domény (IDN) se použije pro název domény výchozí hodnota je none.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[identifikátor URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).|  
  
## <a name="remarks"></a>Poznámky  
 Existující <xref:System.Uri> třída rozšířilo v rozhraní .NET Framework 3.5. 3.0 SP1 a s podporou pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN) 2.0 SP1. Aktuální uživatelé neuvidí žádné chování se liší od rozhraní .NET Framework 2.0, pokud konkrétně povolit IRI a IDN podporovat. Tím se zajistí kompatibilitu aplikace s předchozí verze rozhraní .NET Framework.  
  
 Povolení podpory pro IRI, je potřeba udělat následující dvě změny:  
  
1.  Přidejte následující řádek do souboru machine.config v adresáři rozhraní .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Zadejte, zda má, analýza mezinárodní název domény (IDN) použít na název domény a zda má být použita IRI Analýza pravidla. To lze provést v souboru machine.config nebo v souboru app.config.  
  
 Existují tři možné hodnoty pro IDN v závislosti na servery DNS, které se používají:  
  
-   IDN, povoleno = All  
  
     Tato hodnota převede názvy domén, Unicode jejich ekvivalenty Punycode (IDN. názvy).  
  
-   IDN, povoleno = AllExceptIntranet  
  
     Tato hodnota se převést všechny názvy domén Unicode není v místním intranetu používat kódování Punycode ekvivalenty (IDN. názvy). V takovém případě pro zpracování mezinárodních názvů na místní Intranet, servery DNS, které se používají pro intranetové by měly podporovat překlad kódování Unicode.  
  
-   IDN, povoleno = None  
  
     Tato hodnota nebude převést názvy domén Unicode používat kódování Punycode. Toto je výchozí hodnota, která je konzistentní s chování rozhraní .NET Framework 2.0.  
  
 Povolení IDN převede všechny popisky kódování Unicode v názvu domény jejich ekvivalenty u Punycode. Názvy Punycode obsahovat pouze znaky ASCII a vždy začínají předponou xn –. Důvodem je podpora existující servery DNS na Internetu, protože většina servery DNS podporují pouze znaky ASCII (viz RFC 3940).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy.  
  
### <a name="code"></a>Kód  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
