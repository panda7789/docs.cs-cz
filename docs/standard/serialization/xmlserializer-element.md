---
title: '&lt;xmlSerializer&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2770b82f71f3c4b43df4c44f75248e5392c528c2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132143"
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
 Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data. Učiní tak pokusem o detekovat nekonečné smyčce během deserializace. Pokud je zjištěno takovou podmínku, je vyvolána výjimka s následující zprávou: "došlo k vnitřní chybě: deserializace se nezdařila lze postoupit nad základního datového proudu."  
  
 Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá. V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka. Pokud zjistíte, že v aplikaci konkrétní legitimní zprávy jsou odmítnuta, podle této další úroveň ochrany, nastavte **checkDeserializeAdvances** atribut "false".  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví **checkDeserializeAdvances** atribut "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Serialization.XmlSerializer>  
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
