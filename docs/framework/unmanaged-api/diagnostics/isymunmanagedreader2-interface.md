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
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615394"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 – rozhraní
Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů. Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap – metoda](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Získejte metodu čtečky symbolů s ohledem na token metody a číslo verze Edit-and-Continue.|  
|[GetMethodsInDocument – metoda](isymunmanagedreader2-getmethodsindocument-method.md)|Načte každou metodu, která obsahuje informace o řádku v zadaném dokumentu.|  
|[GetSymAttributePreRemap – metoda](isymunmanagedreader2-getsymattributepreremap-method.md)|Získá vlastní atribut založený na jeho názvu.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader – rozhraní](isymunmanagedreader-interface.md)
