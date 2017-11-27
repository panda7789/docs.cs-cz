---
title: "IMetaDataTables – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c89d615fbeeff4a60eb386d58c573ee7905f538d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables-interface"></a>IMetaDataTables – rozhraní
Poskytuje metody pro ukládání a načítání informací metadat v tabulkách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getblob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Získá ukazatel na binární rozsáhlý objekt (binární rozsáhlý OBJEKT) v indexu zadaný sloupec.|  
|[Getblobheapsize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Získá velikost v bajtech haldě objektů BLOB.|  
|[Getcodedtokeninfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Získá ukazatel na pole tokeny přidružený index zadaný řádku.|  
|[GetColumn – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Získá ukazatel na hodnoty obsažené v sloupce v indexu zadaný sloupec, v tabulce u zadané tabulky indexu.|  
|[GetColumnInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Získá data o zadaný sloupec zadané tabulky.|  
|[Getguid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Získá identifikátor GUID z řádek na pozici se zadaným indexem.|  
|[Getguidheapsize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Získá velikost v bajtech haldě identifikátor GUID.|  
|[Getnextblob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Získá index další objektů BLOB v tabulce.|  
|[Getnextguid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Získá index další hodnota identifikátoru GUID v aktuální sloupec tabulky.|  
|[Getnextstring – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Získá index další řetězce v aktuálním sloupec tabulky.|  
|[Getnextuserstring – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Získá index řádku, který obsahuje další pevně řetězce v aktuálním sloupec tabulky.|  
|[Getnumtables – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Získá počet tabulek v rozsahu aktuální `IMetaDataTables` instance.|  
|[GetRow – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Získá řádek indexem zadaný řádek v tabulce u zadané tabulky indexu.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.|  
|[Getstringheapsize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Získá velikost v bajtech haldy řetězce.|  
|[Gettableindex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Získá index pro tabulku odkazuje zadaný token.|  
|[Gettableinfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Získá název, velikost řádku, počet řádků, počet sloupců a index sloupce klíče tabulky v indexu zadané tabulky.|  
|[Getuserstring – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Získá řetězec pevně v zadaném indexu ve sloupci řetězce v aktuálním oboru.|  
|[Getuserstringheapsize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Získá velikost v bajtech haldě řetězec uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadatatables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
