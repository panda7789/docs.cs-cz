---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 76e28b18cd595a4a18f573dfe9539b646196c944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720337"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídu ServiceMetadataBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídu ServiceMetadataBehavior má následující vlastnosti:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastaví umístění, do kterého služba přesměruje požadavky metadat.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
