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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789221"
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
|[ICorPublish – rozhraní](icorpublish-interface.md)|Poskytuje metody pro publikování informací o procesech a doménách aplikace v těchto procesech.|  
|[ICorPublishAppDomain – rozhraní](icorpublishappdomain-interface.md)|Představuje a poskytuje informace o doméně aplikace v procesu.|  
|[ICorPublishAppDomainEnum – rozhraní](icorpublishappdomainenum-interface.md)|Poskytuje metody, které procházejí kolekci aplikačních domén, které aktuálně existují v rámci procesu.|  
|[ICorPublishProcess – rozhraní](icorpublishprocess-interface.md)|Představuje proces, který je spuštěn v počítači.|  
|[ICorPublishProcessEnum – rozhraní](icorpublishprocessenum-interface.md)|Poskytuje metody, které procházejí kolekci procesů, které jsou spuštěny v počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Typický scénář publikování zahrnuje vývojáře, který chce ladit spravovaný kód, který je spuštěný v počítači v doméně aplikace. Hostující prostředí může v rámci procesu používat více než jednu doménu aplikace. Vývojář chce použít grafické uživatelské rozhraní nebo jiné prostředky k zobrazení seznamu všech procesů spuštěných v počítači a vybrat konkrétní proces. Výpis by měl obsahovat všechny domény aplikace v rámci procesů, na kterých běží spravovaný kód. Vývojář pak může identifikovat konkrétní doménu aplikace a připojit ladicí program k této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
