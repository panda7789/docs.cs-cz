---
title: IMetaDataImport::FindMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3736d604b7e77028a2b99d462d88ae207df926c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448020"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef – metoda
Získá ukazatel na token MemberRef pro člena odkazovat na který je uzavřené do zadané <xref:System.Type> a má zadaný název a metadata podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [v] Odkaz TypeRef token pro třídu nebo rozhraní, která obklopuje odkaz na člena pro vyhledávání. Pokud je tato hodnota `mdTokenNil`, se provádí vyhledávání pro globální proměnné nebo odkaz na globální funkce.  
  
 `szName`  
 [v] Název odkaz na člena pro vyhledávání.  
  
 `pvSigBlob`  
 [v] Ukazatel na binární metadata podpis odkaz na člena.  
  
 `cbSigBlob`  
 [v] Velikost v bajtech `pvSigBlob`.  
  
 `pmr`  
 [out] Ukazatel na odpovídající MemberRef token.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte člena pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).  
  
 Podpis předaný `FindMemberRef` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah. Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota. Token je index do místní definice typu tabulky. Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a použít jako vstup pro tento podpis `FindMemberRef`.  
  
 `FindMemberRef` Vyhledá pouze člen odkazy, které byly definovány přímo v třídy nebo rozhraní; odkazy na zděděné členy nenajde.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
