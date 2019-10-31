---
title: CorpubPublish – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132142"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish – třída typu coclass
Poskytuje rozhraní pro publikování informací o aplikačních doménách a procesech.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[ICorPublish – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Poskytuje metody pro publikování informací o procesech a doménách aplikace v těchto procesech.|  
|[ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Představuje a poskytuje informace o doméně aplikace v procesu.|  
|[ICorPublishAppDomainEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Poskytuje metody, které procházejí kolekci aplikačních domén, které aktuálně existují v rámci procesu.|  
|[ICorPublishProcess – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Představuje proces, který je spuštěn v počítači.|  
|[ICorPublishProcessEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Poskytuje metody, které procházejí kolekci procesů, které jsou spuštěny v počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Typický scénář publikování zahrnuje vývojáře, který chce ladit spravovaný kód, který je spuštěný v počítači v doméně aplikace. Hostující prostředí může v rámci procesu používat více než jednu doménu aplikace. Vývojář chce použít grafické uživatelské rozhraní nebo jiné prostředky k zobrazení seznamu všech procesů spuštěných v počítači a vybrat konkrétní proces. Výpis by měl obsahovat všechny domény aplikace v rámci procesů, na kterých běží spravovaný kód. Vývojář pak může identifikovat konkrétní doménu aplikace a připojit ladicí program k této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
