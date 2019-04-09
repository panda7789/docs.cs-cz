---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160326"
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
