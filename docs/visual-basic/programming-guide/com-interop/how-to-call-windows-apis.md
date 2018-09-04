---
title: 'Postupy: Volání rozhraní API systému Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 739516e86917ac24a81cd6387af5576c512ecbc2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515914"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Postupy: Volání rozhraní API systému Windows (Visual Basic)
Tento příklad definuje a volá `MessageBox` funkce v user32.dll a poté předá řetězec k němu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Metoda není statická, je abstraktní nebo dříve definované. Nadřazený typ je rozhraní nebo délka *název* nebo *názevsouboru* je nula. (<xref:System.ArgumentException>)  
  
-   *Název* nebo *názevsouboru* je `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Nadřazený typ byl dříve vytvořen pomocí `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Viz také  
 [Bližší pohled na vyvolání platformy](https://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Příklady vyvolání platformy](../../../framework/interop/platform-invoke-examples.md)  
 [Používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Definování metody pomocí reflexe generování](https://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
