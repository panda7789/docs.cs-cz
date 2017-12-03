---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2605e1a1f88434a9052059ac3ebdce429d6d6c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída TransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída TransportBindingElement má následující vlastnosti:  
  
### <a name="manualaddressing"></a>manualAddressing  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, jestli uživatel chce převzít kontrolu nad adresování zprávy.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Datový typ: sint64  
  
 Přístup k typu: jen pro čtení  
  
 Velikost fondu maximální vyrovnávací paměti pro vazbu.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Datový typ: sint64  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost zprávy, která je zpracovávané touto vazbou.  
  
### <a name="scheme"></a>Schéma  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Schéma identifikátoru URI pro přenos.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
