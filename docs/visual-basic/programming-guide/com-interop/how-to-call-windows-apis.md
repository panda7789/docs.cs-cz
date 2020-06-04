---
title: 'Postupy: Volání rozhraní API systému Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 2c3bb599b79575180eb2b0ec89453f01901f94c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396840"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Postupy: Volání rozhraní API systému Windows (Visual Basic)
Tento příklad definuje a zavolá `MessageBox` funkci v souboru User32. dll a poté předá do ní řetězec.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Tento příklad vyžaduje:  
  
- Odkaz na <xref:System> obor názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Metoda není statická, je abstraktní nebo dříve definovaná. Nadřazený typ je rozhraní nebo délka *názvu* nebo *Název_souboru_DLL* je nula. (<xref:System.ArgumentException>)  
  
- *Název* nebo název *Název_souboru_DLL* je `Nothing` . (<xref:System.ArgumentNullException>)  
  
- Nadřazený typ byl dříve vytvořen pomocí `CreateType` . (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Viz také

- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Příklady vyvolání platformy](../../../framework/interop/platform-invoke-examples.md)
- [Používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Definování metody pomocí generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Návod: Volání rozhraní API systému Windows](walkthrough-calling-windows-apis.md)
- [Zprostředkovatel komunikace s objekty COM](index.md)
