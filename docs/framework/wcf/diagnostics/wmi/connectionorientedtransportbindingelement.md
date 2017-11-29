---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d28bedb67850b9bb77c25c8d29c6e39b056770a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ConnectionOrientedTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ConnectionOrientedTransportBindingElement má následující vlastnosti:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje, jak dlouho inicializaci kanálu musí dokončit před vypršením časového limitu.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která označuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost vyrovnávací paměti pro použití.  
  
### <a name="maxoutputdelay"></a>maxOutputDelay  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Maximální interval dobu, po kterou může zůstat bloku zprávu nebo zprávu úplné do vyrovnávací paměti v paměti, teprve pak ji bude odeslána.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet čekající asynchronní přijmout vláken, které jsou k dispozici pro zpracování příchozí připojení ve službě.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet čeká na připojení.  
  
### <a name="transfermode"></a>transferMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
