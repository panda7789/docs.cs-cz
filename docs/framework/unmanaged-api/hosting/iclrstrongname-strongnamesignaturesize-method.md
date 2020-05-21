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
ms.openlocfilehash: edce771b3c36f2c56637aa2a21fe524be0ae12c8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763017"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize – metoda
Vrátí velikost podpisu silného názvu. Tato metoda je obvykle používána kompilátory k určení, kolik místa lze v souboru vyhradit při vytváření sestavení se zpožděným podpisem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 pro Struktura typu [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 pro Velikost v bajtech `pbPublicKeyBlob` .  
  
 `pcbSize`  
 pro Počet bajtů vyžadovaných k uložení podpisu silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
