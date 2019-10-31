---
title: CreateInstallReferenceEnum – funkce
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108570"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum – funkce
Získá ukazatel na instanci [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) , která představuje seznam odkazů aplikace na zadané sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefEnum`  
 mimo Vrácený ukazatel `IInstallReferenceEnum`.  
  
 `pName`  
 pro [IAssemblyName](iassemblyname-interface.md) , který identifikuje sestavení, pro které mají být vyčísleny odkazy.  
  
 `dwFlags`  
 pro Příznaky ovlivňující chování čítače.  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Fusion. dll a knihovny Mscorwks. dll. Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IInstallReferenceEnum – rozhraní](iinstallreferenceenum-interface.md)
- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
