---
title: CreateALink – funkce
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
