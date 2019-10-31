---
title: IInstallReferenceEnum – rozhraní
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: d3f7c24b4bd373924c44dbc0490c890e7f1322bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131736"
---
# <a name="iinstallreferenceenum-interface"></a>IInstallReferenceEnum – rozhraní
Představuje enumerátor pro odkazovaná sestavení nainstalovaná v globální mezipaměti sestavení (GAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNextInstallReferenceItem – metoda](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|Získá ukazatel na další `IInstallReferenceItem` obsažený v tomto `IInstallReferenceEnum`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IInstallReferenceItem – rozhraní](iinstallreferenceitem-interface.md)
