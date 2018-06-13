---
title: '&lt;xmlSerializer&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: f80d41701f3e0d62e89a056701bde6fd69ef9ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583250"
---
# <a name="ltxmlserializergt-element"></a>&lt;xmlSerializer&gt; – Element
Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.  
  
 \<Konfigurace >  
\<System.XML.Serialization >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**checkDeserializeAdvances**|Určuje, zda průběh <xref:System.Xml.Serialization.XmlSerializer> je zaškrtnuto. Nastavte atribut na "true" nebo "false". Výchozí hodnota je "true".|  
|**useLegacySerializationGeneration**|Určuje, zda <xref:System.Xml.Serialization.XmlSerializer> používá starší verze serializace generace, který generuje sestavení tak, že zápis do souboru kódu jazyka C# a jeho kompilace na sestavení. Výchozí hodnota je **false**.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)|Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data. Učiní tak pokusem o detekovat nekonečné smyčce během deserializace. Pokud je zjištěn takovém stavu, je vyvolána výjimka s následující zprávou: "vnitřní chyba: deserializace posunutí přes základního datového proudu se nezdařilo."  
  
 Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá. V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka. Pokud zjistíte, že v konkrétní aplikaci legitimní zprávy se odmítne tento další úroveň ochrany, nastavte **checkDeserializeAdvances** atributu na hodnotu "false".  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví **checkDeserializeAdvances** atributu na hodnotu "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
