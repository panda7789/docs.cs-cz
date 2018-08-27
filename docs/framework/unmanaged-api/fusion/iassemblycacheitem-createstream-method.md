---
title: IAssemblyCacheItem::CreateStream – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934082"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream – metoda
Vytvoří datový proud se zadaným názvem a formát.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Příznaky definované v Fusion.idl.  
  
 `pszStreamName`  
 [in] Název datového proudu, který se má vytvořit.  
  
 `dwFormat`  
 [in] Formát souboru, který má být datovým proudem.  
  
 `dwFormatFlags`  
 [in] Příznaky formátu konkrétní definované v Fusion.idl.  
  
 `ppIStream`  
 [out] Ukazatel na adresu vráceného [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.  
  
 `puliMaxSize`  
 [in, volitelné] Maximální velikost datového proudu odkazuje `ppIStream`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IAssemblyCacheItem – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
