---
title: Příklady vyvolání platformy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: da157a40819ada3914cf1791c8ca3f7b30e8c837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124761"
---
# <a name="platform-invoke-examples"></a>Příklady vyvolání platformy
Následující příklady ukazují, jak definovat a volat funkci **MessageBox** v souboru User32. dll, která předává jednoduchý řetězec jako argument. V příkladech je pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> nastaveno na hodnotu **automaticky** , což cílové platformě umožní určit šířku znaku a zařazování řetězců.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Další příklady naleznete v tématu [zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
- [Určení znakové sady](specifying-a-character-set.md)
