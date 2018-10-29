---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198104"
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
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.  
  
### <a name="queuetransferprotocol"></a>Třída queueTransferProtocol  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota výčtu, která označuje přenos zařazených do fronty komunikačního kanálu, který tato vazba používá.  
  
### <a name="useactivedirectory"></a>Třída UseActiveDirectory  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Vrátí logickou hodnotu, která určuje, zda mají být adresy fronty převedeny pomocí služby Active Directory.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
