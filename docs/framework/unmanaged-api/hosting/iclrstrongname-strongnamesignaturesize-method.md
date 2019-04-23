---
title: ICLRStrongName::StrongNameSignatureSize – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c81b51deb6affb3dd39677184ea0a4b2e6ff61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219977"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize – metoda
Vrátí velikost položky podpis silného názvu. Tato metoda se obvykle používá kompilátory, chcete-li určit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděným podpisem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.  
  
 `cbPublicKeyBlob`  
 [in] Velikost v bajtech, z `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [in] Počet bajtů vyžadovaných k uložení podpis silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
