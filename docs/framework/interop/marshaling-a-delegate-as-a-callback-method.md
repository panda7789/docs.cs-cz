---
title: Zařazování delegáta jako metody zpětného volání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff875f2807a14493ab81a9e354b5c4dcdf3d5feb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Zařazování delegáta jako metody zpětného volání
Tento příklad znázorňuje, jak předat delegáti nespravované funkce byl očekáván ukazatelů na funkce. Delegát je třída, která může pojmout odkazu na třídu metodě a je ekvivalentní ukazatel na funkci zajišťující bezpečnost typů nebo funkce zpětného volání.  
  
> [!NOTE]
>  Při použití delegáta uvnitř volání modul common language runtime chrání delegát nebudou uvolnění z paměti po dobu trvání tohoto volání. Ale pokud nespravované funkce ukládá delegát používat po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud nebude dokončeno nespravované funkce s delegátem. Další informace najdete v tématu [HandleRef ukázka](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) a [GCHandle ukázka](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).  
  
 Zpětné volání – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:  
  
-   **TestCallBack** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementaci výše uvedených funkcí.  
  
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
 [Různé zařazování ukázky](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))  
 [Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
