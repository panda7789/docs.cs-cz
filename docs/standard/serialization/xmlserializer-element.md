---
title: Element <xmlSerializer>
description: <xmlSerializer>Prvek určuje, zda je provedena dodatečná kontrolní průběh objektu XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288924"
---
# <a name="xmlserializer-element"></a>Element \<xmlSerializer>
Určuje, zda dodatečnou kontrolu průběh <xref:System.Xml.Serialization.XmlSerializer> je Hotovo.  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<system.xml.serialization>Objekt](system-xml-serialization-element.md)|Obsahuje nastavení konfigurace pro <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.Xml.Serialization.XmlSerializer> poskytuje další vrstvu zabezpečení proti potenciální odmítnutí útoků služby při deserializaci nedůvěryhodná data. Učiní tak pokusem o detekovat nekonečné smyčce během deserializace. Je-li taková podmínka zjištěna, je vyvolána výjimka s následující zprávou: "vnitřní chyba: deserializace nemohla pokračovat v podkladovém datovém proudu".  
  
 Přijetí tato zpráva nemusí znamenat, že útoku služby probíhá. V některých výjimečných případech mechanismus detekce nekonečné smyčce vytváří chybné detekce a legitimní příchozí zprávy, je vyvolána výjimka. Pokud zjistíte, že v rámci konkrétní aplikace jsou legitimní zprávy odmítnuty touto dodatečnou vrstvou ochrany, nastavte atribut **checkDeserializeAdvances** na hodnotu false.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví atribut **checkDeserializeAdvances** na hodnotu false (NEPRAVDA).  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Serialization.XmlSerializer>
- [\<system.xml.serialization>Objekt](system-xml-serialization-element.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
