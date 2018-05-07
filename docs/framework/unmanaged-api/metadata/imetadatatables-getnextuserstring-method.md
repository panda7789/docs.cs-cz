---
title: IMetaDataTables::GetNextUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b9e729732175b7249e4d3be91996bc5e4050855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetnextuserstring-method"></a>IMetaDataTables::GetNextUserString – metoda
Získá index řádku, který obsahuje další pevně řetězce v aktuálním sloupec tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ixUserString`  
 [v] Hodnota indexu z aktuální sloupec řetězec.  
  
 `pNext`  
 [out] Ukazatel na index řádku další řetězce ve sloupci.  
  
## <a name="remarks"></a>Poznámky  
 Nedoporučujeme použití této metody, protože nevrací konzistentních výsledků. Informace o tabulce GUID najdete v dokumentaci společné jazykové infrastruktury (CLI), zejména "oddílu II: Metadata definice a sémantiku". Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
