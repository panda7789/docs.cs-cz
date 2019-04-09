---
title: GetALinkMessageDll – funkce
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163017"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll – funkce
Vyhledá a načte knihovna DLL zprávy. Vrátí hodnotu 0, pokud knihovna DLL zprávy nelze umístěný nebo načíst. Knihovna DLL zprávy musí být buď v podadresáři, jehož název je ID jazyka, nebo v aktuálním adresáři.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** alink.h  
  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také:

- [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
