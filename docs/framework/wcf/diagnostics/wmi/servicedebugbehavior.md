---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498879"
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
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
