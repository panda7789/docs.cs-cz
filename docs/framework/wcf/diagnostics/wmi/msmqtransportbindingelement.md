---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197929"
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
