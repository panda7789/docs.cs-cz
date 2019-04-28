---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641616"
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
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda chce uživatel převzít kontrolu nad adresováním zpráv.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 Datový typ: sint64  
  
 Typ přístupu: jen pro čtení  
  
 Maximální velikost vyrovnávací paměti fondu pro vazbu.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Datový typ: sint64  
  
 Typ přístupu: jen pro čtení  
  
 Maximální velikost zprávy zpracované touto vazbou.  
  
### <a name="scheme"></a>Schéma  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Schéma identifikátoru URI pro přenos.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.TransportBindingElement>
