---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957070"
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Služba se mapuje na doménu aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Datový typ: Služba  
Kvalifikátory: Key  
  
 Typ přístupu: jen pro čtení  
  
 Služba této domény aplikace.  
  
### <a name="ref"></a>ref  
 Datový typ: AppDomainInfo  
Kvalifikátory: Key  
  
 Typ přístupu: jen pro čtení  
  
 Obsahuje vlastnosti domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
