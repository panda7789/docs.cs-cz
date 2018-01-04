---
title: "EnumerateCLRs – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs – funkce
Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [v] Proces identifikátor procesu, ve kterém bude možné provést výčet načíst CLRs.  
  
 `ppHandleArrayOut`  
 [out] Ukazatel na pole obsahující obslužné rutiny události, které se používají ke spuštění CLR pokračovat. Každý popisovač v poli, nemusí být platný. Pokud se platný, popisovač má být použita jako událost pokračovat spuštění pro odpovídající runtime umístěný ve stejné index `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Ukazatel na pole řetězců, které určují úplné cesty k CLRs načíst v procesu.  
  
 `pdwArrayLengthOut`  
 [out] Ukazatel na DWORD, který obsahuje délku stejně velké `ppHandleArrayOut` a `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.  
  
 E_INVALIDARG  
 Buď `ppHandleArrayOut` nebo `ppStringArrayOut` má hodnotu null, nebo `pdwArrayLengthOut` má hodnotu null.  
  
 E_OUTOFMEMORY  
 Funkce se nepodařilo přidělit dostatek paměti pro pole popisovač a cestu.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze vytvořit výčet načíst CLRs.  
  
## <a name="remarks"></a>Poznámky  
 Pro cílový proces, která je identifikovaná `debuggeePID`, funkce vrátí hodnotu pole cesty, `ppStringArrayOut`do CLRs načíst v procesu; pole obslužné rutiny události, `ppHandleArrayOut`, který může obsahovat pokračovat spouštění událostí pro CLR ve stejném indexu; a Velikost pole, `pdwArrayLengthOut`, která určuje počet CLRs, které jsou načteny.  
  
 V operačním systému Windows `debuggeePID` mapuje operační systém zpracovat identifikátor.  
  
 Paměť pro `ppHandleArrayOut` a `ppStringArrayOut` jsou přiděleny pomocí této funkce. Chcete-li uvolnit je paměť přidělená, musí volat [closeclrenumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Tuto funkci nelze volat s oba parametry pole nastavena na hodnotu null, aby bylo možné vrátí počet CLRs v tento cílový proces. Z tento počet můžete volající odvození velikost vyrovnávací paměti, která bude vytvořena: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
