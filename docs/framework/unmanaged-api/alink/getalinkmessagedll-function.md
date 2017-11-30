---
title: "GetALinkMessageDll – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e87fe5b49a7d939a350d5d0bcb31f79eaaf333c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll – funkce
Vyhledá a načte zprávy knihovny DLL. Vrátí hodnotu 0, pokud nelze umístěný nebo načíst knihovny DLL zpráv. Zpráva knihovny DLL musí být buď v podadresáři, jejíž název je ID jazyka, nebo v aktuálním adresáři.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** alink.h  
  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také  
 [Al.exe (Linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
