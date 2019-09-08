---
title: StrongNameSignatureSize – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798952"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize – funkce
Vrátí velikost podpisu silného názvu. `StrongNameSignatureSize`je obvykle používán kompilátory k určení, kolik místa lze v souboru vyhradit při vytváření sestavení se zpožděným podpisem.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureSize –](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 pro Struktura typu [PublicKeyBlob –](publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 pro Velikost v bajtech `pbPublicKeyBlob`.  
  
 `pcbSize`  
 pro Počet bajtů vyžadovaných k uložení podpisu silného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 Pokud se `StrongNameSignatureSize` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureSize – metoda](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
