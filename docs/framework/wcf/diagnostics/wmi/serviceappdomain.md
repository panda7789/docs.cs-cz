---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
