---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: dc7a29e5911a9d0a774e36f5be8c1f3cacad69b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486614"
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
