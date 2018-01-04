---
title: "CreateALink – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a>CreateALink – funkce
Vytvoří instanci Linker sestavení a nastaví ukazatele k zadanému rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`riid`|Fyzický název jednomu z rozhraní Linker sestavení.|  
|`ppInterface`|Umístění, které při úspěšném dokončení obsahuje odkazy `riid` rozhraní.|  
  
## <a name="requirements"></a>Požadavky  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také  
 [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
