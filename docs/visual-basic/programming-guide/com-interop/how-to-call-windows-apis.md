---
title: 'Postupy: Volání rozhraní API Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: e7b76495b83cb9a1dfe7629a1d82695d2046eac2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972765"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Postupy: Volání rozhraní API Windows (Visual Basic)
Tento příklad definuje a volá `MessageBox` funkce v user32.dll a poté předá řetězec k němu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Metoda není statická, je abstraktní nebo dříve definované. Nadřazený typ je rozhraní nebo délka *název* nebo *názevsouboru* je nula. (<xref:System.ArgumentException>)  
  
-   *Název* nebo *názevsouboru* je `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Nadřazený typ byl dříve vytvořen pomocí `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Viz také:

- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Příklady vyvolání platformy](../../../framework/interop/platform-invoke-examples.md)
- [Používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Definování metody pomocí reflexe generování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
