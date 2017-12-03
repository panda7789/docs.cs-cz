---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e1314347dfb83fb0631ebaa98b4d35bb0ac402f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbinarymessageencodinggt"></a>&lt;binaryMessageEncoding&gt;
Definuje kodéru zprávy v binární, která kóduje zprávy Windows Communication Foundation (WCF) v binárním v drátové síti.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|maxReadPoolSize|Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky. Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady. Výchozí hodnota je 64.|  
|maxSessionSize|Kladné celé číslo, které nastavuje velikost v bajtech vyrovnávací paměti používané pro kódování. Větší vyrovnávací paměť zvyšuje rychlost kódování za cenu velikost pracovní sady. Výchozí hodnota je 2048.|  
|maxWritePoolSize|Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače. Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady. Výchozí hodnota je 16.|  
|verze messageVersion|Určuje zprávu protokolu SOAP a WS-Addressing verze, které se nepoužívají nebo se očekává.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Proces transformace zprávu do pořadí bajtů kódování je. Dekódování je zpětné proces. Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).  
  
 `binaryMessageEncoding` Element Určuje binární formát, .NET pro formát XML a má možností, které určují kódování znaků a verzi protokolu SOAP a adresování WS má být použit. Kodér zprávy v binární kódování zpráv Windows Communication Foundation (WCF) v binárním v drátové síti. Když toto kódování výsledkem velmi rychlé přenos zpráv, interoperabilita založené na protokolu WS-* dojde ke ztrátě standardů.  
  
## <a name="example"></a>Příklad  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
