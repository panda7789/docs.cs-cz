---
title: IMetaDataTables::GetRow – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 13d514157382c75a2eb9799837f9355d0e469c99
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489896"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow – metoda
Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixTbl`  
 pro Index tabulky, ze které se má řádek načíst  
  
 `rid`  
 pro Index řádku, který se má načíst  
  
 `ppRow`  
 mimo Ukazatel na ukazatel na řádek.  
  
## <a name="remarks"></a>Poznámky  

  Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky. Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika. Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
