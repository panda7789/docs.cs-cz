---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f17b31e1dfe9ba60b2042a85a6d673d986fe0a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Třída ServiceMetadataBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceMetadataBehavior má následující vlastnosti:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, do kterého službu přesměruje požadavků na metadata.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
