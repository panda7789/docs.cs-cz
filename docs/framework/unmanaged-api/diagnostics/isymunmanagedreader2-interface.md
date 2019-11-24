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
ms.openlocfilehash: a07c75e14244fb5bdf72ff2b0d344ae27672ef89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448264"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 – rozhraní
Represents a symbol reader that provides access to documents, methods, and variables within a symbol store. This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Get a symbol reader method, given a method token and an edit-and-continue version number.|  
|[GetMethodsInDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Gets every method that has line information in the provided document.|  
|[GetSymAttributePreRemap – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Gets a custom attribute based upon its name.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
