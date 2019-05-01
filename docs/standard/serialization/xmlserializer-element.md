---
title: Element <xmlSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2919e8d4c1af858973ff3d2b58b4d3bc4f925527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018058"
---
# <a name="xmlserializer-element"></a>\<xmlSerializer> Element
Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.  
  
 \<Konfigurace >  
\<system.xml.serialization>  
  
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
 Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data. Učiní tak pokusem o detekovat nekonečné smyčce během deserializace. Pokud je zjištěno takovou podmínku, je vyvolána výjimka s následující zprávou: "Došlo k vnitřní chybě: deserializace se nezdařila lze postoupit nad základního datového proudu."  
  
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
