---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: d37ee4527226d9347e24fc2ee8007a263c71f198
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564874"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
  
 Typ přístupu: jen pro čtení  
  
 Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota výčtu, která označuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Vrátí logickou hodnotu, která určuje, zda mají být adresy fronty převedeny pomocí služby Active Directory.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
