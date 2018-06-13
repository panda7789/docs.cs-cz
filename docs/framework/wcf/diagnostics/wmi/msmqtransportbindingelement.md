---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485905"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída prvkem MsmqTransportBindingElement má následující vlastnosti:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.  
  
### <a name="queuetransferprotocol"></a>Třída QueueTransferProtocol  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota výčtu, která určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu.  
  
### <a name="useactivedirectory"></a>Třída UseActiveDirectory  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Vrátí logickou hodnotu, která určuje, zda mají být převedeny fronty adresy pomocí služby Active Directory.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
