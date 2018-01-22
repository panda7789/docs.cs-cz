---
title: "Postupy: Volání rozhraní API systému Windows (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 772db789fba4552a4645d2c6a242ba01944652ee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Postupy: Volání rozhraní API systému Windows (Visual Basic)
Tento příklad definuje a volá `MessageBox` funkce v user32.dll a pak předá řetězec k němu.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Metoda nejsou statické, je abstraktní nebo byla definována dříve. Nadřazený typ je rozhraní nebo délka *název* nebo *názevsouboru* je nulová. (<xref:System.ArgumentException>)  
  
-   *Název* nebo *názevsouboru* je `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Typ obsahující byla dříve vytvořena pomocí `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Viz také  
 [Vyvolání bližší pohled na platformy](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Příklady vyvolání platformy](../../../framework/interop/platform-invoke-examples.md)  
 [Používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Emitování definování metoda pomocí reflexe](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
