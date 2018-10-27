---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188830"
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
  
### <a name="externalmetadatalocation"></a>externalMetadataLocation  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, do kterého služba přesměruje požadavky metadat.  
  
### <a name="httpgetenabled"></a>httpGetEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.  
  
### <a name="httpgeturl"></a>Vlastnost httpGetUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.  
  
### <a name="httpsgetenabled"></a>httpsGetEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.  
  
### <a name="httpsgeturl"></a>Vlastnost httpsGetUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
