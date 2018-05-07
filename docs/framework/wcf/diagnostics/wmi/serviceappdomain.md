---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Mapuje služby domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceAppDomain nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceAppDomain má následující vlastnosti:  
  
### <a name="ref"></a>ref  
 Datový typ: služby  
Kvalifikátory: klíč  
  
 Přístup k typu: jen pro čtení  
  
 Služba této domény aplikace.  
  
### <a name="ref"></a>ref  
 Datový typ: AppDomainInfo  
Kvalifikátory: klíč  
  
 Přístup k typu: jen pro čtení  
  
 Obsahuje vlastnosti domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
