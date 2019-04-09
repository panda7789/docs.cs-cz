---
title: ISymUnmanagedReader2 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 890053e1bf2e0648a41cca718e94edcf21c7e612
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165981"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 – rozhraní
Představuje modul pro načítání symbolů, který poskytuje přístup k dokumentům, metody a proměnných v úložišti symbolů. Toto rozhraní rozšiřuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Získáte metodu čtečky symbolů daný token metody a číslo verze edit-and-continue.|  
|[GetMethodsInDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Získá každou metodu, která obsahuje informace o řádek v zadané dokumentu.|  
|[GetSymAttributePreRemap – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Získá vlastní atribut na základě jeho názvu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
