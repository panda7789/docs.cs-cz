---
title: "Zařazování delegáta jako metody zpětného volání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 894445657c938d381a8585c5e9c7440c694aa5b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Zařazování delegáta jako metody zpětného volání
Tento příklad znázorňuje, jak předat delegáti nespravované funkce byl očekáván ukazatelů na funkce. Delegát je třída, která může pojmout odkazu na třídu metodě a je ekvivalentní ukazatel na funkci zajišťující bezpečnost typů nebo funkce zpětného volání.  
  
> [!NOTE]
>  Při použití delegáta uvnitř volání modul common language runtime chrání delegát nebudou uvolnění z paměti po dobu trvání tohoto volání. Ale pokud nespravované funkce ukládá delegát používat po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud nebude dokončeno nespravované funkce s delegátem. Další informace najdete v tématu [HandleRef ukázka](http://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959) a [GCHandle ukázka](http://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f).  
  
 Zpětné volání – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:  
  
-   **TestCallBack** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) vlastní nespravované knihovnu, která obsahuje implementaci výše uvedených funkcí.  
  
 V této ukázce `LibWrap` třída obsahuje spravovaných prototypy pro `TestCallBack` a `TestCallBack2` metody. Obě metody předání delegáta zpětného volání funkce jako parametr. Podpis delegáta, musí odpovídat podpis metody, na které odkazuje. Například `FPtr` a `FPtr2` delegáti mít podpisy, které jsou stejné jako `DoSomething` a `DoSomething2` metody.  
  
## <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>Viz také  
 [Různé zařazování ukázky](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [Datové typy vyvolání platformy](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
