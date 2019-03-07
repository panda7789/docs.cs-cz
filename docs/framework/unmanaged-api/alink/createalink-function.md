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
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498002"
---
# <a name="createalink-function"></a>CreateALink – funkce
Vytvoří instanci propojovacího programu sestavení a nastaví ukazatel na rozhraní zadané.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`riid`|Fyzický název jedné z propojovacího programu sestavení rozhraní.|  
|`ppInterface`|Umístění, které při úspěšném dokončení obsahuje ukazatel `riid` rozhraní.|  
  
## <a name="requirements"></a>Požadavky  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také:
- [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
