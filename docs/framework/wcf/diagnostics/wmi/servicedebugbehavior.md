---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceDebugBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceDebugBehavior má následující vlastnosti:  
  
### <a name="httphelppageenabled"></a>httpHelpPageEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.  
  
### <a name="httphelppageurl"></a>httpHelpPageUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.  
  
### <a name="httpshelppageenabled"></a>httpsHelpPageEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.  
  
### <a name="httpshelppageurl"></a>httpsHelpPageUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácených klientům pro účely ladění.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
