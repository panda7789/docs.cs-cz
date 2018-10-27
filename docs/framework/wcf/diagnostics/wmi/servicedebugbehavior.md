---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452859"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třídě ServiceDebugBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídě ServiceDebugBehavior má následující vlastnosti:  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
