---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182655"
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
  
### <a name="manualaddressing"></a>Vlastnost manualAddressing  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota určující, zda chce uživatel převzít kontrolu nad adresováním zpráv.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Datový typ: sint64  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost vyrovnávací paměti fondu pro vazbu.  
  
### <a name="maxreceivedmessagesize"></a>maxReceivedMessageSize  
 Datový typ: sint64  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost zprávy zpracované touto vazbou.  
  
### <a name="scheme"></a>Schéma  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Schéma identifikátoru URI pro přenos.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
