---
title: CreateICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 294b82efd66704014aab1b73171afe9165f17664
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616447"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen – funkce
Vytvoří objekt [ICeeFileGen –](iceefilegen-class.md) .  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ceeFileGen`  
 mimo Ukazatel na adresu nového `ICeeFileGen` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM.  
  
## <a name="remarks"></a>Poznámky  
 `ICeeFileGen`Objekt se používá k vytvoření přenosných spustitelných souborů (PE) pro modul CLR (Common Language Runtime).  
  
 Po dokončení volejte funkci [DestroyICeeFileGen –](destroyiceefilegen-function.md) pro zničení `ICeeFileGen` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** ICeeFileGen –. h  
  
 **Knihovna:** MSCorPE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
